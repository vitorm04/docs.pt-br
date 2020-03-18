---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901764"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="82ce6-101">Autenticação: Tipos Newtonsoft.Json substituídos</span><span class="sxs-lookup"><span data-stu-id="82ce6-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="82ce6-102">Em ASP.NET Núcleo 3.0, `Newtonsoft.Json` os tipos usados nas `System.Text.Json` APIs de autenticação foram substituídos por tipos.</span><span class="sxs-lookup"><span data-stu-id="82ce6-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="82ce6-103">Exceto para os seguintes casos, o uso básico dos pacotes de autenticação permanece inalterado:</span><span class="sxs-lookup"><span data-stu-id="82ce6-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="82ce6-104">Classes derivadas dos provedores OAuth, como as do [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="82ce6-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="82ce6-105">Implementações avançadas de manipulação de sinistros.</span><span class="sxs-lookup"><span data-stu-id="82ce6-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="82ce6-106">Para obter mais informações, consulte [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="82ce6-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="82ce6-107">Para discussão, consulte [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="82ce6-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82ce6-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="82ce6-108">Version introduced</span></span>

<span data-ttu-id="82ce6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="82ce6-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82ce6-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="82ce6-110">Recommended action</span></span>

<span data-ttu-id="82ce6-111">Para implementações oAuth derivadas, a mudança `JObject.Parse` `JsonDocument.Parse` mais `CreateTicketAsync` comum é substituir na substituição como mostrado [aqui](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="82ce6-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="82ce6-112">`JsonDocument` implementa `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="82ce6-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="82ce6-113">A lista a seguir descreve alterações conhecidas:</span><span class="sxs-lookup"><span data-stu-id="82ce6-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="82ce6-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>torna-se `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="82ce6-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="82ce6-115">Todas as implementações `ClaimAction` derivadas são igualmente afetadas.</span><span class="sxs-lookup"><span data-stu-id="82ce6-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="82ce6-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> torna-se `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="82ce6-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="82ce6-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> torna-se `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="82ce6-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="82ce6-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>teve um antigo construtor removido e `JObject` o `JsonElement`outro substituído por .</span><span class="sxs-lookup"><span data-stu-id="82ce6-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="82ce6-119">A `User` propriedade `RunClaimActions` e o método foram atualizados para coincidir.</span><span class="sxs-lookup"><span data-stu-id="82ce6-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="82ce6-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>agora aceita um parâmetro `JsonDocument` de `JObject`tipo em vez de .</span><span class="sxs-lookup"><span data-stu-id="82ce6-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="82ce6-121">A `Response` propriedade foi atualizada para coincidir.</span><span class="sxs-lookup"><span data-stu-id="82ce6-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="82ce6-122">`OAuthTokenResponse`agora é descartável e `OAuthHandler`será descartado por .</span><span class="sxs-lookup"><span data-stu-id="82ce6-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="82ce6-123">Implementações oAuth derivadas `ExchangeCodeAsync` não precisam descartar `JsonDocument` o `OAuthTokenResponse`ou .</span><span class="sxs-lookup"><span data-stu-id="82ce6-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="82ce6-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>mudou `JObject` de `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="82ce6-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="82ce6-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>mudou `JObject` de `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="82ce6-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="82ce6-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>mudou de `JObject` `JsonElement`aceitar para .</span><span class="sxs-lookup"><span data-stu-id="82ce6-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="82ce6-127">Categoria</span><span class="sxs-lookup"><span data-stu-id="82ce6-127">Category</span></span>

<span data-ttu-id="82ce6-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="82ce6-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82ce6-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="82ce6-129">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
