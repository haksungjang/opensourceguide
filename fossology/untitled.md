---
description: How to install FOSSology
---

# 설치 방법

FOSSology는 오픈소스로 공개되어 있기 때문에, 누구나 자체적으로 설치하여 운영할 수 있습니다. 아래의 설명이, 오픈소스 라이선스 스캔 도구가 필요하신 분들에게 도움이 되길 바라겠습니다. 

## How to install FOSSology

기업 내에서 FOSSology를 사용하기 위해서는 사내에 FOSSology 서버를 구축해야 합니다. 이를 위해 리눅스 기반의 서버 시스템에 FOSSology를 설치해야 합니다. FOSSology는 다음 세 가지 방법으로 설치할 수 있습니다.

1. Docker 사용  
2. Vagrant와 VirtualBox 사용  
3. Source build 하여 설치  

먼저, 가장 간편한 방법인 Docker를 사용하는 방법에 대해 설명합니다. 

## Docker로 설치하기

FOSSology는 컨테이너화 된 Docker 이미지를 Docker Hub \(https://hub.docker.com/\)를 통해 공개하고 있습니다. : [https://hub.docker.com/r/fossology/fossology](https://hub.docker.com/r/fossology/fossology)

Pre-built 된 Docker 이미지는 다음 명령어를 사용하여 실행할 수 있습니다.

```text
$ docker run -p 8081:80 fossology/fossology
```

Docker 이미지는 다음 URL과 계정 정보로 사용할 수 있습니다. : http://\[IP\_OF\_DOCKER\_HOST\]:8081/repo

* Username : fossy
* Passwd : fossy

설치와 관련한 자세한 내용은 다음 페이지를 참고할 수 있습니다. : [https://github.com/fossology/fossology/blob/master/README.md](https://github.com/fossology/fossology/blob/master/README.md)

## Source Build 설치 on CentOS 7.6

여기서는 FOSSology를 CentOS 7.6에 설치하는 방법에 대해 설명하려고 합니다. 

사실, FOSSology에서 제공하는 Docker image\([https://hub.docker.com/r/fossology/fossology/](https://hub.docker.com/r/fossology/fossology/)\)를 이용하는 것이 가장 간단합니다. 그런데, 자체적으로 서버를 운영하면서, Postgesql, PHP, Apache 등을 개별적으로 설치하면서 설정하는 게 필요할 수 있습니다.  

FOSSology 소스 코드를 빌드하고, 이를 CentOS 7.6에 Deploy한 내용을 정리해보았습니다. \(사용하시는 환경에 따라 정확히 동일하게 동작하지는 않을 수 있습니다.\)

### SELinux 해제

```text
$ sudo vi /etc/sysconfig/selinux
...
SELINUX=disabled
$ sudo reboot
```

### PHP 5.6 upgrade

{% hint style="info" %}
참고 : [https://www.zerostopbits.com/how-to-upgrade-php-5-4-to-php-5-6-on-centos-7-5-1804/](https://www.zerostopbits.com/how-to-upgrade-php-5-4-to-php-5-6-on-centos-7-5-1804/)
{% endhint %}

```text
// php version 확인
$ php -v

// install the Remi and EPEL repositories
$ sudo rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
$ sudo rpm -Uvh https://rpms.remirepo.net/enterprise/remi-release-7.rpm

// Enable the Remi repository globally
$ sudo vi /etc/yum.repos.d/remi.repo

[remi]
...
enabled=1
[remi-php56]
...
enabled=1

// UPGRADE PHP 5.4 TO PHP 5.6
$ sudo yum -y upgrade php*


// 다시 version 확인
$ php -v
```

### Get source code

```text
$ wget https://github.com/fossology/fossology/archive/3.6.0.tar.gz
```

### Install dependencies

```text
// lsb package for centos7 설치
$ sudo yum install redhat-lsb

// composer 설치
$ sudo yum install composer

// dependencies 설치
$ tar xvfz 3.6.0.tar.gz
$ cd fossology-3.6.0
[fossology-3.6.0]$ sudo utils/fo-installdeps
```

### Build source code

```text
// Development Tools 설치
$ sudo yum groupinstall 'Development Tools'

// make
[fossology-3.6.0]$ make
```

### Install FOSSology

```text
// Install & log 저장
[fossology-3.6.0]$ sudo make install 2>&1 | tee install.log
```

### Postgresql 설정

{% hint style="info" %}
참고 : [https://github.com/fossology/fossology/wiki/Configuration-and-Tuning](https://github.com/fossology/fossology/wiki/Configuration-and-Tuning)
{% endhint %}

```text
// initdb
$ sudo postgresql-setup initdb

// postgresql.conf 편집
$ sudo vi /var/lib/pgsql/data/postgresql.conf
...
listen_addresses = '*'

// pg_hba.conf 편집
$ sudo vi /var/lib/pgsql/data/pg_hba.conf
...

# "local" is for Unix domain socket connections only
local   all             all                                     trust
# IPv4 local connections:
host    all             all             127.0.0.1/32            trust
# IPv6 local connections:
host    all             all             ::1/128                 trust

// 부팅 시 시작되도록 postgreasql enable
$ sudo systemctl enable postgresql

// postgreasql 시작
$ sudo systemctl start postgresql
```

### Install 완료 후 추가 사항

```text
// /var/log/fossology 생성
$ sudo mkdir /var/log/fossology

// Postinstall script 실행
$ sudo /usr/local/lib/fossology/fo-postinstall
```

### PHP 설정

```text
[fossology-3.6.0]$ sudo ./install/scripts/php-conf-fix.sh --overwrite
```

### Apache 설정

{% hint style="info" %}
\(여기서는 FOSSology 가이드인 repo alias를 사용하지 않고, Apache home directory 변경하는 방식으로 설정한다.\)

Apache 설치 가이드 for CentOS 7 참고 

* [https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-centos-7)
* [https://pureu0.tistory.com/8](https://pureu0.tistory.com/8)
{% endhint %}

```text
// FOSSology가 설치되어 있는 경로 지정
$ sudo vi /etc/httpd/conf/httpd.conf
...
DocumentRoot "/usr/local/share/fossology/www/ui"
...

# Relax access to content within /var/www.
#
<Directory "/usr/local/share/fossology/www/ui">
...
# Further relax access to the default document root:
<Directory "/usr/local/share/fossology/www/ui">

// httpd restart
$ sudo systemctl restart httpd
```

### 설치 테스트

```text
// Postgresql 접속 확인
$ sudo psql -d fossology -U fossy

// fossology scheduler 동작 확인
$ sudo /usr/local/etc/fossology/mods-enabled/scheduler/agent/fo_scheduler -t
```

### FOSSology start

```text
// 부팅 시 시작되도록 fossology enable
$ sudo systemctl enable fossology

// fossology 시작
$ sudo systemctl start fossology
```

### Browser에서 접속 확인

> http://\[ip\_address\]

### 접속 실패 시 log 확인

```text
// fossology log 확인
$ tail -f /var/log/fossology/fossology.log

// httpd log 확인
$ sudo tail -f /var/log/httpd/error_log
```

