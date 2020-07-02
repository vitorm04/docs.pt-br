---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615594"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a><span data-ttu-id="d7a64-101">A compilação de um edmx do Entity Framework com o Visual Studio 2013 pode falhar com o erro MSB4062 se estiver usando as tarefas EntityDeploySplit ou EntityClean</span><span class="sxs-lookup"><span data-stu-id="d7a64-101">Building an Entity Framework edmx with Visual Studio 2013 can fail with error MSB4062 if using the EntityDeploySplit or EntityClean tasks</span></span>

#### <a name="details"></a><span data-ttu-id="d7a64-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d7a64-102">Details</span></span>

<span data-ttu-id="d7a64-103">As ferramentas do MSBuild 12.0 (incluídas no Visual Studio 2013) alteraram os locais do arquivo MSBuild, fazendo com que arquivos de destino do Entity Framework sejam inválidos.</span><span class="sxs-lookup"><span data-stu-id="d7a64-103">MSBuild 12.0 tools (included in Visual Studio 2013) changed MSBuild file locations, causing older Entity Framework targets files to be invalid.</span></span> <span data-ttu-id="d7a64-104">O resultado é que as tarefas `EntityDeploySplit` e `EntityClean` falham porque não conseguem localizar `Microsoft.Data.Entity.Build.Tasks.dll`.</span><span class="sxs-lookup"><span data-stu-id="d7a64-104">The result is that `EntityDeploySplit` and `EntityClean` tasks fail because they are unable to find `Microsoft.Data.Entity.Build.Tasks.dll`.</span></span> <span data-ttu-id="d7a64-105">Observe que essa interrupção se deve a uma alteração no conjunto de ferramentas (MSBuild/VS), e não por uma mudança no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7a64-105">Note that this break is because of a toolset (MSBuild/VS) change, not because of a .NET Framework change.</span></span> <span data-ttu-id="d7a64-106">Ela ocorrerá apenas no upgrade das ferramentas do desenvolvedor, não simplesmente no upgrade do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7a64-106">It will only occur when upgrading developer tools, not when merely upgrading the .NET Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d7a64-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="d7a64-107">Suggestion</span></span>

<span data-ttu-id="d7a64-108">Os arquivos de destino do Entity Framework foram corrigidos para trabalhar com o novo layout do MSBuild a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="d7a64-108">Entity Framework targets files are fixed to work with the new MSBuild layout beginning in the .NET Framework 4.6.</span></span> <span data-ttu-id="d7a64-109">O upgrade para essa versão do Framework corrigirá esse problema.</span><span class="sxs-lookup"><span data-stu-id="d7a64-109">Upgrading to that version of the Framework will fix this issue.</span></span> <span data-ttu-id="d7a64-110">Como alternativa, [esta solução alternativa](https://stackoverflow.com/a/24249247/131944) pode ser usada para aplicar patches diretamente aos arquivos de destino.</span><span class="sxs-lookup"><span data-stu-id="d7a64-110">Alternatively, [this workaround](https://stackoverflow.com/a/24249247/131944) can be used to patch the targets files directly.</span></span>

| <span data-ttu-id="d7a64-111">Name</span><span class="sxs-lookup"><span data-stu-id="d7a64-111">Name</span></span>    | <span data-ttu-id="d7a64-112">Valor</span><span class="sxs-lookup"><span data-stu-id="d7a64-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d7a64-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="d7a64-113">Scope</span></span>   | <span data-ttu-id="d7a64-114">Principal</span><span class="sxs-lookup"><span data-stu-id="d7a64-114">Major</span></span>       |
| <span data-ttu-id="d7a64-115">Versão</span><span class="sxs-lookup"><span data-stu-id="d7a64-115">Version</span></span> | <span data-ttu-id="d7a64-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d7a64-116">4.5.1</span></span>       |
| <span data-ttu-id="d7a64-117">Type</span><span class="sxs-lookup"><span data-stu-id="d7a64-117">Type</span></span>    | <span data-ttu-id="d7a64-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="d7a64-118">Retargeting</span></span> |
