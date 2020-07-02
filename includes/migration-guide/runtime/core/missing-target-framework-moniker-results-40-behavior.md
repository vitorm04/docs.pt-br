---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619785"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="e883b-101">Ausência do Moniker da Estrutura de Destino resulta no comportamento da versão 4.0</span><span class="sxs-lookup"><span data-stu-id="e883b-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="e883b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e883b-102">Details</span></span>

<span data-ttu-id="e883b-103">Os aplicativos sem um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> aplicado no nível de assembly serão executados automaticamente usando a semântica (quirks) do .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="e883b-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="e883b-104">Para garantir a alta qualidade, é recomendável que todos os binários sejam explicitamente atribuídos com um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicando a versão do .NET Framework com a qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="e883b-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="e883b-105">Usar um moniker da estrutura de destino em um arquivo de projeto fará com que o MSBuild aplique automaticamente um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="e883b-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e883b-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e883b-106">Suggestion</span></span>

<span data-ttu-id="e883b-107">O <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> deve ser fornecido, seja por meio da adição do atributo diretamente ao assembly ou da especificação de uma estrutura de destino no [arquivo de projeto, seja por meio da GUI das propriedades do projeto do Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span><span class="sxs-lookup"><span data-stu-id="e883b-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="e883b-108">Name</span><span class="sxs-lookup"><span data-stu-id="e883b-108">Name</span></span>    | <span data-ttu-id="e883b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="e883b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e883b-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="e883b-110">Scope</span></span>   |<span data-ttu-id="e883b-111">Principal</span><span class="sxs-lookup"><span data-stu-id="e883b-111">Major</span></span>|
|<span data-ttu-id="e883b-112">Versão</span><span class="sxs-lookup"><span data-stu-id="e883b-112">Version</span></span>|<span data-ttu-id="e883b-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e883b-113">4.5</span></span>|
|<span data-ttu-id="e883b-114">Type</span><span class="sxs-lookup"><span data-stu-id="e883b-114">Type</span></span>|<span data-ttu-id="e883b-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="e883b-115">Runtime</span></span>|
