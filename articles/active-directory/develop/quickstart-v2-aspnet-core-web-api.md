---
title: '빠른 시작: Microsoft ID 플랫폼을 사용하여 ASP.NET Core 웹 API 보호 | Azure'
titleSuffix: Microsoft identity platform
description: 이 빠른 시작에서는 권한 부여를 위해 Microsoft ID 플랫폼을 사용하여 ASP.NET Core 웹 API를 보호하는 방법을 보여 주는 코드 샘플을 다운로드하고 수정합니다.
services: active-directory
author: jmprieur
manager: CelesteDG
ms.service: active-directory
ms.subservice: develop
ms.topic: quickstart
ms.workload: identity
ms.date: 09/22/2020
ms.author: jmprieur
ms.custom: devx-track-csharp, scenarios:getting-started, languages:aspnet-core
ms.openlocfilehash: dc0cdca2355403bc8f5409d9a6ca7f4ae89caf25
ms.sourcegitcommit: eb6bef1274b9e6390c7a77ff69bf6a3b94e827fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/05/2020
ms.locfileid: "90945592"
---
# <a name="quickstart-protect-an-aspnet-core-web-api-with-microsoft-identity-platform"></a>빠른 시작: Microsoft ID 플랫폼을 사용하여 ASP.NET Core 웹 API 보호

이 빠른 시작에서는 코드 샘플을 사용하여 권한 있는 계정에서만 액세스할 수 있도록 ASP.NET Core 웹 API를 보호하는 방법을 알아봅니다. 계정은 모든 Azure AD(Azure Active Directory) 인스턴스에서 개인 계정(hotmail.com, outlook.com 등)과 회사 및 학교 계정일 수 있습니다.

> [!div renderon="docs"]
> ## <a name="prerequisites"></a>사전 요구 사항
>
> - 활성 구독이 있는 Azure 계정. [체험 계정을 만듭니다](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
> - [Azure Active Directory 테넌트](quickstart-create-new-tenant.md)
> - [.NET Core SDK 3.1+](https://dotnet.microsoft.com/)
> - [Visual Studio 2019](https://visualstudio.microsoft.com/vs/) 또는 [Visual Studio Code](https://code.visualstudio.com/)
>
> ## <a name="step-1-register-the-application"></a>1단계: 애플리케이션 등록
>
> 먼저 Azure AD 테넌트에 웹 API를 등록하고 다음 단계를 수행하여 범위를 추가합니다.
>
> 1. [Azure Portal](https://portal.azure.com)에 로그인합니다.
> 1. 여러 테넌트에 액세스할 수 있는 경우 위쪽 메뉴의 **디렉터리 + 구독** 필터 :::image type="icon" source="./media/common/portal-directory-subscription-filter.png" border="false":::를 사용하여 애플리케이션을 등록하려는 테넌트를 선택합니다.
> 1. **Azure Active Directory**를 검색하고 선택합니다.
> 1. **관리** 아래에서 **앱 등록**, **새 등록**을 차례로 선택합니다.
> 1. 애플리케이션에 대한 **이름**을 입력합니다(예: `AspNetCoreWebApi-Quickstart`). 이 이름은 앱의 사용자에게 표시될 수 있으며 나중에 변경할 수 있습니다.
> 1. **등록**을 선택합니다.
> 1. **관리**에서 **API 표시**를 선택합니다.
> 1. **범위 추가**를 선택하고 **저장 후 계속**을 선택하여 기본 **애플리케이션 ID URI**를 적용합니다.
> 1. **범위 추가** 창에서 다음 값을 입력합니다.
>    - **범위 이름**: `access_as_user`
>    - **동의할 수 있는 사람**: **관리자 및 사용자**
>    - **관리자 동의 표시 이름**: `Access AspNetCoreWebApi-Quickstart`
>    - **관리자 동의 설명**: `Allows the app to access AspNetCoreWebApi-Quickstart as the signed-in user.`
>    - **사용자 동의 표시 이름**: `Access AspNetCoreWebApi-Quickstart`
>    - **사용자 동의 설명**: `Allow the application to access AspNetCoreWebApi-Quickstart on your behalf.`
>    - **상태**: **Enabled**
> 1. **범위 추가**를 선택하여 범위 추가를 완료합니다.

## <a name="step-2-download-the-aspnet-core-project"></a>2단계: ASP.NET Core 프로젝트 다운로드

> [!div renderon="docs"]
> GitHub에서 [ASP.NET Core 솔루션을 다운로드](https://github.com/Azure-Samples/active-directory-dotnet-native-aspnetcore-v2/archive/aspnetcore3-1.zip)합니다.

> [!div renderon="docs"]
> ## <a name="step-3-configure-the-aspnet-core-project"></a>3단계: ASP.NET Core 프로젝트 구성
>
> 이 단계에서는 이전에 만든 앱 등록을 사용하도록 샘플 코드를 구성합니다.
>
> 1. 드라이브 루트 근처의 폴더로 .zip 보관 파일을 추출합니다. 예를 들어 *C:\Azure-Samples*입니다.
> 1. 코드 편집기의 *webapi* 폴더에서 솔루션을 엽니다.
> 1. *appsettings.json* 파일을 열고 다음을 수정합니다.
>
>    ```json
>    "ClientId": "Enter_the_Application_Id_here",
>    "TenantId": "Enter_the_Tenant_Info_Here"
>    ```
>
>    - `Enter_the_Application_Id_here`를 Azure Portal에 등록한 애플리케이션의 **애플리케이션(클라이언트) ID**로 바꿉니다. 앱의 **개요** 페이지에서 **애플리케이션(클라이언트) ID**를 찾을 수 있습니다.
>    - `Enter_the_Tenant_Info_Here`를 다음 중 하나로 바꿉니다.
>       - 애플리케이션이 **이 조직 디렉터리의 계정**을 지원하는 경우 이 값을 **디렉터리(테넌트) ID**(GUID) 또는 **테넌트 이름**(예: `contoso.onmicrosoft.com`)으로 바꿉니다. 앱의 **개요** 페이지에서 **디렉터리(테넌트) ID**를 찾을 수 있습니다.
>       - 애플리케이션이 **모든 조직 디렉터리의 계정**을 지원하는 경우 이 값을 `organizations`로 바꾸세요.
>       - 애플리케이션이 **모든 Microsoft 계정 사용자**를 지원하는 경우 이 값을 `common`으로 둡니다.
>
> 이 빠른 시작에서는 *appsettings.json* 파일에서 다른 값을 변경하지 마세요.

## <a name="how-the-sample-works"></a>샘플 작동 방법

웹 API는 클라이언트 애플리케이션에서 토큰을 수신하고 웹 API의 코드는 토큰의 유효성을 검사합니다. 이 시나리오는 [시나리오: 보호된 웹 API](scenario-protected-web-api-overview.md)에 자세히 설명되어 있습니다.

### <a name="startup-class"></a>시작 클래스

*Microsoft.AspNetCore.Authentication* 미들웨어는 호스팅 프로세스가 초기화될 때 실행되는 `Startup` 클래스를 사용합니다. 해당 `ConfigureServices` 메서드에서는 *Microsoft.Identity.Web*에서 제공하는 `AddMicrosoftIdentityWebApi` 확장 메서드가 호출됩니다.

```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
                .AddMicrosoftIdentityWebApi(Configuration, "AzureAd");
    }
```

`AddAuthentication()` 메서드는 JwtBearer 기반 인증을 추가하도록 서비스를 구성합니다.

`.AddMicrosoftIdentityWebApi`가 포함된 줄은 웹 API에 Microsoft ID 플랫폼 권한 부여를 추가합니다. 그런 다음, *appsettings.json* 구성 파일의 `AzureAD` 섹션에 있는 정보를 기반으로 Microsoft ID 플랫폼 엔드포인트에서 발급한 액세스 토큰의 유효성을 검사하도록 구성됩니다.

| *appsettings.json* 키 | 설명                                                                                                                                                          |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ClientId`             | Azure Portal에 등록된 애플리케이션의 **애플리케이션(클라이언트) ID**입니다.                                                                                       |
| `Instance`             | 사용자가 인증하는 STS(보안 토큰 서비스) 엔드포인트 이 값은 일반적으로 `https://login.microsoftonline.com/`이며, Azure 퍼블릭 클라우드를 나타냅니다. |
| `TenantId`             | 회사 또는 학교 계정이나 Microsoft 개인 계정을 사용하여 사용자를 로그인하는 테넌트의 이름 또는 해당 테넌트 ID(GUID) 또는 *공용*입니다.                             |

`Configure()` 메서드에는 명명된 기능을 사용할 수 있도록 설정하는 두 가지 중요한 메서드인 `app.UseAuthentication()` 및 `app.UseAuthorization()`이 포함되어 있습니다.

```csharp
// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    // more code
    app.UseAuthentication();
    app.UseAuthorization();
    // more code
}
```

### <a name="protect-a-controller-a-controllers-method-or-a-razor-page"></a>컨트롤러, 컨트롤러의 메서드 또는 Razor 페이지 보호

`[Authorize]` 특성을 사용하여 컨트롤러 또는 컨트롤러 메서드를 보호할 수 있습니다. 이 특성은 인증된 사용자만 허용하여 컨트롤러에 대한 액세스를 제한합니다. 즉, 사용자가 인증되지 않은 경우 인증 질문을 시작하여 컨트롤러에 액세스할 수 있습니다.

```csharp
namespace webapi.Controllers
{
    [Authorize]
    [ApiController]
    [Route("[controller]")]
    public class WeatherForecastController : ControllerBase
```

### <a name="validate-the-scope-in-the-controller"></a>컨트롤러의 범위 유효성 검사

그런 다음, API의 코드는 `HttpContext.VerifyUserHasAnyAcceptedScope(scopeRequiredByApi);`를 사용하여 필요한 범위가 토큰에 있는지 확인합니다.

```csharp
namespace webapi.Controllers
{
    [Authorize]
    [ApiController]
    [Route("[controller]")]
    public class WeatherForecastController : ControllerBase
    {
        // The Web API will only accept tokens 1) for users, and 2) having the "access_as_user" scope for this API
        static readonly string[] scopeRequiredByApi = new string[] { "access_as_user" };

        [HttpGet]
        public IEnumerable<WeatherForecast> Get()
        {
            HttpContext.VerifyUserHasAnyAcceptedScope(scopeRequiredByApi);

            // some code here
        }
    }
}
```

[!INCLUDE [Help and support](../../../includes/active-directory-develop-help-support-include.md)]

## <a name="next-steps"></a>다음 단계

이 ASP.NET Core 웹 API 코드 샘플을 포함하는 GitHub 리포지토리에는 다음 방법을 보여 주는 지침과 추가 코드 샘플이 포함되어 있습니다.

- 새 ASP.NET Core 웹 API에 인증 추가
- 데스크톱 애플리케이션에서 웹 API 호출
- Microsoft Graph 및 기타 Microsoft API와 같은 다운스트림 API 호출

> [!div class="nextstepaction"]
> [GitHub의 ASP.NET Core 웹 API 자습서](https://github.com/Azure-Samples/active-directory-dotnet-native-aspnetcore-v2)
