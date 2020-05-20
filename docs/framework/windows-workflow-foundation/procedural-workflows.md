---
title: Fluxos de trabalho procedurais
description: No Workflow Foundation, os fluxos de trabalho de procedimento usam métodos de controle de fluxo semelhantes àqueles encontrados em linguagens de procedimentos.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 97664c1352928e7d05c2ed15fc118dd21474cfc3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421430"
---
# <a name="procedural-workflows"></a><span data-ttu-id="34f08-103">Fluxos de trabalho procedurais</span><span class="sxs-lookup"><span data-stu-id="34f08-103">Procedural Workflows</span></span>
<span data-ttu-id="34f08-104">Fluxos de trabalho procedurais usam métodos de controle de fluxo semelhantes a esses elementos encontrados em idiomas procedurais.</span><span class="sxs-lookup"><span data-stu-id="34f08-104">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="34f08-105">Essas construções incluem `While` e `If`.</span><span class="sxs-lookup"><span data-stu-id="34f08-105">These constructs include `While` and `If`.</span></span> <span data-ttu-id="34f08-106">Esses fluxos de trabalho podem ser compostos livremente usando outras atividades de controle de fluxo como <xref:System.Activities.Statements.Flowchart> e <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="34f08-106">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="34f08-107">Fluxo de controle de execução</span><span class="sxs-lookup"><span data-stu-id="34f08-107">Controlling Execution Flow</span></span>  
 <span data-ttu-id="34f08-108">A biblioteca de atividade de fluxo de trabalho tem atividades para modelar a maioria dos métodos de controle de fluxo usados em idiomas procedurais.</span><span class="sxs-lookup"><span data-stu-id="34f08-108">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="34f08-109">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="34f08-109">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="34f08-110">Para usar as atividades de controle de fluxo, arraste e solte-as da caixa de ferramentas de **atividade** em uma atividade composta dentro da janela do designer.</span><span class="sxs-lookup"><span data-stu-id="34f08-110">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f08-111">Se você estiver usando os recursos de hospedagem do Windows Server AppFabric para hospedar fluxos de trabalho em um Web farm, o AppFabric moverá as instâncias entre diferentes servidores do AppFabric.</span><span class="sxs-lookup"><span data-stu-id="34f08-111">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="34f08-112">Isso requer que os recursos podem ser compartilhado entre todos os nós.</span><span class="sxs-lookup"><span data-stu-id="34f08-112">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="34f08-113">Nenhuma das atividades padrão de fluxo de trabalho de REDE 4 contêm todas as operações que acessam recursos locais.</span><span class="sxs-lookup"><span data-stu-id="34f08-113">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="34f08-114">Desde que AppFabric não oferece nenhum mecanismo marcar um fluxo de trabalho ainda, como um desenvolvedor não deve criar as atividades personalizados que elas falham quando um fluxo de trabalho é movido.</span><span class="sxs-lookup"><span data-stu-id="34f08-114">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f08-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="34f08-115">See also</span></span>

- [<span data-ttu-id="34f08-116">Fluxos de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="34f08-116">Flowchart Workflows</span></span>](flowchart-workflows.md)
