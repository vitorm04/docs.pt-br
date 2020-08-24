---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394040"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="024d2-101">Identidade: o SignInAsync gera uma exceção para a identidade não autenticada</span><span class="sxs-lookup"><span data-stu-id="024d2-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="024d2-102">Por padrão, `SignInAsync` o gera uma exceção para entidades/identidades em que `IsAuthenticated` é `false` .</span><span class="sxs-lookup"><span data-stu-id="024d2-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="024d2-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="024d2-103">Version introduced</span></span>

<span data-ttu-id="024d2-104">3,0</span><span class="sxs-lookup"><span data-stu-id="024d2-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="024d2-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="024d2-105">Old behavior</span></span>

<span data-ttu-id="024d2-106">`SignInAsync` aceita quaisquer entidades/identidades, incluindo identidades em que `IsAuthenticated` é `false` .</span><span class="sxs-lookup"><span data-stu-id="024d2-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="024d2-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="024d2-107">New behavior</span></span>

<span data-ttu-id="024d2-108">Por padrão, `SignInAsync` o gera uma exceção para entidades/identidades em que `IsAuthenticated` é `false` .</span><span class="sxs-lookup"><span data-stu-id="024d2-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="024d2-109">Há um novo sinalizador para suprimir esse comportamento, mas o comportamento padrão foi alterado.</span><span class="sxs-lookup"><span data-stu-id="024d2-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="024d2-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="024d2-110">Reason for change</span></span>

<span data-ttu-id="024d2-111">O comportamento antigo era problemático porque, por padrão, essas entidades foram rejeitadas pelo `[Authorize]`  /  `RequireAuthenticatedUser()` .</span><span class="sxs-lookup"><span data-stu-id="024d2-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="024d2-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="024d2-112">Recommended action</span></span>

<span data-ttu-id="024d2-113">No ASP.NET Core 3,0 Preview 6, há um `RequireAuthenticatedSignIn` sinalizador `AuthenticationOptions` `true` por padrão.</span><span class="sxs-lookup"><span data-stu-id="024d2-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="024d2-114">Defina esse sinalizador como `false` para restaurar o comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="024d2-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="024d2-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="024d2-115">Category</span></span>

<span data-ttu-id="024d2-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="024d2-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="024d2-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="024d2-117">Affected APIs</span></span>

<span data-ttu-id="024d2-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="024d2-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
