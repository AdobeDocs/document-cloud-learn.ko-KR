---
title: Microsoft Dynamics 365 및 Marketo용 Acrobat Sign을 사용하여 알림 보내기
description: 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 이메일 또는 푸시 알림을 보내는 방법에 대해 알아봅니다.
feature: Integrations
role: Admin
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
topic: Integrations
topic-revisit: Integrations
jira: KT-7249
thumbnail: KT-7249.jpg
exl-id: 2e0de48c-70bf-4dc5-8251-88e7399f588a
source-git-commit: 452299b2b786beab9df7a5019da4f3840d9cdec9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---

# Microsoft Dynamics 365 및 Marketo용 Acrobat Sign을 사용하여 알림 보내기

서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법 및 Acrobat Sign, Microsoft용 Acrobat Sign Dynamic, Marketo 및 Marketo Microsoft Dynamics Sync를 사용하여 계약을 전송하는 방법에 대해 알아봅니다. Marketo에서 알림을 보내려면 먼저 Marketo SMS 관리 기능을 구매하거나 구성해야 합니다. 이 연습에서는 [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/)를 사용하지만 다른 Marketo SMS 솔루션을 사용할 수 있습니다.

## 사전 요구 사항

1. Marketo Microsoft Dynamics Sync를 설치합니다.

   Microsoft Dynamics Sync에 대한 정보 및 최신 플러그인은 [여기서 사용할 수 있습니다.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html)

1. Microsoft Dynamics용 Acrobat Sign을 설치합니다.

   이 플러그인에 대한 정보는 [여기](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html)에서 사용할 수 있습니다.

## 사용자 정의 오브젝트 찾기

Marketo Microsoft Dynamics Sync 및 Dynamics용 Acrobat Sign 구성이 완료되면 Marketo 관리 터미널에 두 개의 새로운 옵션이 나타납니다.

![관리자](assets/adminTerminal.png)

* **[!UICONTROL Dynamics 엔터티 동기화]**&#x200B;를 클릭합니다.

  사용자 정의 엔티티를 동기화하기 전에 동기화를 비활성화해야 합니다. 처음 사용하는 경우 **[!UICONTROL 스키마 동기화]**&#x200B;를 클릭하세요. 그렇지 않으면 **[!UICONTROL 스키마 새로 고침]**&#x200B;을 클릭하세요.

  ![새로 고침](assets/refreshSchema.png)

## 사용자 정의 오브젝트 동기화

1. 오른쪽에서 [!UICONTROL 리드], [!UICONTROL 연락처] 및 [!UICONTROL 계정] 기반 사용자 지정 개체를 찾습니다.

   * Dynamics의 계약에 리드가 추가될 때 트리거하려면 리드의 개체에 대해 **[!UICONTROL 동기화 사용]**&#x200B;을 설정하십시오.

   * Dynamics에서 연락처가 계약에 추가될 때 트리거하려면 연락처 아래에 있는 개체에 대해 **[!UICONTROL 동기화 사용]**&#x200B;을 설정하십시오.

   * Dynamics의 계약에 계정이 추가될 때 트리거하려면 계정의 개체에 대해 **[!UICONTROL 동기화 사용]**&#x200B;을 설정하십시오.

   * 원하는 상위(잠재 고객, 연락처 또는 계정) 아래의 계약 개체에 대해 **동기화 사용**&#x200B;합니다.

   ![사용자 지정 개체](assets/enableSyncDynamics.png)

1. 새 창의 계약에서 원하는 속성을 선택합니다.

   **[!UICONTROL 제약 조건]** 및 **[!UICONTROL 트리거]** 아래의 상자를 활성화하여 마케팅 활동에 표시하세요.

   ![사용자 지정 동기화 1](assets/entitySync1.png)

   ![사용자 지정 동기화 2](assets/entitySync2.png)

1. 사용자 정의 개체에서 동기화를 활성화한 후 동기화를 다시 활성화합니다.

   [!UICONTROL 관리자 터미널](으)로 돌아가서 **[!UICONTROL Microsoft Dynamics]**&#x200B;를 클릭한 다음 **[!UICONTROL 동기화 사용]**&#x200B;을 클릭하십시오.

   ![Microsoft Dynamics](assets/microsoftDynamics.png)

   ![전역 사용](assets/enableGlobalDynamics.png)

## 프로그램 만들기

1. [!UICONTROL 마케팅 활동]에서 왼쪽 막대의 **[!UICONTROL 마케팅 활동]**&#x200B;을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새 캠페인 폴더]**&#x200B;를 선택하고 이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 만든 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새 프로그램]**&#x200B;을 선택하고 이름을 지정합니다.

   다른 모든 것을 기본값으로 두고 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

## [!DNL Twilio] SMS 설정

먼저 활성 [!DNL Twilio] 계정이 있고 필요한 SMS 기능을 구매했는지 확인하십시오.

Marketo - [!DNL Twilio] SMS Webhook을 설정하려면 계정에서 세 개의 [!DNL Twilio] 매개 변수가 필요합니다.

* 계정 SID
* 계정 토큰
* Twilio 전화번호

계정에서 이러한 매개 변수를 읽어들인 후, 이제 Marketo 인스턴스를 여십시오.

1. 오른쪽 상단에서 **[!UICONTROL 관리자]**&#x200B;를 클릭합니다.

   ![관리자](assets/adminTab.png)

1. **[!UICONTROL Webhook]**&#x200B;을 클릭한 다음 **[!UICONTROL 새 Webhook]**&#x200B;을 클릭합니다.

   ![Webhook](assets/webhooks.png)

1. **[!UICONTROL Webhook 이름]** 및 **[!UICONTROL 설명]**&#x200B;을 입력하십시오.

1. 다음 URL을 입력하고 `ACCOUNT_SID` 및 `AUTH_TOKEN`을(를) [!DNL Twilio] 자격 증명으로 바꾸십시오.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. **[!UICONTROL POST]**&#x200B;을(를) 요청 유형으로 선택합니다.

1. 다음 **템플릿**&#x200B;을 입력하고 `MY_TWILIO_NUMBER`을(를) [!DNL Twilio] 전화번호와 `YOUR_MESSAGE`을(를) 선택한 메시지로 바꾸십시오.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. **[!UICONTROL 토큰 인코딩 요청]**&#x200B;을 *양식/URL*(으)로 설정합니다.

1. 응답 유형을 *JSON*(으)로 설정한 다음 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 스마트 캠페인 트리거 설정

1. 마케팅 활동 섹션에서 만든 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL 새 스마트 캠페인]**&#x200B;을 선택합니다.

   ![스마트 캠페인 1](assets/smartCampaign1.png)

1. 이름을 지정한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![스마트 캠페인 2](assets/smartCampaign3.png)

   Microsoft 폴더 아래에서 사용할 수 있는 여러 개의 트리거가 표시되어야 합니다.

1. **[!UICONTROL 계약에 추가됨]**&#x200B;을(를) 클릭하여 **[!UICONTROL 스마트 목록]**(으)로 끈 다음 트리거에 지정할 제약 조건을 추가합니다.

   ![계약에 추가됨](assets/addedToAgreementDynamics.png)

## 스마트 캠페인 플로우 설정

1. [!UICONTROL 스마트 캠페인]에서 **[!UICONTROL 흐름]** 탭을 클릭합니다.

   **Call Webhook** 흐름을 검색하여 캔버스로 드래그하고 이전 섹션에서 만든 Webhook을 선택합니다.

   ![Webhook](assets/callWebhook.png) 호출

1. 계약에 추가된 잠재 고객에 대한 SMS 알림 캠페인이 이제 설정되었습니다.
>[!TIP]
>
>이 자습서는 Experience League에서 무료로 사용할 수 있는 [Microsoft Dynamics 및 Marketo용 Acrobat Sign으로 판매 주기 가속화](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) 과정의 일부입니다.