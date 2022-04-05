---
title: Microsoft Dynamics 365 및 Marketo용 Acrobat Sign을 사용하여 알림 보내기
description: 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다.
role: Admin
product: adobe sign
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7249.jpg
exl-id: 2e0de48c-70bf-4dc5-8251-88e7399f588a
source-git-commit: 60582eeaf8437ca1206f45b0b6daf96629c16b61
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Adobe Sign for Microsoft Dynamics 365 및 Marketo을 사용하여 알림 보내기

Adobe Sign, Microsoft Dynamic용 Adobe Sign, Marketo 및 Marketo Microsoft Dynamics Sync를 사용하여 계약이 진행 중임을 서명자에게 알리기 위해 텍스트 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다. Marketo에서 알림을 보내려면 먼저 Marketo SMS 관리 기능을 구매하거나 구성해야 합니다. 이 연습에서는 [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/)하지만 다른 Marketo SMS 솔루션도 사용할 수 있습니다.

## 사전 요구 사항

1. Marketo Microsoft Dynamics Sync를 설치합니다.

   정보 및 Microsoft Dynamics Sync용 최신 플러그인을 사용할 수 있습니다. [여기](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html)

1. Microsoft Dynamics용 Adobe Sign을 설치합니다.

   이 플러그인에 대한 정보를 사용할 수 있습니다. [여기](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html)

## 사용자 정의 개체 찾기

Marketo Microsoft Dynamics Sync 및 Adobe Sign for Dynamics 구성이 완료되면 Marketo 관리 터미널에 두 개의 새로운 옵션이 나타납니다.

![관리자](assets/adminTerminal.png)

* 클릭 **[!UICONTROL Dynamics 엔터티 동기화]**.

   사용자 정의 엔티티를 동기화하려면 먼저 동기화를 비활성화해야 합니다. 클릭 **[!UICONTROL 스키마 동기화]** 처음이시면 그렇지 않으면 **[!UICONTROL 스키마 새로 고침]**.

   ![새로 고침](assets/refreshSchema.png)

## 사용자 정의 개체 동기화

1. 오른쪽에서 [!UICONTROL 리드], [!UICONTROL 연락처]및 [!UICONTROL 계정]- 기반 사용자 정의 개체입니다.

   * **[!UICONTROL 동기화 사용]** 에 추가합니다.

   * **[!UICONTROL 동기화 사용]** 연락처 아래의 개체에 대해 연락처가 Dynamics에서 계약에 추가되었을 때 트리거하도록 하려는 경우

   * **[!UICONTROL 동기화 사용]** 를 클릭합니다.

   * **동기화 사용** 를 클릭하십시오.

   ![사용자 정의 개체](assets/enableSyncDynamics.png)

1. 새 창의 [계약]에서 원하는 속성을 선택합니다.

   아래의 상자를 활성화합니다. **[!UICONTROL 제한]** 및 **[!UICONTROL 트리거]** 를 클릭하여 마케팅 활동에 알립니다.

   ![사용자 지정 동기화 1](assets/entitySync1.png)

   ![사용자 지정 동기화 2](assets/entitySync2.png)

1. 사용자 정의 개체에서 동기화를 활성화한 후 동기화를 다시 활성화합니다.

   다음으로 돌아가기 [!UICONTROL 관리자 터미널]을 클릭하고 **[!UICONTROL Microsoft Dynamics]**&#x200B;을 클릭한 다음 **[!UICONTROL 동기화 사용]**.

   ![Microsoft Dynamics](assets/microsoftDynamics.png)

   ![전역 사용](assets/enableGlobalDynamics.png)

## 프로그램 만들기

1. In [!UICONTROL 마케팅 활동], 마우스 오른쪽 단추 클릭 **[!UICONTROL 마케팅 활동]** 왼쪽 막대에서 **[!UICONTROL 새 캠페인 폴더]**&#x200B;이름을 지정하고 이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 생성된 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새 프로그램]**&#x200B;이름을 지정합니다.

   다른 모든 항목을 기본값으로 두고 **[!UICONTROL 만들기]**.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

## 설정 [!DNL Twilio] SMS

먼저 활성 상태 확인 [!DNL Twilio] 필요한 SMS 기능을 구입했습니다.

Marketo 설정 - [!DNL Twilio] SMS Webhook에는 3개의 [!DNL Twilio] 매개 변수를 반환합니다.

* 계정 SID
* 계정 토큰
* Twilio 전화 번호

계정에서 이러한 매개 변수를 검색하면 Marketo 인스턴스가 열립니다.

1. 클릭 **[!UICONTROL 관리]** 클릭합니다.

   ![관리자](assets/adminTab.png)

1. 클릭 **[!UICONTROL 웹 후크]**&#x200B;을 클릭하고 **[!UICONTROL 새 Webhook]**.

   ![Webhook](assets/webhooks.png)

1. 다음을 입력합니다. **[!UICONTROL Webhook 이름]** 및 **[!UICONTROL 설명]**.

1. 다음 URL을 입력하고 `ACCOUNT_SID` 및 `AUTH_TOKEN` 에 [!DNL Twilio] 자격 증명

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. 선택 **[!UICONTROL POST]** 를 입력합니다.

1. 다음을 입력합니다 **템플릿** 교체 `MY_TWILIO_NUMBER` 에 [!DNL Twilio] 전화번호 `YOUR_MESSAGE` 선택하신 메시지로 보내주십시오.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. 설정 **[!UICONTROL 요청 토큰 인코딩]** 에 *양식/URL*.

1. 응답 유형을 다음으로 설정 *JSON* 그런 다음 **[!UICONTROL 저장]**.

## 스마트 캠페인 트리거 설정

1. 마케팅 활동 섹션에서 생성한 프로그램을 마우스 오른쪽 버튼으로 클릭한 다음 **[!UICONTROL 새로운 스마트 캠페인]**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. 이름을 지정하고 **[!UICONTROL 만들기]**.

   ![Smart Campaign 2](assets/smartCampaign3.png)

   Microsoft 폴더 아래에서 사용할 수 있는 여러 트리거가 표시됩니다.

1. 클릭 후 드래그 **[!UICONTROL 계약에 추가됨]** 에 **[!UICONTROL 스마트 목록]**&#x200B;트리거에 포함할 제약 조건을 추가합니다.

   ![계약에 추가됨](assets/addedToAgreementDynamics.png)

## 스마트 캠페인 흐름 설정

1. 오른쪽 상단의 **[!UICONTROL 흐름]** 탭 [!UICONTROL Smart Campaign].

   를 검색하고 **Webhook 호출** 캔버스로 이동하고 이전 섹션에서 만든 webhook를 선택합니다.

   ![Webhook 호출](assets/callWebhook.png)

1. 이제 계약에 추가된 리드를 위한 SMS 알림 캠페인이 설정됩니다.
>[!TIP]
>
>이 튜토리얼은 [Microsoft Dynamics 및 Marketo에서 Adobe Sign을 사용하여 세일즈 주기 단축](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) Experience League에서 무료로 사용할 수 있습니다!