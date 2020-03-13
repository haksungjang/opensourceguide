---
description: A Publication of The Linux Foundation
---

# OSS Supply Chain Security

2020년 2월, Linux Foundation에서는 Open Source Software Supply Chain에서의 보안 리스크를 알리기 위한 글을 작성하였으며, 여기에서는 이에 대한 내용을 정리해보았습니다. 

{% hint style="info" %}
원문 출처 : [https://www.linuxfoundation.org/publications/2020/02/open-source-software-supply-chain-security/](https://www.linuxfoundation.org/publications/2020/02/open-source-software-supply-chain-security/)
{% endhint %}

{% file src="../../.gitbook/assets/oss\_supply\_chain\_security.pdf" %}

## Introduction

현대의 Software 개발은 지난 수십 년보다 훨씬 복잡한 프로세스가 되었다. 하나의 조직 내에서 Software 모두를 자체 개발하는 경우는 거의 없다. 대신 대부분의 조직은 Open Source Software\(OSS\)를 활용한다. 다양한 OSS를 포함하면서 서로 연결되는 부분만 자체 개발하여 제품을 개발한다. 

"Software Supply Chain"은 이미 매우 복잡하다. 예전에는 Software가 CD와 같은 물리적 매체를 사용하여 고객에게 제공되었다면, 오늘날의 Software는 \(OSS 및 독점 Software 모두\) "repository"에 저장이 되고, Project Dependency Manager \(PDM\)이나 Package Manager를 통해 수시로 원격으로 배포된다. 

![](https://t1.daumcdn.net/thumb/R1280x0.fpng/?fname=http://t1.daumcdn.net/brunch/service/user/9399/image/UFqIj_ywPKiBf0csdt91M6rzRSU.png)

Software Supply Chain에서의 보안에 대한 최근의 관심은 대부분이 이 Chain의 첫 번째 요소인 Developer이거나 혹은 마지막 부분인 End User였으나, 취약점은 모든 레벨에서 존재한다. 다음과 같은 사건을 살펴보자. 

### 2015년 악성코드 배포를 위한 Xcode Repackaging

2015년 한 보안회사는 App Store를 통해 배포되는 39개의 Application이 iPhone 및 iPad를 감염시키고 있다고 Apple에 경고했다. 디바이스에 다운로드된 악성 Application은 원격 Command/Control 서버에 접속되어 중요한 사용자 정보를 업로드했다. 추가 조사에 따르면 Apple의 공식 개발 플랫폼인 Xcode의 "repackaged" 버전을 통해 악성 코드가 Application에 삽입된 것으로 나타났다. 

이 App들은 즉시 제거되었고, Apple은 합법적인 개발자만이 Xcode의 공식 버전에 액세스 할 수 있도록 추가 조치를 취했지만, 이 사건은 Software Supply Chain 내에서 여러 Application에 영향을 미칠 수 있는 Software의 보안 취약점에 대한 위험을 부각했다.

{% hint style="info" %}
Apple scrambles after 40 malicious “XcodeGhost” apps haunt App Store, Dan Goodin, ArsTechnica \(Sep. 25, 2015\), [https://arstechnica.com/information-technology/2015/09/apple-scrambles-after-40-malicious-xcodeghost-apps-haunt-app-store/](https://arstechnica.com/information-technology/2015/09/apple-scrambles-after-40-malicious-xcodeghost-apps-haunt-app-store/) 
{% endhint %}

### 2016년 "left-pad" Dependency 사고

2016년, 관련 없는\(unrelated\) OSS package에 대한 명명권 분쟁에 이어, 한 유명한 개발자가 Node.js 코드를 배포하는 데 사용되는 Software Registry인 npm에서 모든 OSS package를 제거했다. 이 개발자는 npm에서 총 273개의 package를 제거했지만, 문제는 하나의 package에서 나타났다. "left-pad" 

믿을 수 없을 정도로 간단한 package인 "left-pad"는 텍스트를 오른쪽 정렬하여 읽기 쉽게 텍스트 출력을 제공하다. 그러나 "left-pad"는 수많은 중요한 하위\(downstream\) Package가 의존성을 갖고 있었기 때문에, "left-pad"의 갑작스러운 사라짐은 수많은 하위 Package들이 깨지는 문제를 유발했다. 다른 개발자가 기능적으로 동등한 package로 사라진 package를 대체하였지만, downstream 개발자들은 자신의 코드를 업데이트하고, 새로운 package를 참조하도록 해야 하는 문제가 남아 있었다. 

이 사건은 개발자들이 거의 통제할 수 없는 upsgream package에 의존할 때 직면하는 위험을 극명하게 부각했고, 더불어 광범위한 "dependency" 문제를 드러냈는데, 문제는 이 package가 상위\(upstream\) dependency로 내포되어 있기 때문에 "left-pad"에 의존할 의향이 전혀 없는 개발자들도 영향을 받았다. 

이 "left-pad" 사건은 3년 전에 일어났지만, 여전히 이와 같은 문제들은 남아있다. 

{% hint style="info" %}
Rage-quit: Coder unpublished 17 lines of JavaScript and “broke the Internet”, Sean Gallagher, ArsTechnica \(March 24, 2016\), [https:// arstechnica.com/information-technology/2016/03/rage-quit-coder-unpublished-17-lines-of-javascript-and-broke-the-internet/](https://%20arstechnica.com/information-technology/2016/03/rage-quit-coder-unpublished-17-lines-of-javascript-and-broke-the-internet/) .
{% endhint %}

### 2017년 Python Package \(PyPI\) Highjacking

2017년 공격자들은 Build-in Python library의 이름을 "매우 비슷하게" 만든 악성 library를 만들었다. 이를 의심하지 않은 개발자들은 이 악성 library들을 다운로드하였다. 이 악성 package들은 원본과 동일한 코드를 포함하지만, 설치 스크립트는 악성 코드를 포함하도록 변경이 되어 있었다. 

{% hint style="info" %}
Goodin, Dan. 2017-09-16. “Devs unknowingly use “malicious” modules snuck into official Python repository: Code packages available in PyPI contained modified installation scripts.” Ars Technica. [https://arstechnica.com/information-technology/2017/09/devs-unknowingly-use- malicious-modules-put-into-official-python-repository/](https://arstechnica.com/information-technology/2017/09/devs-unknowingly-use-%20malicious-modules-put-into-official-python-repository/) 
{% endhint %}

### 2018년 Python Package Highjacking

2018년 Python Software Repository에서 "Colourama"라고 불리는 암호 화폐 도용\(cryptocurrency-stealing\) package가 발견되었다. 이 packgae의 이름을 의도적으로 Python repository내에서 가장 많이 다운로드되는 20가지 Software 중 하나인 합적적인 package "Colorama"와 비슷하게 해서 혼동을 주었다. 이 악성 package가 발견되었을 때 단지 151번만 다운로드되었지만, 피해를 입은 디바이스에서 감염을 제거하는 데에는 많은 노력이 필요했으며, 이로 인해 Software repository의 보안 취약성이 부각되었다. 

{% hint style="info" %}
Two new supply-chain attacks come to light in less than a week, Dan Goodin, ArsTechnica \(October, 23, 2018\), [https://arstechnica.com/ information-technology/2018/10/two-new-supply-chain-attacks-come-to-light-in-less-than-a-week/](https://arstechnica.com/%20information-technology/2018/10/two-new-supply-chain-attacks-come-to-light-in-less-than-a-week/).
{% endhint %}

### 2018년 “event- stream” Library의 백도어

2018년, 가장 널리 사용되는 JavaScript library 중 하나가 백도어로 암호 화폐 도용 코드가 삽입되었다. 주목할만한 것은 이 삽입이 유사한 사건들보다 훨씬 더 정교해졌다는 것이다 \(백도어 발견 시점에 이 라이브러리는 2백만 회의 다운로드 수를 기록했다\). 

우선, 백도어 뒤의 악의적인 공격자들은 개발자들에게 도움을 제공함으로써 event-sream package에 대한 합법적인 publishing 권한을 얻었다. 일단 그들은 권한을 얻은 후, 이를 이용하여 양호한 packag를 npm registry, flatmap-stream에 추가하였고, 이 package를 event-stream 자체의 dependency로 추가하였다. 약 한 달 후, 이 악성 공격자들은 인기 있는 암호 화폐 지갑 Software를 대상으로 하는 ftatmap-stream에 악성 코드를 추가했다 \(따라서, event-stream에도 추가됨\). 

이러한 단계적 공격 \(staged attack\)은, 공격자들이 event-stream package에 대한 publishing 권한을 얻기 위해 취한 노력과 함께, 새로운 코드와 새로운 개발자들을 면밀히 조사하는 방식에 약점이 있음을 보여주는 것뿐만 아니라, 악의적인 공격자들이 그러한 노력을 기울인다는 점을 보여준다. 이는 유사한 공격이 계속될 뿐만 아니라, 빈도와 정교함에서도 증가할 가능성이 있음을 시사한다. 

{% hint style="info" %}
Widely used open source software contained bitcoin-stealing backdoor, Dan Goodin, ArsTechnica \(November 26, 2018\), [https:// arstechnica.com/information-technology/2018/11/hacker-backdoors-widely-used-open-source-software-to-steal-bitcoin/](https://%20arstechnica.com/information-technology/2018/11/hacker-backdoors-widely-used-open-source-software-to-steal-bitcoin/)
{% endhint %}

### 2019년 7월, 인기 있는 Ruby Gems Package의 계정 탈취

2019년 7월, codebase를 업데이트한 한 개발자는 dependency 중 하나에서 changelog.md 파일이 누락된 것을 발견했다. 영향을 받은 package인 strong\_password는, 변경 사항에 대한 설명 없이, 그리고 Github에서 호스팅 되는 코드와 Ruby repository에서 호스팅 되는 코드 간에 차이가 있는 상태로, 0.0.6에서 0.0.7로 업데이트되었다. 이 개발자는 추가 조사를 통해 그 package가, production environment 내에서 실행될 때, 원격 URL에 접속하여 추가 코드를 가져와서 그 코드가 포함하도록 업데이트되었음을 발견했다. 일단 그렇게 되면, 새로운 코드는 감염된 환경 내에서 원격 코드가 실행될 기회를 제공했다.

그 개발자는 그 package의 original maintainer에게 이를 통보하였고, 그 maintainer는 자신의 Ruby repository 계정이 탈취되었음을 발견했다. 악의적인 공격자는 maintainer의 계정을 더럽혔고, package 소유권을 변경한 다음, 백도어 코드를 게시했다. 확인되지는 않았지만, original maintainer는 2단계 혹은 다단계 인증 \(2FA or MFA\)이 없었던 것이 악의적인 공격자가 자신들의 개발자 계정에 접근할 수 있었던 원인이라고 믿었다. strength\_password와 같은 dependency는 다양한 환경에서 배포되기 때문에, 그리고 신뢰도에 대한 명성을 얻은 유명한 개발자와 관련이 되어 있기 때문에, 그런 개발자의 계정을 탈취하는 것은 가치가 크다. 이와 비슷한 공격은 증가할 것이다. 

{% hint style="info" %}
strong\_password v0.0.7 rubygem hijacked, Tute Costa \(July 3, 2019\), [https://withatwist.dev/strong-password-rubygem-hijacked.html](https://withatwist.dev/strong-password-rubygem-hijacked.html)
{% endhint %}

### 2018-2019년 Webmin Compromise

2018년 4월에 시작하여 2019년 8월에 발견된, 인기 Webmin 관리 도구에 알려지지 않은 악의적인 공격자가 백도어를 사용했다. 변경은 비교적 작았지만, 상당한 영향을 미칠 수 있었다. 백도어를 사용한 악의적인 공격자는 특수하게 조작된 URL을 활용하여 감염된 서버에 명령을 전송할 수 있고, 이는 최상위 권한 \(root\)으로 명령을 실행할 수 있게 한다. 

Webmin 개발자에 따르면, Webmin 소스 코드가 포함된 서버는 2018년 4월에 악용 되어 악성 코드가 삽입되었다고 한다. 그때 공격자는 관련 서버 로그를 변경하여 파일이 한동안 업데이트되지 않은 것처럼 보이게 하여 코드 비교 툴과 같은 일반적인 탐지 메커니즘으로부터 감지되는 것을 숨겼다. 외부에서 0-day 공격의 일부로 백도어가 공개되었다는 것을 발견한 2019년 8월 17일까지 변경된 코드는 감지되지 않았고, 추가적인 악의적인 행동은 지속되었다. 

Webmin의 maintainer가 감염을 제거하고 추가 단계를 수행했지만, 이 사건은 이러한 Software의 취약성과 악의적인 공격자에게 지속적인 매력이 있다는 걸 보여주는 또 다른 사례가 되었다. 

{% hint style="info" %}
The year-long rash of supply chain attacks against open source is getting worse, Dan Goodin, Ars Technica \(August 21, 2019\) [https:// arstechnica.com/information-technology/2019/08/the-year-long-rash-of-supply-chain-attacks-against-open-source-is-gettingworse/](https://%20arstechnica.com/information-technology/2019/08/the-year-long-rash-of-supply-chain-attacks-against-open-source-is-gettingworse/); Webmin page explaining exploit, Webmin, [http://www.webmin.com/exploit.html](http://www.webmin.com/exploit.html).
{% endhint %}

### 2019년 8월, 11개의 백도어 RubyGems Library 발견

2019년 8월, Ruby library를 조사한 한 개발자에 의한 분석 결과, 11개의 백도어 된 package가 발견되었다. 각각의 경우, 백도어는 미리 선택된 자격 증명을 보유한 악성 공격자들이 감염된 서버에서 원격으로 코드를 실행할 수 이도록 했다. 

감염된 package는 또한 암호 화폐 채굴을 가능하게 했다. 각 library가 어떻게 감염됐는지는 불분명하지만, 적어도 한 개 의상의 package에 대해서는 개발자 계정이 해킹됐기\(compromise\)때문에 코드의 수정이 가능했다. 그 계정은 이전에 크랙 된 패스워드를 사용해왔으며, 2FA나 MFA로 보호되지 않았다. 

이러한 사건들은 package manager와 repository에 의해 사용되는 현재의 정책, 프로세스 및 절차에 내재된 약점을 보여준다. 상황을 더욱 악화시키는 것은, supply chain의 이러한 요소들이 현대의 software 개발에서 필수 불가결하기 때문에, 거의 모든 경우에 조직들은 이러한 요소들을 사용해야 하고, 따라서 통제할 수 없는 높은 수준의 위험에 노출되게 된다. 

끝으로, software supply chain과는 별개이지만 필수 불가결한 최종 요소가 하나 있다. : "Vulnerability Database"

현대 software 개발의 분산되고 압도적으로 복잡한 특성을 감안하면, 배포된 softare에서 발견되는 vulnerability를 식별, 분석, 치료 및 추적하는 것은 매우 중요하다. 그러나, CVE \(Common Vulnerabilities and Exposures\) 프로그램에서 제공하는 NVD \(National Vulnerability Database\)는 세계에서 가장 의존도가 높은 vulnerability 추적 database인데, 현대 software 개발의 성장, 속도 및 복잡성으로 인해 계속 어려움을 겪고 있다. 이러한 어려움은 CVE 및 NVD 프로그램에 의존하는 개발자 및 회사에 직접적인 영향을 미치며 Software Supply Chain의 보안 및 안정성에 전체적으로 영향을 미친다. 여기서는 현재 Software SupplyChain에 영향을 미치는 보안 및 안정성 문제에 대해 살펴보고, 전반적으로 개선하기 위해 변경할 수 있는 부분과 방법을 소개한다. 

## Software Supply Chain 조사

### 개발자 Practice

개발자는 앞에서 소개한 그림에서 Software Supply Chain의 첫 번째에 표시되어 있다. 이것은 사실이기도 하지만, 개발자들은 모든 단계에 존재에 어디에나 존재한다. 개발자들은 프로그래밍 language, repository, PDM을 선택한다. 그들은 소비자가 구매할 회사의 완성 제품을 구성하는 library, package 및 OSS를 선택한다. 즉, 개발자들은 Software Supply Chain에서 가장 없어서는 안 될 구성원이다. 

그러나 많은 개발자들은 Software를 개발할 때 보안 Best Practice를 따르지 않는다. 여기에는 여러 가지 이유가 있다. 그중 하나는, 오늘날의 Software 개발은 엄청나게 복잡한 과정이다. 따라서, 하나의 "Best Practice"의 전략이 다른 사람에게는 치명적인 약점이 될 수도 있다는 걸 감안해야 한다. 또 다른 이유로, 보안은 종종 개발자와 user experience에 방해가 되는 역할로 보인다. 결과적으로 많은 개발자들은 올바른 보안 practice의 사용을 피하거나 최소화한다. 

이렇게 보안 practice를 무시하거나 꺼리는 건 여러 가지 결과를 가져오고, 그중 많은 것은 위에서 설명한 Supply Chain 사건에서 강조되었다. 개발자들이 다음과 같은 보안 Practice를 사용했다면 이러한 사건들 중 많은 부분을 피할 수 있었을 것이다. 

* 특정 프로젝트의 설계, 구축 및 유지 관리와 관련된 개발자 계정 및 기타 중요 계정에 대해 2단계 혹은 다단계 \(2FA 또는 MFA\) 인증 사용
* 개발 프로세스 전반에 걸쳐 프로젝트가 change contrl tracking\(누가 변경했는지, 언제 변경되었는지 포함\)을 지원하도록 요구
* 프로젝트가 각 release에 대해 고유한 version identifier를 갖도록 보장하여 downstream user가 새로운 release를 추적하고, 이를 control 및 verification 하는 mechanism을 구축할 수 있게 함
* 프로젝트의 개발 lifecycle에 testing을 통합하여 일반적인 버그와 예기치 않은 동작을 확인하는 것뿐만 아니라 개발자가 알지 못하는 상태로 이루어지는 악의적인 변경이 있는지 확인
* Downstream user가 쉽게 소비할 수 있도록 프로젝트의 dependency를 문서화하고 전달하는 것을 보장하는 도구 또는 다른 mechanism을 활용
* Dependency를 적절하게 추적, 분석, 관리하는 도구 활용
* 암호화 Signing 또는 프로젝트의 무결성에 대해 입증 가능한 증거를  presenting
* 새로 개발된 코드 및 프로젝트에 통합된 OSS dependency 모두에 대해 vulnerability를 추적하고 치료

많은 개발자들이 이들을 준수하지 못하고 있다. 필요한 자원, 전문지식 또는 지원이 부족해서일 수도 있다. 그러나 분명한 건, 이런 Best Practice를 따르지 못한다면 개발자뿐만 아니라 Software의 최종 사용자에게 심각한 결과를 초래한다는 것이다. 

### Repository

예전에는 많은 Software 개발이 협력업체나 벤더로부터 라이선스 된 코드를 사용하였지만, 현재는 대부분의 개발이 인터넷에서 제한 없이 무료로 검색된 대량의 OSS를 포함시키고 있다. 많은 개발자들은 "repository"라고 알려진 Software 저장소를 의지하여 개발한다. 

기본적으로 Software Repository는 Software Package 세트를 보관하는 서버이다. 이러한 Package는 소규모 Utility Library에서부터 Full Command Line Tool 및 개발 Framework에 이르기까지 다양하다. 일반적으로 Linux 시스템은 Operating System repository를 사용하여 Linux 배포판을 기반으로 application과 해당 application의 depencency를 관리한다. 해당 배포판의 개발자들은 repository의 집합 내에서 모든 package를 관리하며 upstream software package의 release를 기반으로 최신 package를 유지하고, 필요할 경우, 해당 package의 보고된 보안 및 기타 버그를 수정한다. 

Perl로 시작하여 interpreted programming language가 성장함에 따라, 사용자를 위해 "helper" library의 확장된 repository를 제공하는 것이 유리해졌다. 이러한 repository의 크기 때문에, 이들은 일반적으로 개별 Linux 배포판의 main packaging에서 제외되었다. 이러한 language별 repository의 성장으로 인해 해당 language를 사용하는 모든 개발자는 비개발 시스템에서 개발 software를 실행해야 하는 시기뿐만 아니라, 필요한 dependency를 설치하기 위해 language repository 도구를 사용해야 한다. 

오늘날 software 개발의 상당 부분이 OSS에 의존하고 있으며, 전 세계에서 가장 의존적인 OSS의 많은 부분이 그들의 library를 위해 language repository에 의존하는 language로 작성되기 때문에, 개발자들은 이러한 repository에서 software의 일부를 추출해야 한다. 그러나, 다양한 역사적, 경제적 이유로 그러한 language repository는 기본적인 보안이나 품질 관리조차 결여되어 있다. 예를 들면 : 

* 현재 저장된 코드가 목적대로 검사 되는 mechanism을 제공하는 language repository는 거의 없으며, 소비자 혼동을 증가시키고, 경우에 따라 악의적인 활동을 가능하게 한다. 
* 저장된 코드 또는 deprecated package의 vulnerability를 체계적으로 검사하는 langugae repository는 거의 없다. 
* 현재 소비자가 저장된 코드 중 하나가 다른 코드에서 파생되었는지 여부를 확인할 수 있는 mechanism을 제공하는 language repository는 없으며, 이는 vulnerability 또는 다른 문제가 dependency로부터 이어지는지 여부를 확인할 능력을 제한한다. 
* 대부분의 language repository에서, 취약하거나 누락된 인증 및 publisher verification mechanism은 저장된 코드의 출처에 대한 불확실성과 위험을 야기한다. 
* 일부 language repository는 개발자 계정에 대해 2단계 또는 다단계 \(2FA 또는 MFA\) 인증을 제공하지 않으며, 종종 이를 요구하지 않거나, 이를 조장하거나, 개발자 계정\(및 계정을 제어하는 package\)이 취약하게 보호되고 있음을 다른 사람에게 알려준다. 
* 많은 language repository가 code signing을 제공하지만, 그러한 서명의 유효성을 검증하기 위한 강력한 mechanism을 제공하거나 가능하게 하는 경우는 거의 없다. 
* 일부 language repository는 성실한 소비자들이 자기 스스로 저장된 코드에 대해 보안 및 품질 분석을 수행할 수 없도록 제한하는 EULA \(End User License Agreement\)를 포함한다. 
* 많은 language repository는 생성된 package가 다른 사람이 검사할 수 있는 예상된, 공개적으로 사용 가능한 소스에서 생성되었는지 검증하지 않거나, 다른 사용자가 쉽게 확인할 수 있도록 하지 않는다. 

일부 language repository는 이러한 우려들을 해결하기 위한 조치를 취했지만, 모든 문제를 해결하는 mechanism을 개발한 repository는 없다. 또한, 이러한 우려를 해결하려고 시도한 일부 language repository의 경우, 저장소 자체를 "상업화"하였고, "premium" 서비스를 이용하는 고객들에게만 이런 기능을 제공한다. 결과적으로, 기본적으로 필요한 보안과 품질 제어는 많은 일상 소비자의 손이 미치지 않는 곳에 남아 있다. 

### Project Dependency Manager \("Package Manager"\)

오늘날 대규모의 Software를 효율적으로 관리가 위해서는 간단하면서도 강력한 도구가 필요하다. 그러한 도구가 많이 존재하지만, 그중 가장 널리 보급되고 있는 것은 "package manager"이다. package manager는 software package, library 등 파일을 특정 시스템에서 설치, 업그레이드, configuring 및 제거하는 과정을 자동화한다. 특히, "project/application dependency manager"\(PDM\)이라고 하는 package manager가 자주 사용된다. 

PDM을 활용하면서 사용자는 software를 찾고 설치하고 구성하는 이전의 복잡한 여러 단계를 하나의 단계로 전환할 수 있다. PDM은 위에서 설명한 것과 같은 language repository에 연결하여 간접적으로 의존성이 있는 모든 software를 포함하여 사용자가 지정한 software를 검색하고, 구성한다. 이러한 방식으로 software 검색과 관리를 단순화하면서 PDM은 현대 software 개발에 필요한 전문지식과 자원의 수준을 크게 줄였다. 

그러나 PDM은 단순한 software 검색 도구일 뿐이다. PDM은 검색된 software에 대해 다음 사항을 확인하지 않으며, 이를 수정하기 위한 실행 가능한 방법도 없다. 

* 알려진 보안 및 신뢰성 문제가 있는지
* 예상치 않은 혹은 악의적인 행동이 포함되었는지
* 오해의 소지가 있는 package 이름이 있는지 \("typosquatting" 및/또는 built-in library의 이름과 비슷한\) 

{% hint style="info" %}
* Vaidya et al, “Security Issues in Language-based Software Ecosystems, March 6, 2019, [https://arxiv.org/abs/1903.02613](https://arxiv.org/abs/1903.02613)
{% endhint %}

대신에, 이런 practice는, 위에서 논의한 바와 같이, 일반적으로 software supply chain의 다른 부분에서 수행되어야 하는데, 일반적으로 그렇지 못한다. 이로 인해 어느 정도의 보안과 품질을 보장하기 위한 PDM 사용자와 PDM maintainer의 노력은 검색된\(retrieved\) software 내에서 좌절된다. 특히, PDM과 관련된 보안 사고의 빈도가 증가되는 것에서도 볼 수 있듯이, PDM의 현재 절차 내에 내재된 약점들은 악의적인 공격자들에게 인기 있는 수단이 되고 있기 때문에 문제가 된다. 

### Vulnerability Database

위에서 논의한 바와 같이 현대의 software는 많은 software package가 함께 구성된다. 이러한 "building block" package는 독점 코드, 라이선스 받은 코드, 또는 OSS 일 수 있으며, 수십 개에서 수천 개의 block이 구성될 수 있다. 이는 상당한 이점을 제공하지만, 위험 또한 초래한다. 오늘날 개발자와 회사는 자체 코드의 버그와 취약점뿐만 아니라 제품이 의존하는 각각의 software package에 대해서도 관리해야 한다. 

현대 software 개발이 사내 개발 전략보다 앞서가는 것처럼, 현대 software에서 발견되는 취약점과 버그의 수, 다양성 및 고유성은 사내의 취약점 tracking으로 따라가는 것은 불가능하다. 이는 software 커뮤니티가 초기에 인정한 현실이었고, 이에 따라 취약성과 버그의 지정, 설명 및 추적을 위한 표준화된 미국 기반의 프로그램인 CVE \(Common Vulnerability and Exposure\) 프로그램과 NVD \(National Vulnerability Database\) 프로그램을 만들게 되었다. 

이 두 프로그램은 20년 이상 존재했으며, 많은 현대의 사이버 보안 도구, 제품 및 practice의 토대가 되었다. 

{% hint style="info" %}
The NVD is considered so important that in 2018 it was exempted from the U.S. government shutdown. See “Closed Down: Government Shutdown Impacts Enterprise Security, December 31, 2018, [**https://duo.com/decipher/government-shutdown-impacts-enterprise-security** ](https://duo.com/decipher/government-shutdown-impacts-enterprise-security)
{% endhint %}

그러나 최근 몇 년 동안 두 프로그램 모두 새로운 기술의 놀라운 성장과 함께, NVD로의 추가 요청이 크게 증가하면서 어려움을 겪고 있다. 이러한 어려움은 다음과 같은 여러 가지 downstream 문제를 야기시켰다. 

* vulnerability가 누락되거나 거부되어 NVD의 불완전한 coverage를 초래 \(Over 6,000 vulnerabilities went unassigned by MITRE’s CVE project in 2015, Steve Ragan, CSO Online \(Sep. 22, 2016\), [https://www. csoonline.com/article/3122460/over-6000-vulnerabilities-went-unassigned-by-mitres-cve-project-in-2015.html](https://www.%20csoonline.com/article/3122460/over-6000-vulnerabilities-went-unassigned-by-mitres-cve-project-in-2015.html).\)
* vulnerability identifer의 할당이 심각하게 지연되면서, 이를 알지 못하고 있는 downstrea party에게 위험을 초래
* vulnerability에 대한 설명이 부족하여 치료와 관리의 어려움이 증대
* 과도하게 부풀려지거나 낮게 평가된 vulnerability score로 인해 리소스가 잘못 할당되거나, 어떤 경우에는 vulnerability " 피로"가 발생
* 이력서를 채우기 위해 vulnerability 수를 부풀리는 개발자에 의한 남용
* 할당된 vulnerability가 유효하지 않은 것으로 판명될 경우, 이를 취소하는 게 어렵고, 혼동을 유발하여 전체 프로그램에 대한 신뢰 부족 초래
* CVE 할당을 정상적인 Software 업그레이드를 수행할 수 없는 어려운 관리 절차를 회피하는 방법으로 간주하는 조직의 엔지니어에 의한 남용
* CVE 프로그램이 미국 연방 기관에 의해 관리되는 것 자체가 불편
* 장기간에 걸쳐 여러  package를 여러 번 수정해야 하는 지속적이고 복잡한 vulnerability를 처리할 수 없음

결과적으로 거의 모든 현대 기업, 연방 기관 및 기타 조직을 포함하여 CVE 및 NVD 프로그램에 의존하는 많은 이해관계자들은 vulnerability 노출을 완전히 해결하지 못하고 있다. 더 나쁜 것은, NVD coverage의 부족해서 알람이 적은 상황임에도 이해관계자들은 자신들의 제품이 안전하고 신뢰할 수 있다고 믿는 잘못된 보안 의식을 야기할 수 있다는 것이다. 

### End User Practice

Software supply chain의 최종에 있는 이들의 위치를 고려할 때 End User는 보안에 대한 통제력이 가장 낮을 것이다. 

![](https://t1.daumcdn.net/thumb/R1280x0.fpng/?fname=http://t1.daumcdn.net/brunch/service/user/9399/image/FO95cqN6sfQpgXkxjSfHnZnJRog.png)

그러나, supply chain이 loop 형태라고 생각한다면 이야기는 달라진다. 

![](https://t1.daumcdn.net/thumb/R1280x0.fpng/?fname=http://t1.daumcdn.net/brunch/service/user/9399/image/uG9Vz6BGSxxkyT2FHCYrJATMwbM.png)

End User의 경우 일반적으로 기술 공급 업체의 솔루션을 사용할 것이고, 이 경우, PDM 또는 OSS package 선택에 대한 결정을 내릴 수 없다. 하지만, End User는 "인수 요구사항" \(Acuisition Requirement\)을 통제할 수 있다 \(다만, 많은 User는 이를 충분히 활용하지 않고 있다\). 

여기서의 Best Practice는 End User가 기술 제공업체와 협상할 때 계약서에 다음과 같은 요구사항을 추가하는 것이다. 

* Dependency List, Software BOM \(bills-of-material\) 또는 이러한 component tracking mechanism이 매우 견고하고 투명한 방식으로 제공된다. 
* 제품 내의 Vulnerability는 특정 기간 내에 개선되어야 한다. 
* 개발에 관련된 모든 개발자 계정은 2FA 또는 MFA를 사용해야 한다. 

End user가 자신의 솔루션 내의 OSS package에 대해 개발자 Practice에서 논의된 동일한 practice를 자체적으로 수행하는 경우도 있다. 또한, 이러한 practice와 "인수 요구사항" practice 외에도 End User가 취할 수 있는 실질적인 단계가 있다. 즉, Software 신뢰도를 검사하고, Software 다운로드는 신뢰할 수 있는 곳에서 하고, 그들이 수취한 software가 요청한 software인지 확인하는 것이다. 그리고 Supply chain 문제의 영향을 줄이기 위해 Software에 주는 권한을 제한하는 것이다.

그럼에도 여전히 다음과 같은 사실은 남아 있다. 

* Software가 실제로 "신뢰할 수 있다"\(trustworthy\)는 것이 무엇을 의미하는지 합의된 이해가 부족하고 효과적인 도구가 없기 때문에 Software가 신뢰할 수 있는지 판단하기 어렵다. 
* 이와 유사하게, 위에서 논의한 repository와 같은 다운로드 장소가 신뢰할 수 있는지를 알아내는 것은 어렵다. 
* User는 정종 그들이 요청한 Software가 그들이 신뢰하는 package인지 아니면 악의적, 사기적, 혹은 잘못된  것인지 확인하기 어렵다. 
* 마찬가지로, User는 그들이 받은 Software가 자신들이 원하는 software인지 digital signature를 확인하는 등의 방법으로 확인하지 못한다. 그리고, 일부 user는 보안, 품질 등의 확인도 없이 software를 받자 마다 코드를 실행한다. 

End User는 Software Supply Chain에 영향을 미칠 수 있는 가장 좋은, 그리고 가장 나쁜 위치에 있다. Vendor로부터 기술을 취득하는 기업의 경우, acquition practice를 활용하여 vendor에게 보안 best practice를 적용하도록 권장할 수 있지만, 여전히 제공받은 제품의 결함을 시정하거나 혹은 이를 알아내는 조차도 어려움이 있다. 자신의 Software를 스스로 관리하려는 End User의 경우, 이를 위해서는 End User가 본질적으로 개발자가 되어야 하고, 이를 위해 적절하게 행동해야 함을 인식해야 한다. 두 경우 모두, End User는 현대의 Software 개발이 변화하면서 그들 자신의 행동도 변화해야 함을 알아야 한다. 

## 결론

현대의 Software 개발은 "Supply Chain"이 대규모로 분산되어 있다. 계속 증가만 하는 이런 경향은 제품의 평균 출시 시간을 줄이고, 상당한 가치를 창출했지만, 또한 위험과 남용의 기회를 창출했다. 

Software repository, package manager 및 vulnerability database는 이를 활용하는 개발자 및 End User와 마찬가지로 모두 software supply chain에서 필요한 구성 요소이다. 그러나 현재의 내재된 vulnerability가 해결되지 않는 한, 이에 의존하는 기업과 개발자들은 계속해서 중대한 위험에 노출될 것이다. 이 글은 Software supply chain 내의 알려진 문제를 강조하고 이를 해결하기 위한 조치를 취하기 위해 작성되었다. Linux Foundation은 이러한 문제를 해결하기 위한 종합적인 솔루션을 설계하기 위해 글로벌 기술 리더 회의를 소집할 것이다. 

