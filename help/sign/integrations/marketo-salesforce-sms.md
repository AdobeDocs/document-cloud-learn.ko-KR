---
title: Salesforce 및 Marketo용 Adobe 서명을 사용하여 알림 보내기
description: 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다.
role: Admin
product: adobe sign
solution: Adobe Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: ac3334ec-b65f-4ce4-b323-884948f5e0a6
source-git-commit: bc79bbde966c99bdf32231ff073b49cfc759d928
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Salesforce 및 Marketo용 Adobe 서명을 사용하여 알림 보내기

Adobe Sign, Adobe Sign for Salesforce, Marketo 및 Marketo Salesforce Sync를 사용하여 계약이 진행 중임을 서명자에게 알리기 위해 문자 메시지, 전자 메일 또는 푸시 알림을 보내는 방법을 알아봅니다. Marketo에서 알림을 보내려면 먼저 Marketo SMS 관리 기능을 구입하거나 구성해야 합니다. 이 연습에서는 [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/)를 사용하지만 다른 Marketo SMS 솔루션을 사용할 수 있습니다.

## 사전 요구 사항

1. Marketo Salesforce 동기화를 설치합니다.

   Salesforce Sync에 대한 정보 및 최신 플러그 인은 여기에서 [사용할 수 있습니다.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html)

1. Salesforce용 Adobe Sign을 설치합니다.

   이 플러그 인에 대한 정보는 여기에서 [사용할 수 있습니다.](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html)

## 사용자 지정 개체 찾기

Marketo Salesforce Sync 및 Adobe Sign for Salesforce 구성이 완료되면 Marketo 관리 터미널에 몇 가지 새로운 옵션이 나타납니다.

![관리자](assets/adminTab.png)

![개체 동기화](assets/salesforceAdmin.png)

1. 처음 사용하는 경우 **동기화 스키마**&#x200B;를 클릭합니다. 그렇지 않으면 **스키마 새로 고침**&#x200B;을 클릭합니다.

   ![새로 고침](assets/refreshSchema1.png)

1. 전역 동기화가 실행 중인 경우 **전역 동기화 사용 안 함** 을 클릭하여 사용 안함으로 설정합니다.

   ![비활성화](assets/disableGlobal.png)

1. **스키마 새로 고침**&#x200B;을 클릭합니다.

   ![새로 고침 2](assets/refreshSchema2.png)

## 사용자 지정 개체 동기화

오른쪽에 있는 Lead, Contact 및 Account 기반 사용자 정의 객체를 참조하십시오.

**Salesforce의 계약에 Lead가 추가될 때 트리거하려면 Lead 아래의 객체에 대해 Syncc를 활성화합니다.** 

**Salesforce** 의 계약에 연락처가 추가될 때 트리거하려면 연락처 아래의 객체에 대해 동기화를 활성화합니다.

**Salesforce에서** 계정이 계약에 추가될 때 트리거하려면 계정 아래의 개체에 대해 동기화를 사용합니다.

1. **원하는** 상위(Lead, Contact 또는 Account) 아래에 표시된 사용자 정의 객체에 대해 Syncc를 활성화합니다.

   ![사용자 정의 개체](assets/customObjects.png)

1. 다음 에셋에서는 **Sync**&#x200B;를 사용하는 방법을 보여 줍니다.

   ![사용자 지정 동기화 1](assets/customObjectSync1.png)

   ![사용자 지정 동기화 2](assets/customObjectSync2.png)

1. 사용자 지정 개체에서 동기화 활성화가 완료되면 동기화를 다시 활성화합니다.

   ![전역 사용](assets/enableGlobal.png)

## 프로그램 만들기

1. Marketo의 마케팅 활동 섹션에서 왼쪽 막대의 **마케팅 활동**&#x200B;을 마우스 오른쪽 단추로 클릭하고 **새 캠페인 폴더**&#x200B;를 선택한 후 이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 만든 폴더를 마우스 오른쪽 단추로 클릭하고 **새 프로그램**&#x200B;을 선택한 다음 이름을 지정합니다. 다른 모든 항목을 기본값으로 두고 **만들기**&#x200B;를 클릭합니다.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

## Twilio SMS 설정

먼저 활성 Twilio 계정이 있는지 확인하고 필요한 SMS 기능을 구매하십시오.

Marketo - Twilio SMS 웹 훅을 설정하려면 계정에서 세 개의 Twilio 매개 변수가 필요합니다.

- 계정 SID
- 계정 토큰
- Twilio 전화 번호

계정에서 이러한 매개 변수를 검색하여 이제 Marketo 인스턴스를 엽니다.

1. 오른쪽 위에서 **Admin**&#x200B;을 클릭합니다.

   ![관리자](assets/adminTab.png)

1. **Webhook**, **New Webhook**&#x200B;을 차례로 클릭합니다.

   ![Webhook](assets/webhooks.png)

1. **Webhook Name** 및 **Description**&#x200B;을 입력하십시오.

1. 다음 URL을 입력하고 **[ACCOUNT_SID]** 및 **[AUTH_TOKEN]**&#x200B;을 Twilio 자격 증명으로 바꾸십시오.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. 요청 유형으로 **POST**&#x200B;를 선택합니다.

1. 다음 **Template**&#x200B;을 입력하고 **[MY_TWILIO_NUMBER]**&#x200B;을(를) Twilio 전화 번호로 바꾸고 **[YOUR_MESSAGE]**&#x200B;를 선택한 메시지로 바꾸십시오.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. 요청 토큰 인코딩을 양식/URL로 설정합니다.

1. 응답 유형을 JSON으로 설정한 다음 **Save**&#x200B;를 클릭합니다.

## 스마트 캠페인 트리거 설정

1. 마케팅 활동 섹션에서 생성한 프로그램을 마우스 오른쪽 단추로 누른 다음 **새 스마트 캠페인**&#x200B;을 선택합니다.

   ![스마트 캠페인 1](assets/smartCampaign1.png)

1. 이름을 지정한 다음 **만들기**&#x200B;를 클릭합니다.

   ![스마트 캠페인 2](assets/smartCampaign3.png)

   사용자 지정 개체 동기화에 대한 구성이 올바르게 수행된 경우 Salesforce 폴더에서 사용할 수 있는 다음 트리거가 표시됩니다.

1. 계약에 추가됨을 누르고 스마트 목록으로 드래그합니다. 트리거에 포함할 제약 조건을 추가합니다.

   ![계약 2에 추가](assets/addedToAgreement2.png)

## 스마트 캠페인 플로우 설정

1. 스마트 캠페인에서 **흐름** 탭을 클릭합니다. **Call Webhook** 흐름을 캔버스로 끌어 놓은 다음 이전 섹션에서 만든 웹 후크를 선택합니다.

   ![웹 후크 호출](assets/callWebhook.png)

1. 이제 계약에 추가된 잠재 고객에 대한 SMS 알림 캠페인이 설정되었습니다.

>[!TIP]
>
>이 자습서는 [Adobe Sign for Salesforce 및 Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) Experience League에서 무료로 제공되는 영업 주기를 단축합니다.