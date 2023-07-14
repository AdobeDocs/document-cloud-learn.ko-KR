---
title: Salesforce용 Acrobat Sign 및 Marketo 구성 가이드를 사용하여 알림 메시지 전송
description: 일정 기간 후 계약에 서명이 없는 경우 Marketo에서 전자 메일 미리 알림을 보내는 방법을 알아봅니다.
role: Admin
product: adobe sign
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
jira: KT-7248
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: 33aca2e0-2f27-4100-a16f-85ba652c17a3
source-git-commit: aa8fd589d214879f2bfcb6bc54576c707532fd6f
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 1%

---

# Salesforce용 Acrobat Sign 및 Marketo 구성 가이드를 사용하여 알림 메시지 전송

일정 기간 후 계약에 서명이 없는 경우 Marketo에서 이메일 알림 메시지를 보내는 방법에 대해 알아봅니다. 이 통합에서는 Acrobat Sign, Salesforce용 Acrobat Sign, Marketo 및 Marketo 및 Salesforce 동기화를 사용합니다.

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

**동기화 사용** 를 클릭합니다.

**동기화 사용** (연락처 아래에 있는 개체에 대해) 연락처가 Salesforce에서 계약에 서명하지 않았을 때 미리 알림을 보내려는 경우.

**동기화 사용** (계정 아래의 개체에 대해) 계정이 Salesforce에서 계약에 서명하지 않은 경우 미리 알림을 보내려는 경우.

1. **동기화 사용** 의 경우 **계약** 개체가 원하는 상위(잠재 고객, 연락처 또는 계정) 아래에 표시됩니다. 동기화하려는 다른 사용자 정의 개체에 대해 이 작업을 수행합니다.

   ![계약 개체](assets/agreementObject.png)

1. 다음 에셋은 다음을 수행하는 방법을 보여 줍니다 **동기화 사용**.

   ![사용자 지정 동기화 1](assets/customObjectSync1.png)

   ![사용자 지정 동기화 2](assets/customObjectSync2.png)

## 트리거에 사용자 정의 개체 필드 노출

1. 전역 동기화가 비활성화된 상태에서 동기화를 활성화한 계약 사용자 정의 개체를 선택한 다음 **표시되는 필드 편집**.

1. 트리거 열에서 &quot;계약 이름&quot; 필드를 선택하여 Campaign Action 트리거에 표시합니다. 필터링할 다른 필드를 선택한 다음 **저장**.

   ![표시되는 필드 편집 1](assets/editVisible1.png)

   ![표시 가능한 필드 편집 2](assets/editVisible2.png)

1. 사용자 정의 개체에 대한 동기화 활성화 및 트리거 값 노출을 마쳤으면 동기화를 다시 활성화해야 합니다.

   ![전역 사용](assets/enableGlobal.png)

## 프로그램 및 토큰 만들기

1. Marketo의 마케팅 활동 섹션에서 마우스 오른쪽 버튼을 클릭합니다 **마케팅 활동** 왼쪽 막대에서 **새 캠페인 폴더**&#x200B;이름을 지정합니다.

   ![새 폴더](assets/newFolder.png)

1. 생성된 폴더를 마우스 오른쪽 단추로 클릭하고 **새 프로그램**&#x200B;이름을 지정합니다. 다른 모든 항목을 기본값으로 두고 **만들기**.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

1. 다음을 클릭합니다. **내 토큰**, 드래그  **전자 메일 스크립트** 캔버스로 이동합니다.

   ![전자 메일 스크립트](assets/emailScript.png)

1. 이름을 지정한 다음 **클릭하여 편집**.

   ![이름 및 편집](assets/nameAndSave.png)

1. 확장 **사용자 정의 개체** 을 선택한 다음 **계약** 있습니다. 계약 이름, 계약 상태, 서명된 날짜 및 서명 URL을 찾아 캔버스로 드래그합니다.

1. 이러한 토큰을 사용하여 Velocity 스크립트를 작성하면 일주일 동안 서명되지 않은 계약의 계약 URL이 표시됩니다. 다음은 현재 날짜와 보낸 날짜를 비교하는 예입니다.

   ```
   #foreach($agreement in $echosign_dev1__SIGN_Agreement__cList)
       #if($agreement.echosign_dev1__Status__c == "Out for Signature")
           #set($todayCalObj = $date.toCalendar($date.toDate("yyyy-MM-dd",$date.get('yyyy-MM-dd'))) )
           #set($dateSentCalObj = $date.toCalendar($date.toDate("yyyy-MM-dd",$agreement.echosign_dev1__DateSent__c)) )
           #set($dateDiff = ($todayCalObj.getTimeInMillis() - $dateSentCalObj.getTimeInMillis()) / 86400000 )
   
           #if($dateDiff >= 7)
               #set($agreementName = $agreement.Name)
               #set($agreementURL = $agreement.echosign_dev1__Signing_URL__c.substring(8))
               #break
           #else
           #end
       #else
       #end
   #end
   
   #if(${agreementName})
       <a href="https://${agreementURL}">${agreementName}</a>
   #else
       Please contact us. 
   #end
   ```

1. **저장**&#x200B;을 클릭합니다.

## 알림 메시지 생성 및 개인화 추가

개인화의 예는 다음과 같습니다. 서명자 이름, 계약 이름, 계약 링크 등

1. 만든 프로그램을 마우스 오른쪽 단추로 클릭하고 **새 로컬 에셋**&#x200B;을 선택한 다음 **이메일**.

   ![새 전자 메일](assets/createNewEmail.png)

1. 새 탭에서 **이름** 및 **설명** 을 선택하고 템플릿 선택기에서 템플릿을 선택합니다. **만들기**&#x200B;를 클릭합니다.

   ![템플릿 선택기](assets/templatePicker.png)

1. 설정 **보낸 사람 이름** 및 **보낸 사람 주소**.

   ![미리 알림 이메일](assets/reminderEmail.png)

1. 메시지 본문을 클릭하여 편집기를 활성화합니다. 오른쪽 상단의 **토큰 삽입** 단추를 클릭하고 작성한 사용자 정의 계약 URL 토큰을 찾은 다음 을 클릭합니다. **삽입**. 전자 메일 사용자 정의를 완료한 다음 **저장**.

   ![토큰 삽입](assets/insertToken.png)

1. 계약이 할당된 프로파일을 사용하여 미리 봅니다. 계약 이름이 레이블인 URL에 대한 링크가 표시됩니다.

   ![전자 메일 링크](assets/emailLink.png)

## 스마트 캠페인 필터 설정

1. 만든 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **새로운 스마트 캠페인**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. 선택한 이름을 지정한 다음 을 클릭합니다. **만들기**.

   ![Smart Campaign 2](assets/smartCampaign2.png)

1. 검색한 다음 클릭하고 드래그 **계약 있음** 스마트 목록에 추가합니다.

   ![계약 있음](assets/hasAgreement.png)

1. 이제 트리거에 노출된 필드를 **제약 조건 추가**. 선택 **계약 상태** 및 필터링할 기타 필드. 추가된 각 필드에 대해 필터링할 값을 정의합니다. 이 경우 트리거는 **계약 상태** 서명을 위해 전송됨 및 **보낸 날짜** 7일 이전입니다.

   ![계약 상태](assets/agreementStatus.png)

   >[!NOTE]
   >
   > 제약 조건에 대한 고유 식별자 **계약 이름**&#x200B;특정 계약에 대해서만 이 캠페인을 실행하도록 하려면 다음을 수행하십시오.

1. [일정] 탭에서 캠페인 대상자를 확인하고 자격이 되는 사람을 확인합니다.

   ![한정자](assets/qualifiers.png)

## 스마트 캠페인 흐름 설정

캠페인 필터 **서명되지 않은 일 수** 이(가) 사용되었으므로 캠페인에 예약된 되풀이를 사용할 수 있습니다.

1. 오른쪽 상단의 **흐름** 탭을 클릭합니다. 를 검색하고 **전자 메일 보내기** 캔버스로 이동하고 이전 섹션에서 생성한 알림 전자 메일을 선택합니다.

   ![전자 메일 보내기](assets/sendEmail.png)

1. 오른쪽 상단의 **일정** 탭을 클릭합니다. 캠페인 흐름이 **Smart Campaign 설정**. 그런 다음 **되풀이 예약** 탭합니다.

   ![일정 탭](assets/scheduleTab.png)

1. 설정 **일정** 일별로 설정하려면 캠페인의 시작 일자 및 시간과 종료 일자를 선택합니다(필요한 경우).

   ![일정 설정](assets/scheduleSettings.png)

>[!TIP]
>
>이 튜토리얼은 [Salesforce용 Acrobat Sign 및 Marketo을 통해 세일즈 주기 단축](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) Experience League에서 무료로 사용할 수 있습니다!
