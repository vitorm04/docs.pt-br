---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394265"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="0e5ce-101">Autorização: sobrecarga de addautoria movida para um assembly diferente</span><span class="sxs-lookup"><span data-stu-id="0e5ce-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="0e5ce-102">Os métodos Core `AddAuthorization` que costumava residir em `Microsoft.AspNetCore.Authorization` foram renomeados para `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="0e5ce-103">Os métodos antigos de `AddAuthorization` ainda existem, mas estão no pacote `Microsoft.AspNetCore.Authorization.Policy`, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` package instead.</span></span> <span data-ttu-id="0e5ce-104">Os aplicativos que usam os dois métodos não devem ter nenhum impacto.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="0e5ce-105">Os aplicativos que não estavam usando o pacote de política devem mudar para usando `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-105">Apps that weren't using the policy package must switch to using `AddAuthorizationCore`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e5ce-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0e5ce-106">Version introduced</span></span>

<span data-ttu-id="0e5ce-107">3.0</span><span class="sxs-lookup"><span data-stu-id="0e5ce-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0e5ce-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0e5ce-108">Old behavior</span></span>

<span data-ttu-id="0e5ce-109">os métodos `AddAuthorization` existiam no `Microsoft.AspNetCore.Authorization`.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0e5ce-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0e5ce-110">New behavior</span></span>

<span data-ttu-id="0e5ce-111">os métodos `AddAuthorization` existem no `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="0e5ce-112">`AddAuthorizationCore` é o novo nome para os métodos antigos.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0e5ce-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="0e5ce-113">Reason for change</span></span>

<span data-ttu-id="0e5ce-114">`AddAuthorization` é um nome de método melhor para adicionar todos os serviços comuns necessários para autorização.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e5ce-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0e5ce-115">Recommended action</span></span>

<span data-ttu-id="0e5ce-116">Adicione uma referência a `Microsoft.AspNetCore.Authorization.Policy` ou use `AddAuthorizationCore` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0e5ce-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="0e5ce-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="0e5ce-117">Category</span></span>

<span data-ttu-id="0e5ce-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0e5ce-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e5ce-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0e5ce-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
