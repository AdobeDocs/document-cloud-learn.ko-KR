---
title: Acrobat Sign 텍스트 태그 지정
description: 텍스트 태그 지정으로 Acrobat Sign 양식 필드를 만드는 방법에 대해 알아봅니다.
feature: Workflow, Sign
role: User, Admin
level: Experienced
jira: KT-6059
thumbnail: KT-6402.jpg
exl-id: 3a54925d-b713-487b-92b7-ec7160513696,c981c640-e50a-4952-ac39-2f90d6d0cf08
source-git-commit: 06ec359f950cc8e589bc6c97219acc32f460b969
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 2%

---

# Acrobat Sign 텍스트 태그 지정

텍스트 태그 지정으로 Acrobat Sign 양식 필드를 만드는 방법에 대해 알아봅니다. 텍스트 태그는 Microsoft Word, Adobe InDesign 등의 작성 도구에 직접 추가하거나 Acrobat에 PDF이 있는 경우 추가할 수 있습니다. Acrobat Sign에서 사용되는 문서를 준비하는 데 드는 노력을 크게 줄일 수 있습니다. Acrobat Sign에서 태그가 있는 문서를 업로드한 다음 템플릿으로 설정할 수 있으므로 누구나 자신의 문서에 필드를 추가할 필요가 없습니다.

## 시작하기

텍스트 태그는 문서 내 어디에든 배치된 고유한 형식의 텍스트 조각으로,
Acrobat Sign에 업로드하면 자동으로 필드로 인식됩니다.

    ![텍스트 태그의 구문](../assets/syntax.png)

텍스트 태그는 Microsoft Word, Adobe InDesign 등의 작성 도구에 직접 추가하거나
PDF — Acrobat 텍스트 태그를 사용하면 준비하는 데 드는 노력을 크게 줄일 수 있습니다
Acrobat Sign에서 사용되는 문서.

## Microsoft Word에서 태그 추가

Microsoft Word 문서에 텍스트 태그를 추가하려면 이 [비디오 자습서](text-tagging-word.md)를 확인하세요.

## Acrobat에서 태그 추가

Adobe Acrobat은 강력한 끌어다 놓기 양식 작성 환경을 갖추고 있습니다. Acrobat에서 텍스트 태그를 적용하면 Acrobat Sign에서 사용할 수 있는 추가 기능을 이용할 수 있습니다.

1. Acrobat에서 양식을 엽니다.

1. **[!UICONTROL 모든 도구]** 패널에서 **[!UICONTROL 양식 준비]**&#x200B;를 선택합니다.

1. **[!UICONTROL 양식 만들기]**&#x200B;를 선택합니다.

1. **[!UICONTROL 옵션]** 패널 드롭다운에서 **[!UICONTROL 전자 서명 양식 준비]**&#x200B;를 선택합니다.

   ![전자 서명 양식 준비](../assets/tag-prepare-e-signing.png)

1. **[!UICONTROL 다음]**&#x200B;을 선택하여 확인합니다.

   ![필드 변환 확인](../assets/tag-confirm.png)

1. 필드를 두 번 클릭하여 **[!UICONTROL 속성]** 대화 상자를 표시합니다.

   양식 필드 이름을 변경하려면 [Acrobat Sign Text Tag Guide](https://helpx.adobe.com/kr/sign/using/text-tag.html)에 자세히 설명된 구문을 사용합니다.

1. 예를 들어, 필드 이름에 *OInt_es_:signer1:optinitials*&#x200B;를 입력하여 이니셜 필드를 선택적으로 만들 수 있습니다.

   ![필드 이름 변경](../assets/tag-opt-initials.png)

   텍스트 태그는 양식 필드 이름에 추가되며 Microsoft Word(또는 다른 제작 도구)에서 사용하는 구문과 달리 중괄호는 포함되지 않습니다.

   양식 필드의 이름만 바꾸면 필드 패널에서 텍스트 태그를 추가할 수도 있습니다.

   ![필드 패널에서 이름 바꾸기](../assets/tag-rename.png)

1.  파일을 저장하고 닫습니다.

1. Acrobat Sign에서 파일을 업로드하고 다음 섹션의 설명대로 재사용 가능한 템플릿을 만듭니다.

## 재사용할 수 있는 템플릿을 생성합니다.

태그가 있는 문서를 만든 다음 재사용 가능한 템플릿으로 설정하여 누구나 문서에 필드를 추가할 필요가 없도록 합니다.

재사용 가능한 템플릿을 만들려면 이 [비디오 자습서](../sign-advanced-users/create-a-template.md)를 확인하세요.
