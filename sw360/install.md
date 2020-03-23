---
description: SW360의 설치 방법을 설명합니다.
---

# How to install

## 구성

SW360은 다음과 같이 구성됩니다. 

* Frontend : Liferay-\(Tomcat-\)based portal application
* Backend : Tomcat-based thrift service
* Database : CouchDB

## 요구 사항

Project 구조와 설치를 위해 요구되는 소프트웨어 등 자세한 내용은 README의 Required software 부분에서 확인할 수 있습니다. : [https://github.com/eclipse/sw360/blob/master/README.md](https://github.com/eclipse/sw360/blob/master/README.md)

## 설치 방법

SW360은 다음 세 가지의 설치 방법을 제공합니다. 사용자는 이 중 하나를 선택하여 설치할 수 있습니다. 

1. Vagrant \([https://www.vagrantup.com/](https://www.vagrantup.com/)\) 기반 설치 : Vagrant는 가상화 인스턴스를 관리하는 도구로서 sw360vagrant에서는 SW360을 한 번에 Deploy 하기 위한 환경을 제공합니다. : [https://github.com/sw360/sw360vagrant](https://github.com/sw360/sw360vagrant)
2. SW360의 구성요소를 개별적으로 설치할 수 있습니다. : [https://github.com/eclipse/sw360](https://github.com/eclipse/sw360)
3. Docker를 통해 Deploy 할 수 있습니다. : [https://github.com/sw360/sw360chores](https://github.com/sw360/sw360chores)

여기서는 CentOS 7.6 시스템에 Vagrant 기반으로 설치하여 Deploy 하는 방법을 소개합다. 

{% hint style="info" %}
자세한 사항은 README를 참고하세요. : [https://github.com/sw360/sw360vagrant/blob/master/README.md](https://github.com/sw360/sw360vagrant/blob/master/README.md)
{% endhint %}

### 1\) 사전 설치

vagrant box에 SW360을 설치하기 위해서는 openjdk, VirtualBox 및 Vagrant를 설치해야 합니다. 먼저 openjdk 1.8.0을 설치합니다.

```text
$ yum install java-1.8.0-openjdk
$ java -version
openjdk version "1.8.0_191"
OpenJDK Runtime Environment (build 1.8.0_191-b12)”
OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
```

VirtualBox를 설치합다.

```text
$ sudo wget https://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo -P /etc/yum.repos.d
$ sudo yum install VirtualBox-5.2
```

CentOS 7에서 VirtualBox 설치 시, “kernel module is not loaded’ 에러가 발생할 경우, kernel-devel을 설치하여 해결한 후 VirtualBox를 재설치합니다.

```text
$ sudo yum install https://centos7.iuscommunity.org/ius-release.rpm
$ sudo yum install dkms
$ sudo yum install kernel-devel
# reboot
$ sudo /sbin/vboxconfig
$ systemctl status vboxdrv
● vboxdrv.service - VirtualBox Linux kernel module
   Loaded: loaded (/usr/lib/virtualbox/vboxdrv.sh; enabled; vendor preset: disabled)
   Active: active (exited) since Wed 2020-02-19 09:06:02 KST; 20min ago
```

Vagrant와 vagrant-aws plugin을 설치합다.

```text
$ sudo yum install https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.rpm 
# vagrant-aws plugin 설치
$ vagrant plugin install vagrant-aws
```

그리고, sw360vagrant 코드를 Clone합니다.

```text
$ git clone https://github.com/sw360/sw360vagrant.git
```

### 2\) Dependency 다운로드

Vagrant box를 빌드하는 시간을 줄이기 위해 Dependency Package들을 미리 다운로드 받습니다.

```text
$ cd sw360vagrant
$ ./download-packages.sh
```

그러면 다음의 package들이 ./shared/package 폴더 안에 다운로드 니다.

* Liferay 7.2.1 CE GA2 with Tomcat \(9.0.17\)
* Postgresql-42.2.9 ODBC client for Java as \*.jar file
* SW 360에서 필요한 11개의 \*.jar 파일
* Thrift 0.11
* A box images from the Ubuntu 16.04 LTS \(xenial-server-cloudimg-amd64-vagrant.box\)

### **3\) Base box 생성**

이제 다음 명령어로 Base box를 생성합니다.

```text
$ cd generate-box
$ ./generate_box.sh
```

이 작업은 수십 분 소요될 수 있습니다. 

### 4\) Box 실행

다음 명령어로 Box를 실행합니다.

```text
# If you have built a vagrant box from this directory earlier, you will have to destroy it first via
$ vagrant destroy
$ cd ../sw360-single
$ vagrant up
```

Box를 실행하면 liferay, postgresql 및 couchdb가 구성됩니. 이상없이 실행이 될 경우, [https://localhost:8443/](https://localhost:8443/) 로 Liferay 화면에 접근할 수 있습니다.

![](https://lh6.googleusercontent.com/leof_ntxQlxjDeD91E7ZfwWY0ftUlD0D_L58AkeNJb_bEFFzKvuL28yzb4iIA6-bAuSfQydo-gVBlnn5EVGGBKcPh0-6Y7p2Qbar74qpB4uwa_nibrV535NJwEIpWXZPFeNUSRd-)

### 5\) SW360 Layout Deploy

마지막 단계는 Liferay에서 SW360의 Layout을 Deploy하는 것입니다. 이 작업은 아직 자동화가 되지 않아 관리자가 수동으로 수행해야 합다. [https://localhost:8443/](https://localhost:8443/)에 접근하여 다음 계정으로 로그인합니다. 

* id : [setup@sw360.org](mailto:setup@sw360.org)
* pw : sw360fossy

이후에는 다음 사이트의 안내에 따라 Layout deploy를 수행합다. : [https://github.com/eclipse/sw360/wiki/Deploy-Liferay7](https://github.com/eclipse/sw360/wiki/Deploy-Liferay7)

Deploy가 완료되면 다음과 같은 화면을 볼 수 있습니다. 

![](https://lh5.googleusercontent.com/INu1-WWi1-SA9P61IMNlgZhugTXbiwbSKUOu2eWq_d5sIIp8NfqxQntwId41ZDmTG6_5Ope8GdU1J2S0adaJDolM09dtfkwIbOE2gTDC4MZXMxhX9kN28E4Yj8a3deBUHBL7yCqj)

