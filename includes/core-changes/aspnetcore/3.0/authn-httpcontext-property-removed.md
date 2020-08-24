---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901921"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="b4ba1-101">Autenticação: Propriedade HttpContext. Authentication removida</span><span class="sxs-lookup"><span data-stu-id="b4ba1-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="b4ba1-102">A propriedade preterida `Authentication` em `HttpContext` foi removida.</span><span class="sxs-lookup"><span data-stu-id="b4ba1-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b4ba1-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="b4ba1-103">Change description</span></span>

<span data-ttu-id="b4ba1-104">Como parte do [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504), a propriedade preterida `Authentication` em `HttpContext` foi removida.</span><span class="sxs-lookup"><span data-stu-id="b4ba1-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="b4ba1-105">A `Authentication` propriedade foi preterida desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="b4ba1-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="b4ba1-106">Um [Guia de migração](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) foi publicado para migrar o código usando essa propriedade preterida para as novas APIs de substituição.</span><span class="sxs-lookup"><span data-stu-id="b4ba1-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="b4ba1-107">As classes/APIs não usadas restantes relacionadas à pilha de autenticação antiga ASP.NET Core 1. x foram removidas na confirmação [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65) .</span><span class="sxs-lookup"><span data-stu-id="b4ba1-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="b4ba1-108">Para obter uma discussão, consulte [dotnet/aspnetcore # 6533](https://github.com/dotnet/aspnetcore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="b4ba1-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b4ba1-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b4ba1-109">Version introduced</span></span>

<span data-ttu-id="b4ba1-110">3,0</span><span class="sxs-lookup"><span data-stu-id="b4ba1-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b4ba1-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b4ba1-111">Reason for change</span></span>

<span data-ttu-id="b4ba1-112">ASP.NET Core APIs 1,0 foram substituídas por métodos de extensão no <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="b4ba1-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b4ba1-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b4ba1-113">Recommended action</span></span>

<span data-ttu-id="b4ba1-114">Consulte o [Guia de migração](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span><span class="sxs-lookup"><span data-stu-id="b4ba1-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="b4ba1-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="b4ba1-115">Category</span></span>

<span data-ttu-id="b4ba1-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b4ba1-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b4ba1-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b4ba1-117">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
