---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901764"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="bc7c5-101">Autenticação: tipos Newtonsoft. JSON substituídos</span><span class="sxs-lookup"><span data-stu-id="bc7c5-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="bc7c5-102">No ASP.NET Core 3,0, `Newtonsoft.Json` tipos usados em APIs de autenticação foram substituídos por `System.Text.Json` tipos.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="bc7c5-103">Exceto pelos seguintes casos, o uso básico dos pacotes de autenticação permanece inalterado:</span><span class="sxs-lookup"><span data-stu-id="bc7c5-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="bc7c5-104">Classes derivadas de provedores OAuth, como as de [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="bc7c5-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="bc7c5-105">Implementações avançadas de manipulação de declaração.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="bc7c5-106">Para obter mais informações, consulte [dotnet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="bc7c5-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="bc7c5-107">Para obter uma discussão, consulte [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="bc7c5-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bc7c5-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="bc7c5-108">Version introduced</span></span>

<span data-ttu-id="bc7c5-109">3.0</span><span class="sxs-lookup"><span data-stu-id="bc7c5-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bc7c5-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="bc7c5-110">Recommended action</span></span>

<span data-ttu-id="bc7c5-111">Para implementações de OAuth derivadas, a alteração mais comum é substituir `JObject.Parse` por `JsonDocument.Parse` na substituição de `CreateTicketAsync`, conforme mostrado [aqui](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="bc7c5-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="bc7c5-112">`JsonDocument` implementa `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="bc7c5-113">A lista a seguir descreve as alterações conhecidas:</span><span class="sxs-lookup"><span data-stu-id="bc7c5-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="bc7c5-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> se torna `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="bc7c5-115">Todas as implementações derivadas de `ClaimAction` são afetadas de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="bc7c5-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> torna-se `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="bc7c5-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="bc7c5-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> torna-se `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="bc7c5-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="bc7c5-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> teve um Construtor antigo removido e o outro foi substituído `JObject` com `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="bc7c5-119">A propriedade `User` e o método `RunClaimActions` foram atualizados para corresponder.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="bc7c5-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> agora aceita um parâmetro do tipo `JsonDocument` em vez de `JObject`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="bc7c5-121">A propriedade `Response` foi atualizada para corresponder.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="bc7c5-122">`OAuthTokenResponse` agora é descartável e será descartado por `OAuthHandler`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="bc7c5-123">As implementações de OAuth derivadas que substituem `ExchangeCodeAsync` não precisam descartar o `JsonDocument` ou `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="bc7c5-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> alterado de `JObject` para `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="bc7c5-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> alterado de `JObject` para `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="bc7c5-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> alterado de aceitar `JObject` para `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="bc7c5-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="bc7c5-127">Categoria</span><span class="sxs-lookup"><span data-stu-id="bc7c5-127">Category</span></span>

<span data-ttu-id="bc7c5-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bc7c5-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bc7c5-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bc7c5-129">Affected APIs</span></span>

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
