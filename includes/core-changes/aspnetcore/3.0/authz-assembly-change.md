---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74100640"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="ec99f-101">Autorização: sobrecarga de addautoria movida para um assembly diferente</span><span class="sxs-lookup"><span data-stu-id="ec99f-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="ec99f-102">Os métodos Core `AddAuthorization` que costumava residir em `Microsoft.AspNetCore.Authorization` foram renomeados para `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="ec99f-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="ec99f-103">Os métodos de `AddAuthorization` antigos ainda existem, mas estão no assembly `Microsoft.AspNetCore.Authorization.Policy` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ec99f-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="ec99f-104">Os aplicativos que usam os dois métodos não devem ter nenhum impacto.</span><span class="sxs-lookup"><span data-stu-id="ec99f-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="ec99f-105">Observe que `Microsoft.AspNetCore.Authorization.Policy` agora é fornecido na estrutura compartilhada, em vez de um pacote autônomo, conforme discutido em [estrutura compartilhada: assemblies removidos do Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="ec99f-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ec99f-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ec99f-106">Version introduced</span></span>

<span data-ttu-id="ec99f-107">3.0</span><span class="sxs-lookup"><span data-stu-id="ec99f-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ec99f-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ec99f-108">Old behavior</span></span>
<span data-ttu-id="ec99f-109">os métodos `AddAuthorization` existiam no `Microsoft.AspNetCore.Authorization`.</span><span class="sxs-lookup"><span data-stu-id="ec99f-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ec99f-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ec99f-110">New behavior</span></span>

<span data-ttu-id="ec99f-111">os métodos `AddAuthorization` existem no `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="ec99f-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="ec99f-112">`AddAuthorizationCore` é o novo nome para os métodos antigos.</span><span class="sxs-lookup"><span data-stu-id="ec99f-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ec99f-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ec99f-113">Reason for change</span></span>

<span data-ttu-id="ec99f-114">`AddAuthorization` é um nome de método melhor para adicionar todos os serviços comuns necessários para autorização.</span><span class="sxs-lookup"><span data-stu-id="ec99f-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ec99f-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ec99f-115">Recommended action</span></span>

<span data-ttu-id="ec99f-116">Adicione uma referência a `Microsoft.AspNetCore.Authorization.Policy` ou use `AddAuthorizationCore` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ec99f-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="ec99f-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="ec99f-117">Category</span></span>

<span data-ttu-id="ec99f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ec99f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ec99f-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ec99f-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
