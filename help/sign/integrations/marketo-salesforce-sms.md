---
title: Salesforce 및 Marketo용 Acrobat Sign을 사용하여 알림 보내기
description: 서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 이메일 또는 푸시 알림을 보내는 방법에 대해 알아봅니다.
feature: Integrations
role: Admin
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
jira: KT-7247
topic: Integrations
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: ac3334ec-b65f-4ce4-b323-884948f5e0a6
source-git-commit: 51d1a59999a7132cb6e47351cc39a93d9a38eaeb
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# [!DNL Salesforce] 및 [!DNL Marketo]용 Acrobat Sign을 사용하여 알림 보내기

서명자에게 계약이 진행 중임을 알리기 위해 문자 메시지, 이메일 또는 푸시 알림을 보내 Acrobat Sign, Salesforce용 Acrobat Sign, Marketo 및 Marketo Salesforce Sync를 사용하는 방법에 대해 알아봅니다. Marketo에서 알림을 보내려면 먼저 Marketo SMS 관리 기능을 구매하거나 구성해야 합니다. 이 연습에서는 [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/)를 사용하지만 다른 Marketo SMS 솔루션을 사용할 수 있습니다.

## 사전 요구 사항

1. Marketo Salesforce Sync를 설치합니다.

   Salesforce Sync에 대한 정보 및 최신 플러그인은 [여기](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html?lang=ko)에서 사용할 수 있습니다.

1. Salesforce용 Acrobat Sign을 설치합니다.

   이 플러그인에 대한 정보는 [여기](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html)에서 사용할 수 있습니다.

## 사용자 정의 오브젝트 찾기

Marketo Salesforce 동기화 및 Salesforce용 Acrobat Sign 구성이 완료되면 Marketo 관리 터미널에 몇 가지 새로운 옵션이 나타납니다.

![관리자](assets/adminTab.png)

![개체 동기화](assets/salesforceAdmin.png)

1. 처음 사용하는 경우 **스키마 동기화**&#x200B;를 클릭하세요. 그렇지 않으면 **스키마 새로 고침**&#x200B;을 클릭하세요.

   ![새로 고침](assets/refreshSchema1.png)

1. 전역 동기화가 실행 중인 경우 **전역 동기화 사용 안 함**&#x200B;을 클릭하여 비활성화합니다.

   ![사용 안 함](assets/disableGlobal.png)

1. **스키마 새로 고침**&#x200B;을 클릭합니다.

   ![새로 고침 2](assets/refreshSchema2.png)

## 사용자 정의 오브젝트 동기화

오른쪽에서 리드, 연락처 및 계정 기반 사용자 정의 개체를 참조하십시오.

Salesforce에서 리드가 계약에 추가될 때 트리거하려면 리드의 개체에 대해 **동기화를 활성화**&#x200B;합니다.

Salesforce에서 연락처가 계약에 추가될 때 트리거하려면 연락처 아래에 있는 개체에 대해 **동기화 사용**&#x200B;을 선택하세요.

Salesforce에서 계정이 계약에 추가될 때 트리거하려면 계정의 개체에 대해 **동기화를 활성화**&#x200B;합니다.

1. 원하는 상위 개체(잠재 고객, 연락처 또는 계정)에 표시된 사용자 지정 개체에 대해 **동기화를 사용**&#x200B;합니다.

   ![사용자 지정 개체](assets/customObjects.png)

1. 다음 에셋은 **동기화를 활성화**&#x200B;하는 방법을 보여 줍니다.

   ![사용자 지정 동기화 1](assets/customObjectSync1.png)

   ![사용자 지정 동기화 2](assets/customObjectSync2.png)

1. 사용자 정의 개체에서 동기화 활성화를 마쳤으면 동기화를 다시 활성화합니다.

   ![전역 사용](assets/enableGlobal.png)

## 프로그램 만들기

1. Marketo의 마케팅 활동 섹션에서 왼쪽 막대의 **마케팅 활동**&#x200B;을 마우스 오른쪽 단추로 클릭하고 **새 캠페인 폴더**&#x200B;를 선택하고 이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 만든 폴더를 마우스 오른쪽 단추로 클릭하고 **새 프로그램**&#x200B;을 선택하고 이름을 지정합니다. 다른 모든 것을 기본값으로 두고 **만들기**&#x200B;를 클릭합니다.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

## Twilio SMS 설정

먼저 활성 Twilio 계정이 있고 필요한 SMS 기능을 구매했는지 확인하십시오.

Marketo 설정 - Twilio SMS Webhook에는 계정에서 3개의 Twilio 매개 변수가 필요합니다.

- 계정 SID
- 계정 토큰
- Twilio 전화번호

계정에서 이러한 매개 변수를 읽어들인 후, 이제 Marketo 인스턴스를 여십시오.

1. 오른쪽 상단에서 **관리자**&#x200B;를 클릭합니다.

   ![관리자](assets/adminTab.png)

1. **Webhook**&#x200B;을 클릭한 다음 **새 Webhook**&#x200B;을 클릭합니다.

   ![Webhook](assets/webhooks.png)

1. **Webhook 이름** 및 **설명**&#x200B;을 입력하십시오.

1. 다음 URL을 입력하고 **[ACCOUNT_SID]** 및 **[AUTH_TOKEN]**&#x200B;을(를) Twilio 자격 증명으로 바꾸십시오.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. **POST**&#x200B;을(를) 요청 유형으로 선택합니다.

1. 다음 **템플릿**&#x200B;을 입력하고 **[MY_TWILIO_NUMBER]**&#x200B;을(를) Twilio 전화번호로 바꾸고 **[YOUR_MESSAGE]**&#x200B;를 선택한 메시지로 바꾸십시오.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. 토큰 인코딩 요청 을 양식/URL로 설정합니다.

1. 응답 유형을 JSON으로 설정한 다음 **저장**&#x200B;을 클릭합니다.

## 스마트 캠페인 트리거 설정

1. 마케팅 활동 섹션에서 만든 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **새 스마트 캠페인**&#x200B;을 선택합니다.

   ![스마트 캠페인 1](assets/smartCampaign1.png)

1. 이름을 지정한 다음 **만들기**&#x200B;를 클릭합니다.

   ![스마트 캠페인 2](assets/smartCampaign3.png)

   사용자 정의 개체 동기화 구성이 올바르게 수행되었으면 Salesforce 폴더 아래에서 사용할 수 있는 다음 트리거를 볼 수 있습니다.

1. 계약에 추가됨 을 클릭하여 스마트 목록으로 드래그합니다. 트리거에 지정할 제약 조건을 추가합니다.

   ![계약 2](assets/addedToAgreement2.png)에 추가됨

## 스마트 캠페인 플로우 설정

1. 스마트 캠페인에서 **흐름** 탭을 클릭합니다. **Call Webhook** 흐름을 검색하여 캔버스로 드래그하고 이전 섹션에서 만든 Webhook을 선택합니다.

   ![Webhook](assets/callWebhook.png) 호출

1. 계약에 추가된 잠재 고객에 대한 SMS 알림 캠페인이 이제 설정되었습니다.
