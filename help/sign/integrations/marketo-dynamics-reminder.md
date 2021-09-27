---
title: Microsoft Dynamics 365용 Adobe 사인 및 Marketo를 사용하여 미리 알림 보내기
description: 일정 기간 후에 계약이 서명되지 않은 상태로 있을 때 전자 메일 미리 알림을 보내는 방법 알아보기
role: Admin
product: adobe sign
solution: Adobe Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7250.jpg
exl-id: 5a97fade-18a3-448a-8504-efb9e38e9187
source-git-commit: bcddb0ee106239f2786debaed908b2a2ec5ce792
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 2%

---

# Microsoft Dynamics 365용 Adobe 사인 및 Marketo를 사용하여 미리 알림 보내기

일정 기간 후에 계약이 서명되지 않은 상태로 있을 때 전자 메일 미리 알림을 보내는 방법을 알아봅니다. 이 통합에서는 Adobe Sign, Adobe Sign for Microsoft Dynamics, Marketo 및 Marketo Microsoft Dynamics Sync를 사용합니다.

## 사전 요구 사항

1. Marketo Microsoft Dynamics Sync를 설치합니다.

   Microsoft Dynamics Sync용 정보 및 최신 플러그 인은 여기에서 [사용할 수 있습니다.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html)

1. [Microsoft Dynamics](https://appsource.microsoft.com/ko-KR/product/dynamics-365/adobesign.f3b856fc-a427-4d47-ad4b-d5d1baba6f86)용 Adobe Sign을 설치합니다.

   이 플러그 인에 대한 정보는 여기에서 [사용할 수 있습니다.](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html)

## 사용자 지정 개체 찾기

Marketo Microsoft Dynamics Sync 및 Adobe Sign for Dynamics 구성이 완료되면 Marketo 관리 터미널에 두 개의 새 옵션이 나타납니다.

![관리자](assets/adminTerminal.png)

1. **[!UICONTROL Dynamics 엔터티 동기화]**&#x200B;를 클릭합니다.

   사용자 지정 엔터티를 동기화하려면 먼저 동기화를 사용하지 않도록 설정해야 합니다. 처음 사용하는 경우 **동기화 스키마**&#x200B;를 클릭합니다. 그렇지 않으면 **스키마 새로 고침**&#x200B;을 클릭합니다.

   ![새로 고침](assets/refreshSchema.png)

## 사용자 지정 개체 동기화

1. 오른쪽에서 [!UICONTROL Lead], [!UICONTROL Contact] 및 [!UICONTROL Account] 기반 사용자 지정 개체를 찾습니다.

   * **Dynamics** 에서  **** 리더가 계약에 서명하지 않은 경우 미리 알림을 보낼   Leadif 아래의 개체에 대해 동기화를 활성화합니다.

   * **Contactif** 에서 Contacthas가  **** Dynamics에서 계약에 서명하지 않은 경우 미리 알림을 보낼   개체에 대해 동기화를 활성화합니다.

   * **Dynamics에서** Accounthas가 계약에  **** 서명하지 않은 경우 미리 알림을 보낼 Accountif 아래의   개체에 대해 동기화를 활성화합니다.

   * **원하는** 상위( **[!UICONTROL Lead, Contact]**  또는 Account[!UICONTROL ) 아래의 계약] 객체에 대해 Syncc를  [!UICONTROL 활성화합니다] .

   ![사용자 정의 개체](assets/enableSyncDynamics.png)

1. 새 창에서 계약에서 원하는 속성을 선택한 다음 **제약 조건** 및 **트리거**&#x200B;에서 상자를 활성화하여 마케팅 활동에 표시합니다.

   ![사용자 지정 동기화 1](assets/entitySync1.png)

   ![사용자 지정 동기화 2](assets/entitySync2.png)

1. 사용자 지정 개체에서 동기화를 사용하도록 설정한 후 동기화를 다시 활성화합니다.

   관리 터미널로 돌아가서 **Microsoft Dynamics**&#x200B;를 클릭한 다음 **동기화 사용**&#x200B;을 클릭합니다.

   ![Microsoft Dynamics](assets/microsoftDynamics.png)

   ![전역 사용](assets/enableGlobalDynamics.png)

## 프로그램 및 토큰 만들기

1. Marketo의 Marketo Activities 섹션에서 왼쪽 막대의 **Marketing Activities**&#x200B;를 마우스 오른쪽 단추로 클릭합니다.

   **새 캠페인 폴더**&#x200B;를 선택하고 이름을 지정하십시오.

   ![새 폴더](assets/newFolder.png)

1. 만든 폴더를 마우스 오른쪽 단추로 클릭하고 **새 프로그램**&#x200B;을 선택한 다음 이름을 지정합니다.

   다른 모든 항목을 기본값으로 두고 **만들기**&#x200B;를 클릭합니다.

   ![새 프로그램 1](assets/newProgram1.png)

   ![새 프로그램 2](assets/newProgram2.png)

1. **내 토큰**&#x200B;을 클릭한 다음 **전자 메일 스크립트**&#x200B;를 캔버스로 끕니다.

   ![전자 메일 스크립트](assets/emailScript.png)

1. 이름을 지정한 다음 **을 클릭하여**&#x200B;을 편집합니다.

   ![이름 및 편집](assets/nameAndSave.png)

1. 오른쪽에서 **[!UICONTROL 사용자 지정 개체]**&#x200B;를 확장한 다음 **[!UICONTROL 계약]** 개체를 확장합니다.

   [!UICONTROL 이름], 계약 상태, 보낸 사람 및 현재 서명자 URL을 찾아서 캔버스로 끌어 옵니다.

1. 이 토큰을 사용하여 Velocity 스크립트를 작성하여 일주일 동안 서명되지 않은 계약의 계약 URL을 표시합니다. 다음은 현재 날짜를 보낸 날짜와 비교하는 예제입니다.

   ```
   #foreach($agreement in $adobe_agreementList)
       #if($agreement.adobe_esagreementstatus == "Out for Signature")
           #set($todayCalObj = $date.toCalendar($date.toDate("yyyy-MM-dd",$date.get('yyyy-MM-dd'))) )
           #set($dateSentCalObj = $date.toCalendar($date.toDate("yyyy-MM-dd",$agreement.adobe_datesent)) )
           #set($dateDiff = ($todayCalObj.getTimeInMillis() - $dateSentCalObj.getTimeInMillis()) / 86400000 )
   
           #if($dateDiff >= 7)
               #set($agreementName = $agreement.adobe_name)
               #set($agreementURL = $agreement.adobe_currentsignerurl.substring(8))
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

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 미리 알림 만들기 및 개인 설정 추가

개인 설정의 예는 다음과 같습니다. 서명자 이름, 계약명, 계약에 대한 링크 등

1. 만든 프로그램을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새 로컬 자산]**&#x200B;을 클릭한 다음 **[!UICONTROL 전자 메일]**&#x200B;을 선택합니다.

   ![새 전자 메일](assets/createNewEmail.png)

1. 새 탭에서 전자 메일의 **[!UICONTROL Name]** 및 **[!UICONTROL Description]**&#x200B;을 입력하고 템플릿 선택기에서 템플릿을 선택합니다.

   ![템플릿 선택](assets/templatePicker.png)

1. **[!UICONTROL [만들기]]**&#x200B;를 클릭합니다.

1. **[!UICONTROL From Name]** 및 **[!UICONTROL From Address]**&#x200B;를 설정합니다.

   ![미리 알림 전자 메일](assets/reminderEmail.png)

1. 편집기를 활성화하려면 메시지 본문을 클릭합니다.

   **[!UICONTROL 토큰 삽입]** 단추를 클릭하고 만든 사용자 지정 계약 URL 토큰을 찾은 다음 **[!UICONTROL 삽입]**&#x200B;을 클릭합니다. 전자 메일 사용자 지정을 완료하고 **[!UICONTROL Save]**&#x200B;를 클릭합니다.

   ![토큰 삽입](assets/insertToken.png)

1. 계약이 할당된 프로파일을 사용하여 미리 봅니다.

   계약 이름이 레이블로 표시된 URL에 대한 링크가 표시됩니다.

   ![전자 메일 링크](assets/emailLink.png)

## 스마트 캠페인 필터 설정

1. 만든 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL 새 스마트 캠페인]**&#x200B;을 클릭합니다.

   ![스마트 캠페인 1](assets/smartCampaign1.png)

1. 선택한 이름을 지정한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![스마트 캠페인 2](assets/smartCampaign2.png)

1. 을 검색한 다음 **[!UICONTROL 계약 있음]**&#x200B;을(를) 클릭하여 스마트 목록으로 끕니다.

   ![계약 있음](assets/hasAgreementDynamics1.png)

   트리거에 노출된 필드는 **[!UICONTROL 제약 조건 추가]**&#x200B;에서 사용할 수 있어야 합니다.

1. **[!UICONTROL 계약 상태]** 및 필터링할 기타 필드를 선택합니다.

   추가된 각 필드에 대해 필터링할 값을 정의합니다. 이 경우에는 **[!UICONTROL Agreement Status]** Out for Signature *이고&#x200B;**[!UICONTROL Sent On]**이(가) 1주 전에*&#x200B;인 경우에만 트리거됩니다.**

   ![계약 상태](assets/hasAgreementDynaSentOn.png)

   >[!NOTE]
   >
   > 이 캠페인을 특정 계약에 대해서만 실행하려면 **Name**&#x200B;과(와) 같은 제약 조건에 고유 식별자를 추가합니다.

1. 캠페인 대상을 확인하고 일정 탭에서 자격을 얻을 대상을 확인합니다.

   ![구분자](assets/qualifiers.png)

## 스마트 캠페인 플로우 설정

캠페인 필터 **만료까지 일**&#x200B;이 사용되었으므로 캠페인에 예약된 되풀이를 사용할 수 있습니다.

1. [!UICONTROL Smart Campaign]에서 **[!UICONTROL Flow]** 탭을 클릭합니다.

   **전자 메일 보내기** 흐름을 캔버스로 끌어서 이전 섹션에서 만든 미리 알림 전자 메일을 선택합니다.

   ![전자 메일 보내기](assets/sendEmail.png)

1. 스마트 캠페인에서 **[!UICONTROL 일정]** 탭을 클릭합니다. 캠페인 흐름이 **Smart Campaign Settings**&#x200B;에서 한 사람당 한 번만 실행되도록 제한되는지 확인하십시오. 그런 다음 **되풀이 일정 잡기** 탭을 클릭합니다.

   ![스케줄 탭](assets/scheduleTab.png)

1. **Schedule**&#x200B;을 _Daily_&#x200B;로 설정합니다. 필요한 경우 캠페인의 시작 날짜 및 시간 및 종료 날짜를 선택합니다.

   ![일정 설정](assets/scheduleSettings.png)

>[!TIP]
>
>이 자습서는 Adobe Sign for Microsoft Dynamics 및 Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) Adobe Sign for Microsoft Dynamics를 사용하여 영업 주기를 단축시키는 과정의 일부로, Experience League에서 무료로 사용할 수 있습니다.[