---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394435"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="43ef0-101">Estrutura compartilhada: Removed Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="43ef0-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="43ef0-102">A partir de ASP.NET Core `Microsoft.AspNetCore.All` 3.0, `Microsoft.AspNetCore.All` o metapacote e a estrutura compartilhada correspondente não são mais produzidos.</span><span class="sxs-lookup"><span data-stu-id="43ef0-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="43ef0-103">Este pacote está disponível em ASP.NET Core 2.2 e continuará recebendo atualizações de manutenção em ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="43ef0-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="43ef0-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="43ef0-104">Version introduced</span></span>

<span data-ttu-id="43ef0-105">3.0</span><span class="sxs-lookup"><span data-stu-id="43ef0-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="43ef0-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="43ef0-106">Old behavior</span></span>

<span data-ttu-id="43ef0-107">Os aplicativos `Microsoft.AspNetCore.All` podem usar o `Microsoft.AspNetCore.All` metapacote para segmentar a estrutura compartilhada no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43ef0-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="43ef0-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="43ef0-108">New behavior</span></span>

<span data-ttu-id="43ef0-109">O .NET Core 3.0 `Microsoft.AspNetCore.All` não inclui uma estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="43ef0-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="43ef0-110">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="43ef0-110">Reason for change</span></span>

<span data-ttu-id="43ef0-111">O `Microsoft.AspNetCore.All` metapacote incluiu um grande número de dependências externas.</span><span class="sxs-lookup"><span data-stu-id="43ef0-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="43ef0-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="43ef0-112">Recommended action</span></span>

<span data-ttu-id="43ef0-113">Migre seu projeto `Microsoft.AspNetCore.App` para usar a estrutura.</span><span class="sxs-lookup"><span data-stu-id="43ef0-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="43ef0-114">Os componentes que estavam disponíveis anteriormente ainda `Microsoft.AspNetCore.All` estão disponíveis no NuGet.</span><span class="sxs-lookup"><span data-stu-id="43ef0-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="43ef0-115">Esses componentes agora são implantados com seu aplicativo em vez de serem incluídos na estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="43ef0-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="43ef0-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="43ef0-116">Category</span></span>

<span data-ttu-id="43ef0-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43ef0-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="43ef0-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="43ef0-118">Affected APIs</span></span>

<span data-ttu-id="43ef0-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="43ef0-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
