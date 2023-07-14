---
title: Salesforce용 Acrobat Sign 및 Marketo을 사용하여 알림 보내기
description: 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다.
role: Admin
product: adobe sign
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
jira: KT-7247
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: ac3334ec-b65f-4ce4-b323-884948f5e0a6
source-git-commit: aa8fd589d214879f2bfcb6bc54576c707532fd6f
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 1%

---

# Acrobat Sign을 사용하여 알림 보내기 [!DNL Salesforce] 및 [!DNL Marketo]

Acrobat Sign, Salesforce용 Acrobat Sign, Marketo 및 Marketo Salesforce 동기화를 사용하여 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다. Marketo에서 알림을 보내려면 먼저 Marketo SMS 관리 기능을 구매하거나 구성해야 합니다. 이 연습에서는 [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/)하지만 다른 Marketo SMS 솔루션도 사용할 수 있습니다.

## 사전 요구 사항

1. Marketo Salesforce 동기화를 설치합니다.

   정보 및 Salesforce용 최신 플러그인을 사용할 수 있습니다. [여기](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html)

1. Salesforce용 Acrobat Sign 설치.

   이 플러그인에 대한 정보를 사용할 수 있습니다. [여기](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html)

## 사용자 정의 개체 찾기

Marketo Salesforce 동기화 및 Salesforce용 Acrobat Sign 구성이 완료되면 몇 가지 새로운 옵션이 Marketo 관리 터미널에 나타납니다.

![관리](assets/adminTab.png)

![개체 동기화](assets/salesforceAdmin.png)

1. 클릭 **스키마 동기화** 처음이시면 그렇지 않으면 **스키마 새로 고침**.

   ![새로 고침](assets/refreshSchema1.png)

1. 전역 동기화가 실행 중인 경우 **전역 동기화 사용 안 함**.

   ![비활성화](assets/disableGlobal.png)

1. 클릭 **스키마 새로 고침**.

   ![새로 고침 2](assets/refreshSchema2.png)

## 사용자 정의 개체 동기화

오른쪽의 리드, 연락처 및 계정 기반 사용자 정의 개체를 참조하십시오.

**동기화 사용** 에 추가합니다.

**동기화 사용** 연락처 아래에 있는 개체에 대해 연락처가 Salesforce에서 계약에 추가되었을 때 트리거하도록 하려는 경우

**동기화 사용** 를 클릭합니다.

1. **동기화 사용** 을 선택합니다.

   ![사용자 정의 개체](assets/customObjects.png)

1. 다음 에셋은 다음을 수행하는 방법을 보여 줍니다 **동기화 사용**.

   ![사용자 지정 동기화 1](assets/customObjectSync1.png)

   ![사용자 지정 동기화 2](assets/customObjectSync2.png)

1. 사용자 정의 개체에서 동기화 활성화를 마치면 동기화를 다시 활성화합니다.

   ![전역 사용](assets/enableGlobal.png)

## 프로그램 만들기

1. Marketo의 마케팅 활동 섹션에서 마우스 오른쪽 버튼을 클릭합니다 **마케팅 활동** 왼쪽 막대에서 **새 캠페인 폴더**&#x200B;이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 생성된 폴더를 마우스 오른쪽 단추로 클릭하고 **새 프로그램**&#x200B;이름을 지정합니다. 다른 모든 항목을 기본값으로 두고 **만들기**.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

## Twilio SMS 설정

먼저 Twilio 계정이 활성화되어 있고 필요한 SMS 기능을 구입했는지 확인합니다.

Marketo 설정 - Twilio SMS Webhook을 사용하려면 계정에서 세 개의 Twilio 매개 변수가 필요합니다.

- 계정 SID
- 계정 토큰
- Twilio 전화 번호

계정에서 이러한 매개 변수를 검색하면 Marketo 인스턴스가 열립니다.

1. 다음을 클릭합니다. **관리** 클릭합니다.

   ![관리](assets/adminTab.png)

1. 다음을 클릭합니다. **웹 후크**, **새 Webhook**.

   ![Webhook](assets/webhooks.png)

1. 다음을 입력합니다. **Webhook 이름** 및 **설명**.

1. 다음 URL을 입력하고 **[ACCOUNT_SID]** 및 **[AUTH_TOKEN]** 사용할 수 있습니다.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. 선택 **POST** 를 입력합니다.

1. 다음을 입력합니다 **템플릿** 교체 **[MY_TWILIO_NUMBER]** 사용할 수 있습니다. **[YOUR_MESSAGE]** 선택하신 메시지로 보내주십시오.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. 요청 토큰 인코딩을 양식/URL로 설정합니다.

1. 응답 유형을 JSON으로 설정한 다음 **저장**.

## 스마트 캠페인 트리거 설정

1. 마케팅 활동 섹션에서 생성한 프로그램을 마우스 오른쪽 버튼으로 클릭한 다음 **새로운 스마트 캠페인**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. 이름을 지정하고 **만들기**.

   ![Smart Campaign 2](assets/smartCampaign3.png)

   사용자 정의 개체 동기화에 대한 구성이 올바르게 수행된 경우, Salesforce 폴더 아래에서 사용할 수 있는 다음 트리거가 표시되어야 합니다.

1. 계약에 추가됨 을 클릭하여 스마트 목록으로 드래그합니다. 트리거에 지정할 제약 조건을 추가합니다.

   ![계약 2에 추가됨](assets/addedToAgreement2.png)

## 스마트 캠페인 흐름 설정

1. 오른쪽 상단의 **흐름** 탭을 클릭합니다. 를 검색하고 **Webhook 호출** 캔버스로 이동하고 이전 섹션에서 만든 webhook를 선택합니다.

   ![Webhook 호출](assets/callWebhook.png)

1. 이제 계약에 추가된 리드를 위한 SMS 알림 캠페인이 설정됩니다.

>[!TIP]
>
>이 튜토리얼은 [Salesforce용 Acrobat Sign 및 Marketo을 통해 세일즈 주기 단축](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) Experience League에서 무료로 사용할 수 있습니다!