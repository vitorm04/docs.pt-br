---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394228"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="e5ca9-101">Autorização: implementações de IAuthorizationPolicyProvider exigem novo método</span><span class="sxs-lookup"><span data-stu-id="e5ca9-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="e5ca9-102">No ASP.NET Core 3,0, um novo método `GetFallbackPolicyAsync` foi adicionado a `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="e5ca9-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="e5ca9-103">Essa política de fallback é usada pelo middleware de autorização quando nenhuma política é especificada.</span><span class="sxs-lookup"><span data-stu-id="e5ca9-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="e5ca9-104">Para obter mais informações, consulte [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="e5ca9-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="e5ca9-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e5ca9-105">Version introduced</span></span>

<span data-ttu-id="e5ca9-106">3.0</span><span class="sxs-lookup"><span data-stu-id="e5ca9-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e5ca9-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="e5ca9-107">Old behavior</span></span>

<span data-ttu-id="e5ca9-108">As implementações de `IAuthorizationPolicyProvider` não exigiam um método `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="e5ca9-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e5ca9-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="e5ca9-109">New behavior</span></span>

<span data-ttu-id="e5ca9-110">As implementações de `IAuthorizationPolicyProvider` exigem um método `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="e5ca9-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e5ca9-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="e5ca9-111">Reason for change</span></span>

<span data-ttu-id="e5ca9-112">Um novo método era necessário para o novo `AuthorizationMiddleware` a ser usado quando nenhuma política é especificada.</span><span class="sxs-lookup"><span data-stu-id="e5ca9-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5ca9-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e5ca9-113">Recommended action</span></span>

<span data-ttu-id="e5ca9-114">Adicione o método `GetFallbackPolicyAsync` às suas implementações de `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="e5ca9-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="e5ca9-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="e5ca9-115">Category</span></span>

<span data-ttu-id="e5ca9-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5ca9-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5ca9-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e5ca9-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
