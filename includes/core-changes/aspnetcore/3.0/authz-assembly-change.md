---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100640"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="0d7fc-101">Autorização: Adicionar Sobrecarga de autorização movida para diferentes conjuntos</span><span class="sxs-lookup"><span data-stu-id="0d7fc-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="0d7fc-102">Os `AddAuthorization` métodos centrais que `Microsoft.AspNetCore.Authorization` costumavam `AddAuthorizationCore`residir foram renomeados para .</span><span class="sxs-lookup"><span data-stu-id="0d7fc-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="0d7fc-103">Os `AddAuthorization` métodos antigos ainda existem, mas estão na `Microsoft.AspNetCore.Authorization.Policy` montagem em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0d7fc-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="0d7fc-104">Os aplicativos que usam ambos os métodos não devem ver nenhum impacto.</span><span class="sxs-lookup"><span data-stu-id="0d7fc-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="0d7fc-105">Observe `Microsoft.AspNetCore.Authorization.Policy` que agora é enviado no framework compartilhado em vez de um pacote autônomo como discutido no [Framework Compartilhado: Conjuntos removidos do Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="0d7fc-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0d7fc-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0d7fc-106">Version introduced</span></span>

<span data-ttu-id="0d7fc-107">3.0</span><span class="sxs-lookup"><span data-stu-id="0d7fc-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0d7fc-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0d7fc-108">Old behavior</span></span>
<span data-ttu-id="0d7fc-109">`AddAuthorization`métodos existiam `Microsoft.AspNetCore.Authorization`em .</span><span class="sxs-lookup"><span data-stu-id="0d7fc-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0d7fc-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0d7fc-110">New behavior</span></span>

<span data-ttu-id="0d7fc-111">`AddAuthorization`métodos existem em `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="0d7fc-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="0d7fc-112">`AddAuthorizationCore`é o novo nome para os métodos antigos.</span><span class="sxs-lookup"><span data-stu-id="0d7fc-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0d7fc-113">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="0d7fc-113">Reason for change</span></span>

<span data-ttu-id="0d7fc-114">`AddAuthorization`é um nome de método melhor para adicionar todos os serviços comuns necessários para autorização.</span><span class="sxs-lookup"><span data-stu-id="0d7fc-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0d7fc-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0d7fc-115">Recommended action</span></span>

<span data-ttu-id="0d7fc-116">Adicione uma referência `Microsoft.AspNetCore.Authorization.Policy` ou `AddAuthorizationCore` use em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0d7fc-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="0d7fc-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="0d7fc-117">Category</span></span>

<span data-ttu-id="0d7fc-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0d7fc-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0d7fc-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0d7fc-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
