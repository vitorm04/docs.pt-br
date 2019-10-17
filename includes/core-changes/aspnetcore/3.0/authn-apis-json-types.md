---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394253"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="5cd90-101">Autenticação: tipos Newtonsoft. JSON substituídos</span><span class="sxs-lookup"><span data-stu-id="5cd90-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="5cd90-102">No ASP.NET Core 3,0, os tipos `Newtonsoft.Json` usados em APIs de autenticação foram substituídos por tipos `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="5cd90-103">Exceto pelos seguintes casos, o uso básico dos pacotes de autenticação permanece inalterado:</span><span class="sxs-lookup"><span data-stu-id="5cd90-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="5cd90-104">Classes derivadas de provedores OAuth, como as de [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="5cd90-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="5cd90-105">Implementações avançadas de manipulação de declaração.</span><span class="sxs-lookup"><span data-stu-id="5cd90-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="5cd90-106">Para obter mais informações, consulte [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="5cd90-106">For more information, see [aspnet/AspNetCore#7105](https://github.com/aspnet/AspNetCore/pull/7105).</span></span> <span data-ttu-id="5cd90-107">Para obter uma discussão, consulte [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="5cd90-107">For discussion, see [aspnet/AspNetCore#7289](https://github.com/aspnet/AspNetCore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5cd90-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5cd90-108">Version introduced</span></span>

<span data-ttu-id="5cd90-109">3.0</span><span class="sxs-lookup"><span data-stu-id="5cd90-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5cd90-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5cd90-110">Recommended action</span></span>

<span data-ttu-id="5cd90-111">Para implementações de OAuth derivadas, a alteração mais comum é substituir `JObject.Parse` por `JsonDocument.Parse` na substituição `CreateTicketAsync`, conforme mostrado [aqui](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="5cd90-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="5cd90-112">`JsonDocument` implementa `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="5cd90-113">A lista a seguir descreve as alterações conhecidas:</span><span class="sxs-lookup"><span data-stu-id="5cd90-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="5cd90-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> se torna `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="5cd90-115">Todas as implementações derivadas de `ClaimAction` são afetadas de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="5cd90-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="5cd90-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> se torna `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="5cd90-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="5cd90-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> se torna `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="5cd90-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="5cd90-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> teve um Construtor antigo removido e o outro foi substituído `JObject` por `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="5cd90-119">A propriedade `User` e o método `RunClaimActions` foram atualizados para corresponder.</span><span class="sxs-lookup"><span data-stu-id="5cd90-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="5cd90-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> agora aceita um parâmetro do tipo `JsonDocument` em vez de `JObject`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="5cd90-121">A propriedade `Response` foi atualizada para corresponder.</span><span class="sxs-lookup"><span data-stu-id="5cd90-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="5cd90-122">`OAuthTokenResponse` agora é descartável e será descartado por `OAuthHandler`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="5cd90-123">As implementações de OAuth derivadas que substituem `ExchangeCodeAsync` não precisam descartar o `JsonDocument` ou o `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="5cd90-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> alterado de `JObject` para `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="5cd90-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> alterado de `JObject` para `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="5cd90-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> mudou de aceitando `JObject` para `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="5cd90-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="5cd90-127">Categoria</span><span class="sxs-lookup"><span data-stu-id="5cd90-127">Category</span></span>

<span data-ttu-id="5cd90-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5cd90-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5cd90-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5cd90-129">Affected APIs</span></span>

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
