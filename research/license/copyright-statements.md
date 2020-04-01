---
description: How and why to properly write copyright statements in your code
---

# 코드 내 저작권 표시를 해야 하는 이유와 올바른 방법

오픈소스 분야의 저명한 변호사인 Matija Šuklje는 최근 소스 코드 내 저작권 표시가 필요한 이유와 올바르게 작성하는 방법을 소개하였습니다. : [https://matija.suklje.name/how-and-why-to-properly-write-copyright-statements-in-your-code](https://matija.suklje.name/how-and-why-to-properly-write-copyright-statements-in-your-code)

여기서는 이 글의 주요 사항을 소개합니다. 

## TL;DR

이 글 전체를 읽을 시간이 도저히 없다면, 최소한 이것 만이라도 보세요. 

아래 포맷의 저작권 및 라이선스 표시 당신이 작성한 모든 소스 코드 파일에 추가하세요. 

```text
SPDX-FileCopyrightText: © {$year_of_file_creation} {$name_of_copyright_holder} <{$contact}>

SPDX-License-Identifier: {$SPDX_license_name}
```

예를 들어, 내가 오늘 소스 코드 파일을 하나 작성하였고, 이를 [BSD-3-Clause](https://spdx.org/licenses/BSD-3-Clause.html) 라이선스로 공개하였다면, 다음과 같은 내용을 파일 상단 주석 부분에 추가합니다. 

```text
// SPDX-FileCopyrightText: © 2020 Matija Šuklje <matija@suklje.name>
// 
// SPDX-License-Identifier: BSD-3-Clause
```

참고로 [REUSE.software](https://reuse.software/) 프로젝트의 가이드를 따르면 모든 파일에 적절한 표시가 되었는지 확인할 수 있습니다. 

## 저작권이란?

저작권은 \([베른 협약](https://en.wikipedia.org/wiki/Berne_Convention) 이후\) 저작자가 저작물 만들때 자동으로 생성됩니다. 모든 저작물은 저작권에 의해  보호되며, 저작권 보유자에게 저작물에 대한 독점적인 권한을 부여합니다. 따라서 당신의 저작물\(소스 코드, 텍스트, 이미지, 기타 미디어 등\)을 다른 사용자가 사용할 수 있게 하려면 그들에게 라이선스를 부여해야 합니다. 라이선스의 사전적 정의는 "특정 권리를 실행하기 위해 자격이 있는 기관으로 부터 받은 허가"이며, 이러한 허가 없이 특정 권리를 실행하는 것은 불법 행위가 됩니다. 

이에 따라 당신이 다른 사람의 소스 코드를 복사, 수정 등의 작업을 하려면 필요한 권한을 부여 받아야 합니다. 즉, 라이선스를 받아야 합니다. 만약, 그 라이선스가 권리 실행 허가 조건으로 특정 의무를 요구한다면, 당신은 권리 실행을 위해서는 그 의무사항도 따라야만 합니다. 

어쨌든, 저작권법의 기본 요건을 준수해야 하며, 최소한 다음 두 가지가 필요합니. 

* **저작자 표시 \(attribution\)** : 저작권 보유자 및/또는 저자를 명시합니다. \(특히 도덕적 권리를 인정하는 관할권에서\)
* **라이선스 \(license\)** : 라이선스는 저작권 보유자 이외의 다른 사람에게 코드를 사용할 권한을 부여하는 유일한 방법이기 때문에 라이선스를 고지하고 전체 라이선스 텍스트를 제공하는 것이 좋습니다. 이는 당신이 내보내는 Outbound 라이선스나 복사된 코드나 라이브러리 같은 3rd party 저작물을 사용하면서 다른이로부터 받는 Inbound 라이선스 모두에 해당합니다. 

{% hint style="warning" %}
Inbound vs. Outbound 라이선스

당신이 사용자\(downstream\)에게 부여한 라이선스를 Outbound 라이선스라고 부릅니다. 이는 당신으로부터 흘러 나오는\(out\) 코드의 권한을 다루기 때문입니다. 반대로, 동일한 코드의 동일한 라이선스가 사용자 입장에서는 그들에게 흘러 들어오는 \(in\) 코드의 권한을 다루기 때문에 Inbound 라이선스로 간주됩니다. 

간단히 말해, 유입되는 권한을 설명하는 라이선스를 Inbound 라이선스라고 하고, 유출되는 권한을 설명하는 라이선스를 Outbound 라이선스라고 합니다. 
{% endhint %}

다행인 점은 저작자 표시는 저자의 권리이지 의무는 아닙니다. 또한 사용자는 저자가 저작자 표시 권리를 사용한 경우에만 이를 유지해야 하는 의무가 있습니다. 즉, 저자가 저작자 표시를 하지 않았을때에는 사용자가 이 표시하려고 수고하지 않아도 됩니다. 

## 왜 저작권 표시를 해야 하나요?

1989년 베른 협약에 가입하기 전까지 미국 저작권법은 저작물을 보호하려면 명시적인 저작권 표시를 요구했습니다. 그러나 베른 협약으로 저작권 표시를 하지 않아도 저작권은 자동으로 생성됩니다. 그럼에도 저작권 표시는 유용합니다. 

{% hint style="warning" %}
저작권 표시가 법에 의해 요구되는 것은 아니지만, 실제로는 해당 저작물의 저작권이 누구에게 있는지에 대한 증거로서 매우 유용합니다. 또한, 이는 컴플라이언스 측면이나 코드 추적을 위해서도 큰 도움이 됩니다. 
{% endhint %}

저작권 표시는 실질적으로 다음과 같은 이유때문에 필수적입니다. 

1. 대부분의 라이선스가 저작권 표시를 요구합니다. 
2. 라이선스에서 요구하지 않더라도 대부분의 관할권의 저작권 법률에서 요구합니다. 
3. \(이러한 요구가 없더라도\) 사용자는 법적 또는 기술적인 이유로 원저작에게 연락하기를 원할 수도 있습니다.

따라서, 저작물에 저작자의 이름과 연락처 정보를 포함하는 것은 의미가 있습니다. 

## 저작권 표시 및 라이선스 고지의 올바른 방법

### 저작권 표시 

저작권 표시는 다음 정보로 구성합니다. 

* © 기호로 시작합니다. 
* 처음 발행한 연도 : 처음 소스 코드 파일을 작성한 연도입니다. 더 이상 수정하지 마세요.
* 저작권 보유자의 이름 : 일반적으로 저자이지만, 저자의 고용주일 수 있습니다. 또한, CLA에 따라 다른 법인이나 개인이 될 수도 있습니다. 
* 유효한 연락처 : 저작권 보유자에게 연락할 수 있는 정보

예를 들어, 오늘 소스 코드 파일을 작성했다면 다음과 같이 저작권 표시를 파일 상단 헤더 부분에 추가합니다. 

```text
// © 2020 Matija Šuklje <matija@suklje.name>
```

### 라이선스 고지

또한, 코드를 공개하면서 라이선스가 무엇인지 알리는 것도 매우 중요합니다. [SPDX ID](https://spdx.org/ids)를 사용하면 코드의 라이선스를 명확하게 알릴 수 있습니다. 라이선스 고지가 명확하지 않으면 이를 보는 사용자에게 혼란을 야기시킬 수 있습니다. 

### REUSE.software

[REUSE.software](https://reuse.software/) 프로젝트는 SPDX tag를 사용해서 저작권 표시와 라이선스 고지를 작성하는 Best Practice를 제공합니다. 

* 저작권 표시 : SPDX-FileCopyrightText
* 라이선스 고지 : SPDX-License-Identifier

아래의 예는 위의 모든 사항을 고려하고 SPDX 및 REUSE.software 요구사항을 모두 준수하는 저작권 표시 및 라이선스 고지입니다. 

```text
// SPDX-FileCopyrightText: © 2020 Matija Šuklje <matija@suklje.name>
// 
// SPDX-License-Identifier: BSD-3-Clause
```

이제 당신이 작성한 모든 소스 코드 파일에 이러한 주석이 포함되었는지 확인하세요!

## Q&A

### 왜 연도를 표시해야 하나요?

어떤 사람들은 연도를 생략하고 단순하게 작성하는게 오히려 저작권 표시를 유지하기 쉬울 것이라고 주장합니다. 실제로 이는 Microsoft와 GitHub의 정책이기도 합니다.

나는 연도를 표시하지 않는게 작업을 크게 단순화한다는 데에는 동의하지만, 이를 유지한다면 코드 베이스에서의 모호한 타임라인을 확인하는데 도움이 된다고 생각합니다. 또한, 발명이 처음으로 일반인에게 언제 공개되었는지를 알아내는데 유용할 수 있습니다. 특히 특허 방어에 유용하게 사용될 수 있을 겁니다. 

이런 사항들을 고려한 한 예로 Liferay의 새로운 정책에서는 파일 생성 연도를 작성하고, 연도를 더 이상 변경하지 않습니다. 

### 연도 표시를 변경하지 않는게 좋다고요?

다음과 같은 저작권 표시를 보았을 겁니다. 

```text
Copyright (C) 1992, 1995, 2000, 2001, 2003 CompanyX Inc.
```

이렇게 계속해서 연도를 추가하는건 이렇게 해야 저작권으로 보호되는 시간을 연장할 수 있다는 생각이 있기 때문이며, 널리 행하여 지고 있습니다. 하지만, 불행하게도 이런 작업은 쓸모가 없고, 오히려 해가 될 수도 있습니다. 

게다가 새로운 변경이나 기여를 받을 때마다 이렇게 그 연도를 추가하는 행위를 법적으로 본다면 논란의 여지가 있습니다. 문제는 모든 기여가 저작권을 주장할 수 있을 정도로 독창적이거나 규모가 있지 않습니다. 따라서, 모든 기여에 대해 법률에 의해 저작권 보호를 받을 수 있을 만큼 독창적인지 여부를 먼저 판단하고, 그에 따라 저작권 표시에 연도를 추가해야 문제 소지가 없을 것입니다. 

반면에 저작권은 저자의 사망 이후 \(혹은 저작권자가 법인일 경우, 발행 이후\) 최소 50년 \(보통 70년\) 동안 지속됩니다. 따라서, 굳이 저작권 표시에 연도를 계속해서 추가하지 않아도 저작권을 주장하지 못하게 될 위험은 매우 낮습니다. 

게다가, 일반적으로 하나의 소스 코드 파일은 소프트웨어를 구성하는 수많은 파일 중 하나일 뿐입니다. 소프트웨어가 성장해가면서 새롭게 파일이 추가될텐데, 그 때 새로운 파일을 작성한 연도를 추가해간다면 전체 저작물로서의 소프트웨어에는 최신 연도의 저작권 표시가 이미 포함되는 것이죠. 

{% hint style="warning" %}
**Git/VCS 히스토리를 더럽히지 마세요.** 

만약 매년 모든 파일에 연도 표시를 새롭게 추가한다면 이로 인해 Git/VCS 히스토리가 불필요하게 길어지게 되고, 저장소 공간을 소비하며, 정작 중요한 정보를 찾을 때 방해가 될 수 있습니다.
{% endhint %}

### 연도를 범위로 표시하는건 어떤가요?

연도를 범위로 표시하는 것\(예: 1999-2020\)도 매년 연도 표시를 변경해줘야하기 때문에 위의 질문에서 언급한 모든 사항이 동일하게 적용됩니다. 

어떤 경우는 '{$year}-present'와 같은 형태로 범위를 지정하기도 합니다. 이 또한 위에서 언급한 사항들이 대부분 적용되며, 추가로 또 다른 혼란을 줄 수 있습니다. 'present'가 의미하는 것은 추상적입니다. 다음 중 어떤 것을 의미하는걸까요?

* 파일이 마지막으로 수정 시간?
* 패키지가 릴리즈된 시간?
* 처음 다운로드 한 시간?
* 마지막으로 실행한 시간?
* 아니면 바로 지금?

이와 같이 'present'는 전혀 도움이 되지 않는 표시입니다. 

### Git/Mercurial이 저작권 정보를 추적하는데 더 좋지 않나요?

항상 그렇지는 않습니다. Git \(및 다른 VCS\)은 메타데이터 관리에 뛰어나지만, 항상 이를 의존하는 것은 주의해야 합니다. 

먼저 Git은 'Committer' 필드와 별개로 'Author' 필드가 있습니다. 기여자마다 'Author' 필드에 제각각의 값을 포함시킬 뿐더러, 'Author' 필드에 입력된 자가 실제 저자라고 가정하여도 저자는 저작권 보유자가 아닐 수도 있습니다. 

더 중요하게는, 파일이 저장소에서 옮겨지게 되면 메타데이터는 사라집니다. 소스 코드만 압축해서 배포한다거나, 저장소를 fork 혹은 rebase하는 방식으로 각 파일을 새로운 코드베이스로 복사하면 이전까지의 추적 데이터는 더 이상 확인할 수 없습니다. 

이러한 문제들은 모든 파일에 저작권 및 라이선스 정보를 표시하면 해결됩니다. [REUSE.software](https://reuse.software/)의 Best Practice는 이를 아주 잘 처리합니다. 

### 왜 © 기호를 사용하나요?

어떤 사람들은 "Copyright"이라는 영어 단어가 더 자주 사용되고, 많은 사람들이 익숙하다고 주장할 수도 있지만, 실제로 저작권법을 보면 "©" \(Copyright Sign\)을 사용하는 것이 저작권 진술을 위한 유일한 방법임을 알 수 있습니다. 

또한, © 는 "common global denominator"이기 때문에 이를 사용하는 것이 합리적입니다. 

{% hint style="warning" %}
EU에서의 한 예로, 슬로베니아의 ZASP §175. \(1\)은 독점적 저작권 보유자가 자신의 저작물을 표시하기 위해 "\(c\)" 또는 "©"로 표시할 수 있다고 명시하고 있습니다. 

반면에 미국에서는 17 U.S. Code § 401. \(b\)\(1\) 에서는 다음과 같이 더 다양한 단어를 사용하는 접근법을 제공합니다. 

"the symbol © \(the letter C in a circle\), or the word “Copyright”, or the abbreviation “Copr.”"
{% endhint %}

© 기호가 호불호가 있을 수 있지만, 실용적인 관점에서 볼 때 가장 덜 중요한 부분입니다. 위에서 설명했듯이 저작권은 자동으로 생성되기 때문에 어떤 기호를 쓰느냐에 따라 법적인 리스크가 달라지지는 않습니다. 

### 왜 연락처를 남겨야 하나요? 두 명 이상의 저자가 있을때는?

연락처 정보는 저작권법에 의해 요구되는 것은 아니지만, 실용적인 이유로 매우 유용할 수 있습니다. 

법적 또는 기술적인 문의를 위해 코드의 저자 또는 저작권 보유자에게 연락해야 할 수도 있습니다. 코드가 어떻게 동작하는지 물어보거나 수정을 요청할 수도 있습니다. 라이선스 문제를 발견하여 문제를 해결할 수 있도록 도움을 주거나 별도의 라이선스를 요청해야 할 수도 있습니다. 이 모든 경우에 연락처 정보가 많은 도움이 됩니다. 

* 현재까지도 이메일이 자주 사용 되는 연락 방법이기 때문에 저작권자의 이메일 주소를 제공하는 것이 가장 좋습니다. 
* 저작권이 매우 분산되어 있거나 법인인 경우도 있습니다. 이런 경우에는 프로젝트 또는 법인 홈페이지의 URL을 제공하는 것이 더 합리적일 수 있습니다. 
* 프로젝트에서 AUTHORS 또는 CONTRIBUTORS와 같은 파일에 저작권 보유자를 표시하는 경우 해당 파일을 가리키는 링크를 제공하는 것도 좋은 옵션입니다. 

### Public Domain에 대해 설명해주세요.

Public Domain은 까다로운 개념입니다. 

일반적으로 Public Domain은 저작권 기간이 만료된 저작물입니다. 

일부 관할권 \(예: 미국, 영국\)에서는 자신의 저작권을 포기하고 저작물을 Public Domain으로 제공할 수 있는 반면, 대부분의 관할권\(예: 대부분의 EU 회원국\)에서는 이런 행위가 불가능합니다. 이는 해당 관할권에 따라 저자가 자신의 저작물을 Public Domain으로 제공한다고 표시했다고 하더라도 이것이 실제로 발생하기 위한 법적 기준을 충족할 수 없고, 결국 여전히 자신의 저작물에 대한 저작권을 보유하고 있을 수 있다는 것을 의미합니다. 

따라서 저작권과 라이선스를 진지하게 다루는 오픈소스 컴플라이언스 담당자들은 "this is public domain"이라는 표시를 매우 경계합니다. 

저작권자는 이같은 문제는 다음 두가지 방법으로 완화시킬 수 있습니다.

* "public domain"이라는 단어를 사용하는 것 대신, [CC0-1.0 ](https://spdx.org/licenses/CC0-1.0)과 같은 매우 허용적인 라이선스를 적용하세요. 
* "SPDX-FileCopyrightText:" 필드에 이름과 연락처 정보를 포함하세요. 저작권자가 어떤 의도로 public domain이라고 표시했는지 의심이 들거나, 어떤 불분명한 사항이 있을 경우 연락을 취하여 문제를 해결할 수 있게 합니다. 

### Minified JavaScript는 어떻게 하죠?

최근의 Minifier는 주석을 제거하더라도 저작권 및 라이선스 정보는 보존하는 옵션을 제공합니다. 코드를 minify할 때 이런 옵션을 사용하여 저작권과 라이선스 정보를 유지하세요. 

{% hint style="warning" %}
소스 코드를 다른 언어나 컴파일러 및 다른 형태로 변환하더라도 모두 저작권 보유자에게 독점적 권리가 있습니다. 따라서, minify한 코드를 사용할 때에도 유효한 라이선스가 필요합니다. 
{% endhint %}

### "All rights reserved"에 어떤 문제가 있나요?

종종 저작권 표시에 "All rights reserved"라는 문장을 본 적이 있을겁니다. 저작권법은 이런 표현을 요구하지 않습니다. 아마 음악 CD나 책에서 사용하는걸 보고 단순히 모방해서 사용하는게 아닐까 생각합니다. 하지만, 오픈소스에서 이런 표현은 혼란을 야기시킵니다. 

"All rights reserved"는 명백히 오픈소스 라이선스와 모순됩니다. 오픈소스 라이선스는 누구나 코드를 사용, 연구, 공유 및 개선할 수 있는 권리를 제공합니다. 반면에 "All rights reserved"는 이러한 모든 권리가 자신에게만 부여된다는 표현입니다. 

"All right reserved"는 이와 같은 문제만 가져올뿐, 어떤 이점도 가져오지 않기 때문에 사용하지 말아야 합니다. 
