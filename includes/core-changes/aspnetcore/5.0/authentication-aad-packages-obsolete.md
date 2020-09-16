---
ms.openlocfilehash: 8bcd9987cb061233c8476b9c083a224fc0e25440
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539435"
---
### <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="0b2fa-101">Autenticação: AzureAD. UI e AzureADB2C. UI APIs e pacotes marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="0b2fa-101">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="0b2fa-102">No ASP.NET Core 2,1, a integração com o Azure Active Directory (Azure AD) e a autenticação Azure Active Directory B2C (Azure AD B2C) são fornecidas pelos pacotes [Microsoft. AspNetCore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) e [Microsoft. AspNetCore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) .</span><span class="sxs-lookup"><span data-stu-id="0b2fa-102">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="0b2fa-103">A funcionalidade fornecida por esses pacotes é baseada no ponto de extremidade v 1.0 do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0b2fa-103">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="0b2fa-104">No ASP.NET Core 5,0 e posterior, a integração com o Azure AD e a autenticação Azure AD B2C é fornecida pelo pacote [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) .</span><span class="sxs-lookup"><span data-stu-id="0b2fa-104">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="0b2fa-105">Este pacote é baseado na plataforma de identidade da Microsoft, que é conhecida anteriormente como ponto de extremidade v 2.0 do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0b2fa-105">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="0b2fa-106">Consequentemente, as APIs antigas nos `Microsoft.AspNetCore.Authentication.AzureAD.UI` `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` pacotes e foram preteridas.</span><span class="sxs-lookup"><span data-stu-id="0b2fa-106">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="0b2fa-107">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).</span><span class="sxs-lookup"><span data-stu-id="0b2fa-107">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0b2fa-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0b2fa-108">Version introduced</span></span>

<span data-ttu-id="0b2fa-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0b2fa-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0b2fa-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0b2fa-110">Old behavior</span></span>

<span data-ttu-id="0b2fa-111">As APIs não estavam marcadas como obsoletas.</span><span class="sxs-lookup"><span data-stu-id="0b2fa-111">The APIs weren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0b2fa-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0b2fa-112">New behavior</span></span>

<span data-ttu-id="0b2fa-113">As APIs são marcadas como obsoletas.</span><span class="sxs-lookup"><span data-stu-id="0b2fa-113">The APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0b2fa-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="0b2fa-114">Reason for change</span></span>

<span data-ttu-id="0b2fa-115">A funcionalidade de autenticação do Azure AD e Azure AD B2C foi migrada para as APIs da MSAL (biblioteca de autenticação da Microsoft) fornecidas pelo `Microsoft.Identity.Web` .</span><span class="sxs-lookup"><span data-stu-id="0b2fa-115">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0b2fa-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0b2fa-116">Recommended action</span></span>

<span data-ttu-id="0b2fa-117">Siga as `Microsoft.Identity.Web` diretrizes de API para [aplicativos Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) e [APIs Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span><span class="sxs-lookup"><span data-stu-id="0b2fa-117">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

#### <a name="category"></a><span data-ttu-id="0b2fa-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="0b2fa-118">Category</span></span>

<span data-ttu-id="0b2fa-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b2fa-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0b2fa-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0b2fa-120">Affected APIs</span></span>

* [<span data-ttu-id="0b2fa-121">Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="0b2fa-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="0b2fa-122">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="0b2fa-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="0b2fa-123">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADOptions</span><span class="sxs-lookup"><span data-stu-id="0b2fa-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="0b2fa-124">Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="0b2fa-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="0b2fa-125">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="0b2fa-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="0b2fa-126">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="0b2fa-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
