---
description: How and why to properly write copyright statements in your code
---

# 코드 내 저작권 표시를 해야 하는 이유와 올바른 방법

오픈소스 분야의 저명한 변호사인 Matija Šuklje는 최근 소스 코드 내 저작권 표시가 필요한 이유와 올바르게 작성하는 방법을 소개하였습니다. : [https://matija.suklje.name/how-and-why-to-properly-write-copyright-statements-in-your-code](https://matija.suklje.name/how-and-why-to-properly-write-copyright-statements-in-your-code)

여기서는 이 글의 주요 사항을 소개합니다. 

## TL;DR

이 글 전체를 읽을 시간이 도저히 없다면, 최소한 이것 만이라도 보세요. 아래 포맷의 저작권 및 라이선스 표시을 당신이 작성한 모든 소스 코드 파일에 추가하세요. 

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

저작권은 \([베른 협약](https://en.wikipedia.org/wiki/Berne_Convention) 이후\) 자동으로 생성되며 모든 저작물은 저작권에 의해 자동으로 보호됩니다. 

