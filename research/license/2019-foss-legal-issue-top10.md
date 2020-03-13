# 2019 FOSS Legal Issue Top 10

DLA Piper의 IP 전문 변호사인 Mark Radcliffe는 최근 "[Top 10 FOSS legal developments in 2019](https://www-synopsys-com.cdn.ampproject.org/c/s/www.synopsys.com/blogs/software-security/top-10-open-source-legal-issues-2019/amp/)"라는 글을 기고하였습니다. Open Source Compliance에 관심 있는 분들에게 도움이 될 것으로 기대하여 내용을 제가 이해하는 선에서 정리해보았습니다. \(저는 법률가가 아니기 때문에 법적인 용어나 해석 부분은 미흡한 부분이 있을 수 있습니다. 보완이 필요한 부분을 알려주시면 고맙겠습니다.\)

### 1. McHardy \(Linux system copyright 트롤, 독일\), 새로운 전략 채택

Linux kernel의 초기 기여자인 Patrick McHardy는 독일에서 소송을 무기로 금적적인 이익을 취득하려는 Copyright 트롤과 같은 활동을 하였다. 그는 7년 반 동안 활동했으며, 80개가 넘는 회사에 접근한 것으로 알려져 있지만, 많은 기업이 소송까지 가지 않고 합의로 처리하였고, 독일 법원의 소송 절차는 기밀로 유지되기 때문에 정확한 수치는 추정하기는 어렵다. 2017년 McHardy가 소송을 제기한 [Geniatech 사건](https://www.jolts.world/index.php/jolts/article/view/128)의 항소 법원 판사는 2018년 GPLv2 위반에 대한 저작권 주장을 제기하는 McHardy의 주장에 대해 회의적으로 대응하였고, 결국 MacHardy는 소송을 취하하였다.

이후 McHardy는 추가적인 소송 제기하는 상황을 만들고 있지는 않지만, 여전히 GPLv2에 대한 Compliance 위반에 대한 주장을 계속하고 있다. 그는 그동안 가벼운 Contractual Penalty를 우선 체결하고, 이후 추가적인 위반을 발견해서 무거운 Penalty를 집행하는 방법으로 금전적인 이익을 취했다면, 2019년 초부터는 위반을 찾아내기 위해 그가 소비한 시간에 대한 배상을 요구\(과다한 Engineering cost 요구\)하는 새로운 전략으로 전환했다.

### 2. Richard Stallman, GNU, MIT 및 Free Software Foundation에서 사임

Richard Stallman이 Free Software Foundation의 President 겸 이사직을 [사임](https://www.fsf.org/news/richard-m-stallman-resigns)했다. Free Software \(및 Open Source\) 운동은 Richard Stallman의 비전과 지속적인 노력에 힘입은 바가 크다. 그러나 지난 수년간 그는 FOSS 운동 이외의 문제에 대해 여러 의견을 제시하여 논쟁을 불러일으켰다. Jeffrey Epstein 사건의 희생자에 대한 올해의 그의 진술은 Free Software Foundation으로부터의 사임 압력을 받게 하였다.

그는 또한 MIT에서 사임했고, GNU 운영 체제의 Maintainer들은 그를 쫓아냈다. 그들은 그의 기여에 대해서는 인정했지만, 다음과 같이 [언급](https://guix.gnu.org/blog/2019/joint-statement-on-the-gnu-project/)했다. "그러나, 몇 년 동안 Stallman의 행동이 GNU 프로젝트의 핵심 가치인 [모든 컴퓨터 사용자](https://www.gnu.org/gnu/manifesto.html#benefit)의 이익을 약화시켰음을 인정해야 한다. GNU는 리더의 행동이 우리가 도달하고자 하는 가치에서 멀어질 때 제대로 된 임무를 수행할 수 없다."

앞으로 누가 Free Software 운동의 리더십 역할을 맡을지는 분명하지 않다. 

\(관련 국내 기사 : [http://www.zdnet.co.kr/view/?no=2019091817351](http://www.zdnet.co.kr/view/?no=20190918173513)\)

### 3. OSS에 닥친 무역 전쟁

2019년 5월, 미 산업안전국\(BIS\)은 Huawei Technologies Co., Ltd. 및 68개 미국 이외의 계열사를 Entry List에 [올렸다](https://www.federalregister.gov/documents/2019/05/21/2019-10616/addition-of-entities-to-the-entity-list). BIS는 2019년 8월 Entry List에 46개의 미국 이외의 Huawei 계열사를 추가했다. 회사들은 BIS가 임시 라이선스를 발급한 4개 영역\(2019년 8월, 3개로 축소\)을 제외하고는 수출 관리 규정\(EAR\)에 해당하는 품목을 Huawei로 수출, 재수출, 또는 양도할 수 없다. 

Google은 즉시 Google Play Store와 같은 Google Service 뿐만 아니라 Android OS에 대한 접근을 [차단했다](https://www.theverge.com/2019/5/19/18631558/google-huawei-android-suspension)\(단, BIS 예외에 따라 일부 업데이트 제공\). Huawei는 Android Open Source Project를 사용하는 것으로 되돌아가야 했다. BIS는 Temporary General License를 여러 차례 연장했다. Huawei는 Android를 대체할 수 있는 버전을 개발 중이며, 다음 버전의 폰과 함께 배포할 수 있을 것이라고 [발표했다](https://www.engadget.com/2019/08/09/huawei-harmony-os-hongmeng-android/). 이번 Huawei의 Google Android OS 접속 중단은 영구적일 것으로 보여 Android가 미국에 본사를 둔 생태계와 중국에 본사를 둔 생태계 두 곳으로 쪼개질 가능성도 있다. 

### 4. OSS 라이선스에서의 윤리적 제한

OSS에는 윤리적인 이유에 대해 사용을 조건화하려는 여러 차례의 시도가 있었다. 올해, 여러 가지의 "Ethical License" 사례가 있었다. 한 예로, 개발자인 Seth Vargo는 자신의 open source library project인 Chef Sugar를 사용자들이 사용할 수 없도록 [삭제해버렸다](https://www.wired.com/story/developer-deletes-code-protest-ice/). 그는 Chef Sugar가 미국 이민 관세 수사청\(U.S. Immigration and Customs Enforcement, ICE\)과의 계약의 일부로 사용\(되었고, 그는 ICE가 불법 입국한 부모와 자녀를 격리 수용한 것을 비판하기\)때문에 Chef Sugar를 삭제했다. 

초기에는 Chef Sugar 제공사인 Chef가 Chef Sugar 프로젝트의 저작권을 소유하고 있다고 주장하며, 문제를 해결하려고 했다. Chef의 CEO는 Chef가 ICE에 서비스를 계속 제공할 것이라고 했지만, 4일 후 CEO는 Chef가 ICE와의 라이선스를 갱신하지 않고, ICE 계약의 수익을 이산가족\(ICE로 인해 헤어진 가족\)을 다루는 자선단체에 기부할 것이라도 [발표했다](https://www.businessinsider.com/chef-ice-contract-expires-next-year-2019-9). 

운동가인 Coraline Ada Ehmke는 [Hippocratic License](https://firstdonoharm.dev/)를 만들었다. 그녀는 이 라이선스가 "Open Source 프로젝트에 윤리를 추가"한다고 말한다. Hippocratic License는 MIT License에 다음 조항을 추가한다.:

“The software may not be used by anyone for systems or activities that actively and knowingly endanger, harm, or otherwise threaten the physical, mental, economic, or general well-being of other individuals or groups, in violation of the [United Nations Universal Declaration of Human Rights](https://www.un.org/en/universal-declaration-human-rights/).” 

OSI는 Hippocratic License가 "open source" 라이선스가 아니라고 신속하게 [언급했다](https://perens.com/2019/09/23/sorry-ms-ehmke-the-hippocratic-license-cant-work/). 불행히도 이 추가 조항으로 인해 매우 해석하기 어려운 라이선스가 됐다. 

### 5. 블록체인 프로젝트의 FOSS 전략

많은 [블록체인](https://www.synopsys.com/glossary/what-is-blockchain.html) 프로젝트가 FOSS 라이선스 하에 공개되었다. 블록체인 커뮤니티가 인프라 기술에 대한 복잡하고 특이한 선택을 했다. 새로운 블록체인인 Algorand 블록체인 프로젝트는 2019년 SDK, example application, helper library를 MIT License로 공개하였다. 그러나 Algorand node software는 [AGPLv3](https://github.com/algorand/go-algorand/blob/master/COPYING_FAQ)로 라이선스 되었다. 많은 회사의 법률 또는 Compliance 부서는 AGPLv3 하의 software는 compliance를 보장하기가 어렵기 때문에 이를 사용하지 못하도록 제한한다. 이로 인해 기업들이 Algorand 프로젝트를 채택하는데 어려움을 초래할 수 있게 되었다. 

### 6. Oracle v. Google 전쟁

연방 순회 항소 법원\(CAFC\)은 Oracle v. Google의 사건에 대한 두 번째 결정을 [발표했으며](http://www.cafc.uscourts.gov/sites/default/files/opinions-orders/17-1118.Opinion.3-26-2018.1.PDF), 여기에서 Google이 Android 운영체제에서 Oracle의 Java Application Programing Interface \(API\) 37개 package를 무단 사용한 것이 Oracle의 저작권을 침해했다고 판결하였다. 2014년 CAFC는 지방 법원의 1심 판결을 뒤집고 API가 저작권을 가지고 있다고 인정했으며, 다만 Fair Use 여부를 심리하도록 1심으로 환송하였다. 2016년 지방 법원은 Google의 API 사용이 Fair Use에 해당한다는 사실을 근거로 Google이 승소하는 판결을 내렸고, Oracle은 항소했다. 2019년 3월, CAFC는 다시 한번 지방 법원의 판결을 뒤집어 Google의 API 사용이 법적인 관점에서 Fair Use에 해당하지 않는다고 판결하였다. 대법원은 이송 명령서\(certiorari\)를 부여했다 \(2020년 3월부터 심리 예정\). 이 사건은 컴퓨터 소프트웨어의 저작권 보호 범위를 결정하는 데 매우 중요한 근거가 될 것이다. 

\(관련 국내 기사 : [https://byline.network/2020/02/11-94/](https://byline.network/2020/02/11-94/)\)

### 7. 독일 Hellwig/VMware case 종결

2015년 3월, Linux kernel의 핵심 개발자인 Christoph Hellwig는 독일 함부르크 지방 법원에 [VMware를 고소했다.](https://www.theregister.co.uk/2015/03/05/vmware_sued_for_gpl_violation_by_linux_kernel_developer/) Hellwig는 VMware가 \(1\) 파생 저작물을 생성하는 방식으로 Linux와 "vmkernel"이라는 VMware의 독점 코드를 결합하였음에도 \(2\) GPLv2에 따라 vmkernel의 완전한 해당 소스 코드\(complete corresponding source code\)를 제공하지 않음으로써 GPLv2의 조건을 위반했다고 주장했다. VMware ESXi 운영체제의 "kernel"인 vmkernel은 물리 서버의 하드웨어 및 소프트웨어 리소스를 관리한다. 

VMware는 vmkernel이 Linux의 파생 저작물이 아니라 단지 VMK API를 통해 Linux와 통신한다고 응답했다. 또한, VMware는 또한 vmkernel과 동작하는 드라이버는 Linux 드라이버일 필요는 없으며, "'vmklinux'라고 불리는 loadable kernel module을 통한 compatiblity alternative\(어떤 Linux driver와도 연동\)가 vmkernel에 의해 로드되고, VMK API를 통해 vmkernel과 인터페이스 한다."라고 [하였다](http://vmware.com/company/news/vmware-update-to-mr-hellwigs-legal-proceedings.html). 공소장 및 법정 문서들은 독일 법원의 규정에 따라 기밀로 유지되기 때문에 분쟁과 관련된 사실은 확인할 수 없다. 

함부르크 법원은 Hellwig가 자신이 개발한 Linux 시스템의 구성 요소와 VMware가 해당 구성 요소를 사용했는지 여부를 입증하지 못했다는 근거로 Hellwig의 소송을 기각했다. 함부르크 고등 법원은 1심 판결에 대한 항소를 기각했으며, Hellwig는 그 결정에 항소하지 않기로 결정했다. 두 법원은 고소장의 실질적인 문제는 다루지 않았으며, Linux에서 가져온 일부 component의 right ownership 또는 copyright protection 능력에 대한 불충분한 증거에 근거하여 결정을 내렸다. 

이러한 결정에 대한 대응으로 VMware는 "VMware는 소송과 무관하게 vSphere에서 vmklinux를 제거하기 위한 활동을 다년간 활발히 진행해 왔으며, 향후 major release에서 이를 달성하기를 희망한다"라고 [발표했다](https://www.vmware.com/company/news/updates/march-2019-hellwig-legal-proceedings.html). 

### 8. OSS 비즈니스 모델 및 라이선스

많은 상용 FOSS 회사들이 전통적인 OSS 라이선스는 Cloud Service Provider가 FOSS 회사에 비용을 지불하지 않고도 그들의 프로그램을 사용하는 것을 허용한다는 우려를 표명한다. 2019년 6월, CockroachDB는 Open Source 운동의 창시자 중 한 명인 Bruce Perens가 MariaDB를 위해 처음 개발한 [BSL \(Business Source License\)를 채택했다](https://www.cockroachlabs.com/blog/oss-relicensing-cockroachdb/). CockroachDB의 CEO는 다음과 같이 말했다. "오늘 우리는 매우 permissive 한 라이선스인 BSL \(Business Source License\)를 채택한다. CockroachDB의 사용자는 CockroachDB를 여러 노드로 확장할 수 있다. CockroachDB를 사용하거나 application에 포함시킬 수 있다 \(application을 고객에게 배포하거나 servicve 형태로 실행하거나 상관없이\). 내부적으로 서비스로 실행할 수도 있다. **단 하나의 유일한 제한은 라이선스를 구매하지 않은 상태로 CockroachDB를 상용 버전의 서비스로 제공할 수 없다는 것이다.**"

11월, Sentry도 [BSL을 채택했다](https://blog.sentry.io/2019/11/06/relicensing-sentry/). 2018년에 채택된 새로운 라이선스들에도 몇 가지 새로운 발전이 있었다. 2018년 Redis Labs는 Redis 모듈의 라이선스를 AGPL에서 Common Clause가 추가된 Apache v2.0으로 변경하였다 \(이 Redis 모듈은 Redis core 위에 add-on 된다\). Common Clause는 Cloud Service Provider에 의한 제품 사용을 제한하기 위해 Apache Software License version 2에 추가되는 형식으로 도입되었다. 이 혼합 라이선스의 도입은 논란의 여지가 많았으며, Redis는 Commons Clause를 포기하고, RediSearch, RedisGraph, RedisJSON, Redis-ML 및 RedisBloom에 [Redis Source Available License를 채택했다](https://redislabs.com/blog/redis-labs-modules-license-changes/). 다른 회사들도 비슷한 라이선스를 채택했다.

### 9. FOSS governance와 표준 제정기구 governance를 사용하는 프로젝트 간 RAND 특허 라이선스에 대한 충돌

FOSS가 하나의 개발 방법론으로 널리 보급되면서 표준 제정기구 \(standard setting organizations / SSO\)는 FOSS 접근 방식을 자신의 프로세스에 통합하기 위해 노력해왔다. 그러나 FOSS 프로젝트와 SSO의 방법론은 상당히 다르다. FOSS 프로젝트는 매우 다양한 책임과 더 분산된 방식으로 실행된다. 특히 마찰이 되는 요인 중 하나는 SSO의 일반적인 접근 방식으로써 SSO는 멤버들에게 royalty-bearing 기준\(공정하고, 합리적이고, 비차별적 혹은 FRAND 조건으로 / FRAND : Fair, Reasonable, And Non-Discriminator\)의 특허권을 부여한다. 이러한 마찰은 open source license에서 특허 라이선싱에 관한 분쟁을 다룬 기사들에서 보여준다 \([here](http://www.stlr.org/download/volumes/volume20/kappos.pdf) 및 [here](http://stlr.org/2019/03/04/oss-and-frand-complementary-models-for-innovation-and-development/)\).

David Kappos 전 특허청장은 다음과 같이 [언급했다](http://stlr.org/2018/10/15/the-truth-about-oss-frand-by-all-indications-compatible-models-in-standards-settings/). "대신, 우리는 OSD 준수 라이선스는 명시적 특허 허여 조항이 없는 한 특허 라이선스를 부여하는 것으로 가정해서는 안 된다는 반대 결론에 대한 상당한 지지를 얻었다. 즉, OSS 라이센서는 특허 라이선스를 부여하는 라이선스를 선택하거나, MIT와 Berkely처럼 부여하지 않는 라이선스를 선택할 수 있다. 그래서 OSS와 실질 표준특허\(standard-essential patents, SEP\)가 혁신을 발전시키는데 협력할 수 있는 능력을 보존할 수 있다."

반면에 Van Lindberg는 다음과 같이 [응답했다](http://stlr.org/2019/03/04/oss-and-frand-complementary-models-for-innovation-and-development/). : "이것이 open source와 FRAND가 상호보완적이지만 호환될 수 없는 이유이다.: open source와 FRAND는 서로 다른 지적 재산 정책에 의존하여 혁신해간다. 이 두 개발 모델은 서로 배우고, 서로 경쟁할 수 있지만, 근본적으로 다른 기본 원칙을 기반으로 한다. "

"SSO가 OSS를 포함시키려는 이유는 이해할만하다. open source는 저렴하고, 상호 운용이 가능하며, 혁신적이다. SSO는 OSS와 상호 운용성을 확보하기 위해 변화할 수 있는 능력이 있다. 많은 조직이 그랬던 것처럼 Royalty-free IPR\(지식 재산권\) 정책을 채택하기만 하면 된다. 그러나 FRAND 로열티를 부과하고자 하는 SSO라면 궁극적으로 open source를 다룰 때 상업적인 기업들이 가지고 있는 것과 같은 선택권을 가지고 있는 것이다. 즉, OSS 사용 시 준수해야 하는 라이선스와 규칙을 존중하거나, 아니라면 상용 버전을 만들어내는데 시간을 투자해야 한다. "

특허에 대한 로열티 지불 방식의 차이는 FOSS와 SSO 커뮤니티 사이에 긴장을 유발하고 있다. 그리고 일부 SSO 커뮤니티는 "open source"가 무엇인지 정의할 수 있어야 한다고 주장했다. 이 문제는 가까운 시일 내에 해결되지 않을 것 같다.

### 10. Open source license, 데이터 및 암호 문제로 확장

데이터는 "new oil"이라고 불린다. Open source 개념이 데이터 라이선스에 적용되었다\(2017년 Linux Foundation의 [Community Data License Agreement](https://cdla.io/) 참조\). 그러나 올해에는 데이터와 사이버 보안\(cybersecurity\)에 적용되었다. 예를 들어, Holochain에서 잘 알려진 open source 변호사인 Van Lindberg에 의해 [Cryptographic Autonomy License](https://github.com/holochain/cryptographic-autonomy-license) \(CAL\)가 개발되었다. Holochain은 이 라이선스에 대해 다음과 같이 [설명했다](https://medium.com/holochain/understanding-the-cryptographic-autonomy-license-172ac920966d). "분산 앱의 경우, 암호화 키\(cryptograhpic key\)는 code와 user data 사이의 낯선 중간 영역에 들어간다. Code는 기능적이며 컴퓨팅 시스템의 입력 또는 출력으로 user data를 라우팅하고 변환하는 프로세스를 제공한다. User data는 일반적으로 code에 의해 처리되고 저장될 수 있는 수동 콘텐츠에 더 가깝다. 암호화 키는 user data이면서 기능적\(functional\)이다. Holochain에서 암호화 키는 데이터의 소유권에 대한 증명을 조율한다 : 데이터가 어디에 저장되는지, 누가 데이터를 제어하는지, 통신과 스토리지의 보안과 암호화를 누가 확인하는지, 데이터의 순서와 무결성을 확립하는 progressive hashing 및 signning을 위한 체인 구조의 운영 등."

CAL은 user data와 관련하여 다음과 같은 의무를 [제공한다](https://github.com/holochain/cryptographic-autonomy-license/blob/master/README.md). "Throughout any period in which You exercise any of the permissions granted to You under this License, You must also provide to any Recipient to whom you provide services via the Work, a no-charge copy, provided in a commonly used electronic form, of the Recipient’s User Data in your possession, to the extent that such User Data is available to You for use in conjunction with the Work."

또한 이 라이선스는 또한 보안상의 결함을 다루는 경우, 소스 코드 제공의 지연을 허용하는데 이는 새롭고 환영받는 접근 방식이다. "You may delay providing the Source Code corresponding to a particular modification of the Work for up to ninety \(90\) days \(the ‘Embargo Period’\) if: a\) the modification is intended to address a newly-identified vulnerability or a security flaw in the Work, b\) disclosure of the vulnerability or security flaw before the end of the Embargo Period would put the data, identity, or autonomy of one or more Recipients of the Work at significant risk, c\) You are participating in a coordinated disclosure of the vulnerability or security flaw with one or more additional Licensees, and d\) Access to the Source Code pertaining to the modification is provided to all Recipients at the end of the Embargo Period."

Linux Foundation은 JDF \(Joint Development Foundation\)을 통해 open data 문제에 대해 작업을 계속했다. JDF는 AWS, Genesys 및 Salesforce와 협력하여 Cloud 애플리케이션 전반에서 데이터 상호 운용성을 표준화하는 open source data 모델인 Cloud Information Model을 개발했다. 

