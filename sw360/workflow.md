---
description: SW360의 기본 사용법을 설명합니다.
---

# Basic Workflow

## 1. License 등록

SW360을 처음 설치하면 먼저 자주 사용하는 오픈소스 라이선스 들을 등록해야 합니다. 라이선스 다음과 같은 정보를 포함합니다. 

* Full Name
* Short Name
* License Type
* GPL-2.0 Compatibility \(예: yes, no\)
* License Text

메뉴 &gt; Licenses &gt; Add License를 선택하면 다음과 같이 Create License 화면으로 진입합니다. 

![](https://lh6.googleusercontent.com/8bn6z_39PK5WrjP7mzhHrTwfM5PU19QT3TiQnAatOYywVwcGLJGFMmMgMkzh4CKAPM0SOOy7VDoboaj9OKpD1QEZv6KWOeWxZfqGA_2geYrYOBm2kOVzrNOmGPVK-8hzJvBZ-klT)

이와 같이 라이선스를 하나씩 수동으로 등록하는 일은 상당히 수고스러울 수 있는데, 다행히 SW360은 SPDX License List를 한 번에 Import 하는 기능을 제공합니다. 메뉴 &gt; Admin &lt; Import SPDX Information을 클릭합니다. 

![](https://lh5.googleusercontent.com/d8ZK-dD34z1yKZn-szPNrN7iT4zg1EQnKnAv4QcPslSR0-laETy37ArojuweqSsxpWuvGXtdF5FabiWk57So-bD_iiEx7eVIR6tWDsYO2SkaCdlKr6ELDN9y_NdkqWFbQgRF2lXN)

그러면, 곧 SPDX License List가 자동으로 등록됩니다. 메뉴 &gt; Licenses에서 338개의 License가 등록된 것을 확인할 수 있습니다. 

![](https://lh6.googleusercontent.com/Ucjuo09uJKhEhACZ90y98PszgSiCGtlDotH8mbTXJ2ePnF3TquzNX2yWzOCENTKNk1UjMJhyFgHxTCH6lxvZJg1l07M0hCc-v-14loAJ0efUU9V9hqS9mUabAT9QNysYL8E2tgIf)

## 2. Component 및 Release 등록

SW360에서 Component는 하나의 소프트웨어 단위입니다. 여기에는 다양한 형태의 소프트웨어가 해당할 수 있으며, 그 예는 다음과 같습니다.

* 오픈소스 소프트웨어
* 라이브러리
* 3rd party 소프트웨어

Component는 다음과 같은 정보를 포함합니다.  

* Component Name
* Main Licenses
* Categories \(예: Library, Cloud, Mobile, ...\)
* Component Type \(예: OSS, Internal, InnerSource, Service, Freeware\)
* Default Vendor
* Homepage URL

Release는 Component에서 하나의 Version을 가리키는 단위입니다. 따라서 하나의 Component는 여러 개의 Release를 가질 수 있습니다. Release는 하나의 Component 하위에 생성되어 관리됩니다.

Release는 다음과 같은 정보들을 포함합니다. 

* Component Name
* Version
* License
* Download URL
* CPE ID \(예: cpe:2.3:a:apache:maven:3.0.4\)

예를 들어, zlib-1.2.8을 등록해야 한다면, 먼저 Component에 zlib을 먼저 등록한 후, Release에 zlib 1.2.8을 등록합니다.  Menu &gt; Components &gt; Add Component를 선택하면 Create Component 화면으로 진입하여 zlib에 대한 정보를 등록할 수 있습니다.

![](https://lh6.googleusercontent.com/0a3ecmmFzumTZTaoWCOZPKkQIZLJwbPoAaduCTfwQMH_N67DPaMpTkerA4LOynwkl_nLkNT-pRh-rKzj4XHtBjoTkVMW9g06Rywryk3wbAj-Y3ONDg16VcGepMEm7m7Y8M3iDWyH)

Component를 생성하면, Components &gt; Releases &gt; Add Release에서 zlib-1.2.8 version에 대한 정보를 등록할 수 있습니다.

![](https://lh4.googleusercontent.com/ynUEB5-rGVYDirFghLx2v3tUt-uh-WL3YTN0siaGZWBrWQKYnIiV3B04mvdv3nZUW7t_U2Gl8msV_es1X181uq95YAp1bnqa0e3QLshhd1zhqk6z8ubPeEfo74cKdwho95_NyI1J)

하나의 zlib이라는 Component에 1.2.8과 1.2.11 version을 각각의 Release로 등록하였을 때, Release Overview 화면에서 다음과 같이 2개의 Release가 존재하는 것을 볼 수 있습니다.

![](https://lh3.googleusercontent.com/GxgMJQbNjRBNxMTMBvqEXNFNElXGXoCnaksCMs46ydREIrqrj7dFxMK0YkvjviHYMCiHY07xlR-Xixpa_C5nMFLzih0dXZAtv-6yKg4RdADJxr5qmDwhAEopVOaVNqzVWc3gMpLq)

SW360은 다수의 Component 정보를 Import 시키기 위한 기능을 제공합니다. 메뉴 &gt; Admin &gt; Import / Export에 CSV template에 등록을 원하는 Component 정보를 입력 후 Import 할 수 있습니다.  

![](https://lh5.googleusercontent.com/VInFwWAV-1lG1E7zFQPvn1GIlYPPY5ToGbSa49Brg7XuB-AwyCEHA9han0EUij1KX3c8aN2UZ1mKkN-5Y4BNv8LOV3O5YoypLQ7EF43QFPAU9L18XT57Ec5eoneswtGtt3rMSPoQ)

단, 이 기능은 2020년 2월 기준 아직 안정적으로 동작하지 않을 수 있습니다. 

## 3. Project 생성

Project는 하나의 제품을 가리킵니다. 사업 유형에 따라 제품일수도 있고, 서비스 혹은 소프트웨어 일수도 있습니다. Project에는 제품에 사용된 Component/Release를 등록하여 관리합니다.

Project 생성 시에는 다음과 같은 정보를 등록합니다. 

* Project Name
* Version
* Project type \(예: Product, Customer Project, Service, Internal Project, InnerSource\)

메뉴 &gt; Projects &gt; Add Project를 통해 Project를 생성할 수 있습니다.

![](https://lh6.googleusercontent.com/6gNtLci53U6zaU6Th5SHousuZ4VUijzuYjiJJlB0R6JwiHG4ggjb0RcnRYDkZCBhE2dMP2gGbT4qmB2FE5O8EW8hTfv1lgM4_XN0vzQUkttfTbX2cF0aNftHYuUy9EXczT2LzLO5)

Project를 생성하고 나면, 포함하는 Release나 하위 Project를 등록합니다. 메뉴 &gt; Projects에서 해당 Project를 선택하면 “Linked Releases and Projects”에서 Linked Projects와 Linked Releases를 등록할 수 있습니다. 

![](https://lh4.googleusercontent.com/ZjD7r7EzxfdQ4bhw4ODsChydb6Vgqj1m4Ad0cWlYtyYXO40MCbPpTHHcy-wJmbHeA_FxTa66Mpza6-9ohu0e93b7BaGb7Zc9soTA3mGCHGnyGURukRUnJS_duI7T8IL2aTgMFzjB)

다음은 SuperCalc라는 Project에 OpenSSL 1.0.1과 zlib 1.2.8을 Linked Releases로 등록한 이후의 화면입니다.

![](https://lh3.googleusercontent.com/tZCshPwxtukNLvfL-f-LfNOH-4ATof0bIGxpghVKXQ9QMBgoc_t0ROJMYafS9V4PuRaOOEW9zp25yk0gFA_kcaoRN83UKwUaFhaXxSWg7xPWvsYoJ_-pZkROkey1mYVTqGxKsCRu)

## 4. 보안 취약점 관리

SW360은 등록된 Release에 대해 보안 취약점이 있는지 자동으로 확인할 수 있습니다. 이를 위해 SW360은 CVE 정보를 주기적으로 수집하도록 스케쥴링하는 기능을 제공합니다. 메뉴 &gt; Admin &gt; Schedule 에서 CVE SEARCH 정보를 24시간마다 수집하도록 스케쥴링을 설정할 수 있습니다.

![](https://lh5.googleusercontent.com/V2AJbexZqJJqwFYD1kFpjdZ7zVM9PCd-I_6MSBu3djO2Gi6gQxxQpKoqqsETxDaSkpDXOKFOp9h0Fps1xYHEphesVX9ECwBwnSX5cWdziXoohh-CMmqRh_wVkwUD8dZE9w1raJRk)

이렇게 스케쥴링을 설정하면 SW360은 정해진 시간에 CVE Search 사이트\([https://cve.circl.lu/](https://cve.circl.lu/)\)에서 CVE 정보를 수집합니다. 수집한 CVE 정보는 메뉴 &gt; Vulnerabilities에서 확인할 수 있습니다. 

![](https://lh3.googleusercontent.com/dpIMyX7qCMdnibNihuL6RBSKg2fEckbOBPWJEtw08mY4quhv6Hh3BlgFIeydPOS6N8rF6ZSs4hpZgBGcXbcJI9saFDyfv4i-TCvxV5z-4LD9ZXpKah0jQU45j3iibxFpYoa7Hj9u)

이렇게 Vulnerabilities 정보가 수집된 이후에는 생성한 Project에 보안 취약점이 있는지 조회할 수 있습니다. 위에서 생성한 SuperCalc Project에서는 85개의 보안 취약점이 보고된 것을 확인할 수 있습니다. 

![](https://lh5.googleusercontent.com/lGeLbWHIBk6y2OSOXskcp4A2c5od0eTH6n7U5YG0p4cwTrrX02b6TpeRqJ7VXg5aUE7qDP2X2f8o4Rj1JsPHhZ-CUdLiy80O532Cgw-h_P9r-jHdL61QaXhFOPxIjTlX1cg9XPk5)

이와 같은 방법으로 기업에서 개발/배포하는 소프트웨어를 SW360에 등록하여 관리한다면, 오픈소스 컴플라이언스뿐만 아니라 보안 취약점에 대해서도 리스크를 최소화할 수 있는 형태로 관리가 가능합니다. 

또한 SW360은 위와 같은 Web Interface 뿐만 아니라 대부분의 기능을 REST API로 제공하여서 FOSSology 등의 다른 도구와의 연동이 가능합니다. : [https://github.com/eclipse/sw360/wiki/Dev-REST-API](https://github.com/eclipse/sw360/wiki/Dev-REST-API)

즉, 소스 코드 스캐닝 도구의 분석 결과를 SW360에 Import 시키는 등의 방법으로 DevOps에 Integration 시켜서 Project, Release 등록을 자동화시켜서 관리한다면 효율성이 크게 증가될 것입니다.   


