---
title: GigaSign을 사용하여 대용량 문서 수집
description: Gigasign을 사용하면 수천 명의 사용자에게 동시에 서명하기 위해 문서를 보내고 수집하고 추적할 수 있습니다.
role: User, Admin
product: adobe sign
level: Intermediate
topic-revisit: Integrations
thumbnail: 328113.jpg
exl-id: a59eab61-fe61-45c6-8137-f074e1f2b3ed
source-git-commit: 7d82422e442cbbed9420050c30ca70821e9a2cdd
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 4%

---

# GigaSign을 사용하여 대용량 문서 수집

Gigasign을 사용하면 수천 명의 사용자에게 동시에 서명을 위한 문서를 보내고 수집하고 추적할 수 있습니다. 이 제품은 직원 및 고객과의 대량 커뮤니케이션을 위해 설계되었으며 각 대량 발송을 통해 최대 2,500명의 수신자를 지원합니다. GigaSign은 Adobe Sign API를 사용하여 MegaSign과 동일한 기능을 제공하며 여러 서명자, 수신자 그룹, 수신자 역할, 계약 이름, 탄소 복사 등을 지원합니다.

>[!VIDEO](https://video.tv.adobe.com/v/328113?hidetitle=true)

## GigaSign 앱 다운로드 및 설치

[GigaSign Zip 파일 다운로드](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:8975dbca-98d5-4e66-9164-d21163c91c7f)

[Java 1.8 다운로드 링크(필요한 경우에만)](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) {target=&quot;_blank&quot;}

[IP 주소를 흰색으로 표시(필요한 경우에만)](https://helpx.adobe.com/kr/sign/system-requirements.html#IPs){target=&quot;_blank&quot;}

## 기본 설정 지침

1. Adobe Sign 계정에 로그인합니다.

1. **[!UICONTROL 그룹]** 또는 **[!UICONTROL 계정]**&#x200B;을 클릭합니다. 맨 위에 표시되는 것을 클릭합니다.

1. 화면 왼쪽의 검색 필드에 &quot;Access tokens&quot;를 입력합니다.

1. 오른쪽에 있는 &quot;+&quot; 아이콘을 누릅니다.

1. 필요한 범위를 사용하여 키 만들기(User_Read, Agreement_Read, Agreement_Write, Agreement_Send, Library_Read)

1. 만든 키를 두 번 클릭하고 전체 텍스트를 복사합니다. 전체 텍스트는 화면에서 오른쪽으로 이동하므로 모두 가져와 보십시오.

1. GigaSign을 엽니다.

1. 오른쪽 상단에 있는 **[!UICONTROL 설정]** 아이콘을 클릭합니다.

1. 첫 줄에 통합 키를 붙여넣습니다.

1. 두 번째 줄에 해당 키를 만드는 데 사용되는 계정의 전자 메일 주소를 입력하십시오.

1. **[!UICONTROL 제출]**&#x200B;을 클릭합니다.
