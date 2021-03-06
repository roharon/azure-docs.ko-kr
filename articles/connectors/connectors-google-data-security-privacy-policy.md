---
title: Google 커넥터에 대 한 데이터 보안 및 개인 정보 취급 방침
description: 'Google 보안 및 개인 정보 취급 방침이 Google 커넥터 (예: Gmail)에 미치는 영향에 대해 자세히 알아보세요 Azure Logic Apps'
services: logic-apps
ms.suite: integration
ms.reviewer: divswa, logicappspm
ms.topic: conceptual
ms.date: 06/05/2020
ms.openlocfilehash: 2a5204be638f108b40e431b148c9cb97788c4a52
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91400760"
---
# <a name="data-security-and-privacy-policies-for-google-connectors-in-azure-logic-apps"></a>Azure Logic Apps의 Google 커넥터에 대 한 데이터 보안 및 개인 정보 취급 방침

2020 년 5 **월 1**일부 터 Google의 [데이터 보안 및 개인 정보 취급 방침](https://www.blog.google/technology/safety-security/project-strobe/) 으로 인 한 변경 내용은 [Gmail 커넥터](/connectors/gmail/)를 사용 하는 논리 앱 워크플로에 영향을 줄 수 있습니다. 논리 앱에서 Gmail 소비자 계정 (또는로 끝나는 전자 메일 주소)과 함께 Gmail 커넥터를 사용 하는 경우 @gmail.com @googlemail.com 논리 앱은 특정 [Google 승인 된 트리거, 작업 및 커넥터만](#approved-connectors)사용할 수 있습니다.

> [!NOTE]
> 논리 앱에서 G 제품군 비즈니스 계정 (사용자 지정 도메인이 있는 전자 메일 주소)과 함께 Gmail 커넥터를 사용 하는 경우 논리 앱은 영향을 받지 않으며 Gmail 커넥터 사용에 대 한 제한이 없습니다.

## <a name="affected-logic-apps"></a>영향을 받는 논리 앱

Gmail 커넥터를 사용 하는 논리 앱이 있는 경우 잠재적으로 영향을 받는 논리 앱에 대 한 전자 메일을 받게 됩니다. 그러나 **2020 년 6 월 15**일부 터 비준수 워크플로는 사용 하지 않도록 설정 됩니다. 다음 작업 중 하나를 수행할 수 있습니다.

* [이 항목의 단계를 수행](#update-affected-workflows)하 여 영향을 받는 논리 앱을 업데이트 합니다. Gmail 트리거 또는 작업에서 인증에 사용 하는 클라이언트 ID 및 클라이언트 암호를 제공 하는 Google 클라이언트 앱을 만들어야 합니다.

* 사용 하지 않도록 설정 된 논리 앱을 다시 사용 하도록 설정 하기 전에 [Google 승인 커넥터도](#approved-connectors) 사용 하도록 영향을 받는 논리 앱을 업데이트 합니다.

<a name="approved-connectors"></a>

## <a name="google-approved-connectors"></a>Google 승인 커넥터

이 정책에서 Gmail 소비자 계정을 사용할 때 변경 될 수 있는 특정 Google 승인 서비스만 포함 된 Gmail 커넥터를 사용할 수 있습니다. Microsoft 엔지니어링 팀은 Google 작업을 계속 하 여이 목록에 더 많은 서비스를 추가 합니다. 이제 Gmail 소비자 계정을 사용할 때 Gmail 커넥터를 사용 하 여 동일한 논리 앱 워크플로에서 사용할 수 있는 Google 승인 된 트리거, 작업 및 커넥터는 다음과 같습니다.

* 일괄 처리, 제어, 데이터 작업, 날짜/시간, 플랫 파일, 액체, 요청, 일정, 변수 및 XML Logic Apps 기본 제공 트리거 및 동작을 제공 합니다.

  Google에서 승인 되지 않은 기본 제공 트리거 및 작업 (예: HTTP, Azure Functions, Azure Logic Apps 및 기타)은 앱이 어디에서 나 데이터를 보내거나 받을 수 있기 때문에 Gmail 커넥터와 호환 되지 않는 논리 앱을 만듭니다.

* Google 서비스: Gmail, Google 캘린더, Google 연락처, Google Drive, Google Sheets 및 Google 작업

* 승인 된 Microsoft 서비스: Dynamics 365, Excel Online, Microsoft 팀, Microsoft 365, OneDrive 및 SharePoint Online

* 고객이 관리 하는 데이터 원본에 대 한 커넥터: FTP, RSS, SFTP, SMTP 및 SQL Server

## <a name="non-compliant-examples"></a>비규격 예제

Google에서 승인 되지 않은 기본 제공 트리거와 작업 또는 관리 되는 커넥터를 사용 하는 Gmail 커넥터를 사용 하는 몇 가지 예제는 다음과 같습니다.

* 이 논리 앱은 HTTP 기본 제공 트리거와 함께 Gmail 커넥터를 사용 합니다.

  ![비호환 논리 앱-예제 1](./media/connectors-google-data-security-privacy-policy/not-compliant-logic-app-1.png)
  
  또한 논리 앱은 승인 된 Google 캘린더 커넥터를 사용 합니다.

* 이 논리 앱은 Azure Blob Storage 커넥터에서 Gmail 커넥터를 사용 합니다.

  ![비호환 논리 앱-예제 2](./media/connectors-google-data-security-privacy-policy/not-compliant-logic-app-2.png)

* 이 논리 앱은 Twitter 커넥터를 사용 하 여 Gmail 커넥터를 사용 합니다.

  ![비호환 논리 앱-예제 3](./media/connectors-google-data-security-privacy-policy/not-compliant-logic-app-3.png)

최신 정보는 [Gmail 커넥터의 기술 참조 설명서](/connectors/gmail/)를 참조 하세요.

<a name="update-affected-workflows"></a>

## <a name="steps-for-affected-logic-apps"></a>영향을 받는 논리 앱에 대 한 단계

Gmail 소비자 계정으로 Gmail 커넥터를 사용 하 고 논리 앱에서 Google 승인 되지 않은 커넥터를 사용 해야 하는 경우 회사에서 개인 또는 내부용으로 사용자 고유의 Google 앱을 만들 수 있습니다. 이 시나리오에서는 다음과 같은 개략적인 단계를 수행 해야 합니다.

1. [GOOGLE API 콘솔](https://console.developers.google.com)을 사용 하 여 google 클라이언트 앱을 만듭니다.

1. Gmail 커넥터에서 Google 클라이언트 앱의 클라이언트 ID 및 클라이언트 암호 값을 사용 합니다.

자세한 내용은 [Gmail 커넥터의 기술 참조 설명서](/connectors/gmail/#authentication-and-bring-your-own-application)를 참조 하세요.

### <a name="create-google-client-app"></a>Google 클라이언트 앱 만들기

클라이언트 앱에 대 한 프로젝트를 설정 하려면 [GOOGLE API 콘솔 마법사](https://console.developers.google.com/start/api?id=gmail&credential=client_key) 를 사용 하 여 지침을 따릅니다. 또는 자세한 단계를 보려면 [Gmail 커넥터의 기술 참조 설명서](/connectors/gmail/#authentication-and-bring-your-own-application)에 있는 지침을 검토 하세요.

완료 되 면 사용자가 논리 앱에서 나중에 사용할 수 있는 고유한 **클라이언트 ID** 및 **클라이언트 암호** 값을 포함 한다는 점을 제외 하 고 화면은 다음 예제와 같습니다.

![Google 클라이언트 앱에 대 한 클라이언트 ID 및 클라이언트 암호](./media/connectors-google-data-security-privacy-policy/google-api-console.png)

### <a name="use-client-app-settings-in-logic-app"></a>논리 앱에서 클라이언트 앱 설정 사용

Gmail 트리거 또는 작업에서 Google 클라이언트 앱의 클라이언트 ID 및 클라이언트 암호를 사용 하려면 다음 단계를 수행 합니다.

1. [Azure Portal](https://portal.azure.com)의 Logic Apps 디자이너에서 논리 앱을 엽니다.

1. 새 Gmail 트리거 또는 작업을 추가 하 고 완전히 새로운 연결을 만드는 경우 다음 단계를 계속 합니다. 그렇지 않은 경우 Gmail 트리거 또는 작업에서 **변경 연결**  >  **추가 새로 추가**를 선택 합니다. 예를 들면 다음과 같습니다.

   !["연결 변경" > "새로 추가"를 선택 합니다.](./media/connectors-google-data-security-privacy-policy/change-gmail-connection.png)

1. 연결 정보를 제공 합니다. 예를 들면 다음과 같습니다.

   ![연결 정보 제공](./media/connectors-google-data-security-privacy-policy/authentication-type-bring-your-own.png)

   | 속성 | 값 | 설명 |
   |----------|-------|-------------|
   | **인증 유형** | **사용자 고유의 응용 프로그램 가져오기** | 인증을 위해 사용자 고유의 클라이언트 앱을 사용 하도록 지정 합니다. |
   | **클라이언트 ID** | <*client-ID*> | Google 클라이언트 앱의 클라이언트 ID |
   | **클라이언트 암호** | <*client-secret*> | Google 클라이언트 앱의 클라이언트 암호 |
   ||||

1. 완료 되 면 **로그인**을 선택 합니다.

   만든 클라이언트 앱을 보여 주는 페이지가 나타납니다. Gmail 소비자 계정을 사용 하는 경우 Google에서 클라이언트 앱을 확인 하지 않고, 먼저 Google 계정에 대 한 액세스를 허용 하 라는 메시지가 표시 되는 페이지가 표시 될 수 있습니다.

   ![Google 계정에 대 한 액세스 확인](./media/connectors-google-data-security-privacy-policy/allow-access-authorized-domain.png)

1. 필요한 경우 **허용**을 선택 합니다.

   이제 논리 앱에 대 한 제한 없이 Gmail 커넥터를 사용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Gmail 커넥터](/connectors/gmail/) 에 대 한 자세한 정보

