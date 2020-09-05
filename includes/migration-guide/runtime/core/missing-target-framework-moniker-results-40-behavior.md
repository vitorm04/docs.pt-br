---
ms.openlocfilehash: 49740d3b1890d72935e6e329a4f4be836ed70b25
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496248"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="617cc-101">Ausência do Moniker da Estrutura de Destino resulta no comportamento da versão 4.0</span><span class="sxs-lookup"><span data-stu-id="617cc-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="617cc-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="617cc-102">Details</span></span>

<span data-ttu-id="617cc-103">Os aplicativos sem um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> aplicado no nível de assembly serão executados automaticamente usando a semântica (quirks) do .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="617cc-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="617cc-104">Para garantir a alta qualidade, é recomendável que todos os binários sejam explicitamente atribuídos com um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicando a versão do .NET Framework com a qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="617cc-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="617cc-105">Usar um moniker da estrutura de destino em um arquivo de projeto fará com que o MSBuild aplique automaticamente um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="617cc-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="617cc-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="617cc-106">Suggestion</span></span>

<span data-ttu-id="617cc-107">O <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> deve ser fornecido, seja por meio da adição do atributo diretamente ao assembly ou da especificação de uma estrutura de destino no [arquivo de projeto, seja por meio da GUI das propriedades do projeto do Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span><span class="sxs-lookup"><span data-stu-id="617cc-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="617cc-108">Nome</span><span class="sxs-lookup"><span data-stu-id="617cc-108">Name</span></span>    | <span data-ttu-id="617cc-109">Valor</span><span class="sxs-lookup"><span data-stu-id="617cc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="617cc-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="617cc-110">Scope</span></span>   |<span data-ttu-id="617cc-111">Principal</span><span class="sxs-lookup"><span data-stu-id="617cc-111">Major</span></span>|
|<span data-ttu-id="617cc-112">Versão</span><span class="sxs-lookup"><span data-stu-id="617cc-112">Version</span></span>|<span data-ttu-id="617cc-113">4.5</span><span class="sxs-lookup"><span data-stu-id="617cc-113">4.5</span></span>|
|<span data-ttu-id="617cc-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="617cc-114">Type</span></span>|<span data-ttu-id="617cc-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="617cc-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="617cc-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="617cc-116">Affected APIs</span></span>

<span data-ttu-id="617cc-117">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="617cc-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
