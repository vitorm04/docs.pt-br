---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901954"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="28461-101">Autorização: implementações de IAuthorizationPolicyProvider exigem novo método</span><span class="sxs-lookup"><span data-stu-id="28461-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="28461-102">No ASP.NET Core 3,0, um novo método `GetFallbackPolicyAsync` foi adicionado a `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="28461-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="28461-103">Essa política de fallback é usada pelo middleware de autorização quando nenhuma política é especificada.</span><span class="sxs-lookup"><span data-stu-id="28461-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="28461-104">Para obter mais informações, consulte [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="28461-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="28461-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="28461-105">Version introduced</span></span>

<span data-ttu-id="28461-106">3.0</span><span class="sxs-lookup"><span data-stu-id="28461-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="28461-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="28461-107">Old behavior</span></span>

<span data-ttu-id="28461-108">As implementações de `IAuthorizationPolicyProvider` não exigiam um método `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="28461-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="28461-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="28461-109">New behavior</span></span>

<span data-ttu-id="28461-110">Implementações de `IAuthorizationPolicyProvider` exigem um método `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="28461-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="28461-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="28461-111">Reason for change</span></span>

<span data-ttu-id="28461-112">Um novo método era necessário para o novo `AuthorizationMiddleware` a ser usado quando nenhuma política é especificada.</span><span class="sxs-lookup"><span data-stu-id="28461-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="28461-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="28461-113">Recommended action</span></span>

<span data-ttu-id="28461-114">Adicione o método `GetFallbackPolicyAsync` às suas implementações de `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="28461-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="28461-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="28461-115">Category</span></span>

<span data-ttu-id="28461-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="28461-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="28461-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="28461-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
