---
title: GigaSign을 사용하여 대용량 문서 수집
description: Gigasign을 사용하면 동시에 수천 명의 사람들에게 서명을 받을 문서를 보내고 수집하고 추적할 수 있습니다
feature: Workflow
role: Developer
level: Intermediate
jira: KT-6626
topic-revisit: Integrations
thumbnail: 328113.jpg
exl-id: a59eab61-fe61-45c6-8137-f074e1f2b3ed
source-git-commit: ba9931920ab3bfb6ea38a92cac4a35da1d0295cd
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%

---

# GigaSign을 사용하여 대용량 문서 수집

Gigasign을 사용하면 동시에 수천 명의 사람들에게 서명을 받을 문서를 보내고 수집하고 추적할 수 있습니다. 직원 및 고객과의 대량 커뮤니케이션을 위해 설계되었으며 각 대량 전송에 최대 2,500명의 수신자를 지원합니다. GigaSign은 Acrobat Sign API를 사용하여 MegaSign과 동일한 기능을 제공하며 여러 서명자, 수신자 그룹, 수신자 역할, 계약 이름, Carbon Copy 등에 대한 지원을 포함합니다.

>[!IMPORTANT]
>
>GigaSign은 더 이상 최신 버전의 Java 또는 Acrobat Sign으로 업데이트되지 않으며 제한된 지원만 제공합니다. GigaSign의 기능은 [대량 전송](https://experienceleague.adobe.com/docs/document-cloud-learn/sign-learning-hub/admin-set-up/getting-started-admin/megasign.html?) 기능 아래에 제품에 추가됩니다. GigaSign의 사용이 명시적으로 필요하지 않은 모든 사용 사례에 대해 대량 전송 을 사용하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/328113?quality=12&learn=on&hidetitle=true)

## GigaSign 앱 다운로드 및 설치

[GigaSign Zip 파일 다운로드](https://acrobat.adobe.com/id/urn:aaid:sc:US:001cf62d-1cab-46c7-aa96-661ac8680206)

[Java 1.8 다운로드 링크(필요한 경우에만)](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) {target="_blank"}

[허용 목록에 IP 주소(필요한 경우에만)](https://helpx.adobe.com/kr/sign/system-requirements.html#IPs){target="_blank"}

## 기본 설정 지침

1. Acrobat Sign 계정에 로그인합니다.

1. **[!UICONTROL 그룹]** 또는 **[!UICONTROL 계정]** 중 맨 위에 표시되는 항목을 클릭합니다.

1. 화면 왼쪽의 검색 필드에 &quot;액세스 토큰&quot;을 입력합니다.

1. 오른쪽의 &quot;+&quot; 아이콘을 누릅니다.

1. 필요한 범위(User_Read, Agreement_Read, Agreement_Write, Agreement_Send, Library_Read)가 있는 키를 만듭니다.

1. 만든 키를 두 번 클릭하고 전체 텍스트를 복사합니다(화면 밖으로 오른쪽으로 이동하므로 모두 표시됨).

1. GigaSign을 엽니다.

1. 오른쪽 상단의 **[!UICONTROL 설정]** 아이콘을 클릭합니다.

1. 첫 번째 줄에 통합 키를 붙여넣습니다.

1. 두 번째 줄에 해당 키를 만드는 데 사용되는 계정의 이메일 주소를 입력합니다.

1. **[!UICONTROL 제출]**&#x200B;을 클릭합니다.
