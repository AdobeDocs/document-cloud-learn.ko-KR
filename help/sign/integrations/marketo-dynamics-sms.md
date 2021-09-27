---
title: Microsoft Dynamics 365용 Adobe Sign 및 Marketo를 사용하여 알림 보내기
description: 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다.
role: Admin
product: adobe sign
solution: Adobe Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7249.jpg
exl-id: 2e0de48c-70bf-4dc5-8251-88e7399f588a
source-git-commit: bcddb0ee106239f2786debaed908b2a2ec5ce792
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Microsoft Dynamics 365용 Adobe Sign 및 Marketo를 사용하여 알림 보내기

Adobe Sign, Adobe Sign for Microsoft Dynamic, Marketo 및 Marketo Microsoft Dynamics Sync를 사용하여 계약이 진행 중임을 서명자에게 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다. Marketo에서 알림을 보내려면 먼저 Marketo SMS 관리 기능을 구입하거나 구성해야 합니다. 이 연습에서는 [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/)를 사용하지만 다른 Marketo SMS 솔루션을 사용할 수 있습니다.

## 사전 요구 사항

1. Marketo Microsoft Dynamics Sync를 설치합니다.

   Microsoft Dynamics Sync용 정보 및 최신 플러그 인은 여기에서 [사용할 수 있습니다.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html)

1. Microsoft Dynamics용 Adobe 서명을 설치합니다.

   이 플러그 인에 대한 정보는 여기에서 [사용할 수 있습니다.](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html)

## 사용자 지정 개체 찾기

Marketo Microsoft Dynamics Sync 및 Adobe Sign for Dynamics 구성이 완료되면 Marketo 관리 터미널에 두 개의 새 옵션이 나타납니다.

![관리자](assets/adminTerminal.png)

* **[!UICONTROL Dynamics 엔터티 동기화]**&#x200B;를 클릭합니다.

   사용자 지정 엔터티를 동기화하려면 먼저 동기화를 사용하지 않도록 설정해야 합니다. 처음 사용하는 경우 **[!UICONTROL 동기화 스키마]**&#x200B;를 클릭합니다. 그렇지 않으면 **[!UICONTROL 스키마 새로 고침]**&#x200B;을 클릭합니다.

   ![새로 고침](assets/refreshSchema.png)

## 사용자 지정 개체 동기화

1. 오른쪽에서 [!UICONTROL Lead], [!UICONTROL Contact] 및 [!UICONTROL Account] 기반 사용자 지정 개체를 찾습니다.

   * **[!UICONTROL Dynamics의 계약에 Lead가 추가될 때 트리거하려면 Lead 아래의 객체에 대해 Syncc를 활성화합니다.]** 

   * **[!UICONTROL Dynamics의 계약에 연락처가 추가될 때 트리거하려면 연락처 아래의 개체에 대해 동기화를 활성화합니다.]** 

   * **[!UICONTROL Dynamics의 계약에 계정이 추가될 때 트리거하려면 계정 아래의 개체에 대해 동기화를 활성화합니다.]** 

   * **원하는 상위(Lead, Contact 또는 Account) 아래의 계약 객체에 대해 Syncc를 활성화합니다.** 

   ![사용자 정의 개체](assets/enableSyncDynamics.png)

1. 새 창에서 계약에서 원하는 속성을 선택합니다.

   **[!UICONTROL Constraint]** 및 **[!UICONTROL Trigger]**&#x200B;에서 상자를 사용하여 마케팅 활동에 표시합니다.

   ![사용자 지정 동기화 1](assets/entitySync1.png)

   ![사용자 지정 동기화 2](assets/entitySync2.png)

1. 사용자 지정 개체에서 동기화를 사용하도록 설정한 후 동기화를 다시 활성화합니다.

   [!UICONTROL 관리 터미널]으로 돌아가서 **[!UICONTROL Microsoft Dynamics]**&#x200B;를 클릭한 다음 **[!UICONTROL 동기화 사용]**&#x200B;을 클릭합니다.

   ![Microsoft Dynamics](assets/microsoftDynamics.png)

   ![전역 사용](assets/enableGlobalDynamics.png)

## 프로그램 만들기

1. [!UICONTROL 마케팅 활동]의 왼쪽 막대에서 **[!UICONTROL 마케팅 활동]**&#x200B;을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새 캠페인 폴더]**&#x200B;를 선택한 후 이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 만든 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새 프로그램]**&#x200B;을 선택한 다음 이름을 지정합니다.

   다른 모든 항목을 기본값으로 두고 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

## [!DNL Twilio] SMS 설정

먼저 활성 [!DNL Twilio] 계정이 있고 필요한 SMS 기능을 구매했는지 확인하십시오.

Marketo - [!DNL Twilio] SMS 웹 훅을 설정하려면 계정에서 세 개의 [!DNL Twilio] 매개 변수가 필요합니다.

* 계정 SID
* 계정 토큰
* Twilio 전화 번호

계정에서 이러한 매개 변수를 검색하고 이제 Marketo 인스턴스를 엽니다.

1. 오른쪽 위에서 **[!UICONTROL Admin]**&#x200B;을 클릭합니다.

   ![관리자](assets/adminTab.png)

1. **[!UICONTROL 웹 후크]**&#x200B;를 클릭한 다음 **[!UICONTROL 새 웹 후크]**&#x200B;를 클릭합니다.

   ![Webhook](assets/webhooks.png)

1. **[!UICONTROL Webhook Name]** 및 **[!UICONTROL Description]**&#x200B;을 입력하십시오.

1. 다음 URL을 입력하고 `ACCOUNT_SID` 및 `AUTH_TOKEN`을 [!DNL Twilio] 자격 증명으로 바꾸십시오.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. 요청 유형으로 **[!UICONTROL POST]**&#x200B;를 선택합니다.

1. 다음 **Template**&#x200B;을 입력하고 `MY_TWILIO_NUMBER`를 [!DNL Twilio] 전화 번호로 바꾸고 `YOUR_MESSAGE`를 선택한 메시지로 바꾸십시오.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. **[!UICONTROL Request Token Encoding]**&#x200B;을 *Form/URL*&#x200B;로 설정합니다.

1. 응답 유형을 *JSON*&#x200B;으로 설정한 다음 **[!UICONTROL Save]**&#x200B;를 클릭합니다.

## 스마트 캠페인 트리거 설정

1. 마케팅 활동 섹션에서 생성한 프로그램을 마우스 오른쪽 단추로 누른 다음 **[!UICONTROL 새 스마트 캠페인]**&#x200B;을 선택합니다.

   ![스마트 캠페인 1](assets/smartCampaign1.png)

1. 이름을 지정한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![스마트 캠페인 2](assets/smartCampaign3.png)

   Microsoft 폴더에서 사용할 수 있는 여러 트리거가 표시되어야 합니다.

1. **[!UICONTROL 계약에 추가됨]**&#x200B;을(를) 클릭하여 **[!UICONTROL 스마트 목록]**&#x200B;으로 끌어온 다음 트리거에 사용할 제약 조건을 추가합니다.

   ![계약에 추가](assets/addedToAgreementDynamics.png)

## 스마트 캠페인 플로우 설정

1. [!UICONTROL Smart Campaign]에서 **[!UICONTROL Flow]** 탭을 클릭합니다.

   **Call Webhook** 흐름을 캔버스로 끌어 놓은 다음 이전 섹션에서 만든 웹 후크를 선택합니다.

   ![웹 후크 호출](assets/callWebhook.png)

1. 이제 계약에 추가된 잠재 고객에 대한 SMS 알림 캠페인이 설정되었습니다.
>[!TIP]
>
>이 자습서는 Adobe Sign for Microsoft Dynamics 및 Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) Adobe Sign for Microsoft Dynamics를 사용하여 영업 주기를 단축시키는 과정의 일부로, Experience League에서 무료로 사용할 수 있습니다.[