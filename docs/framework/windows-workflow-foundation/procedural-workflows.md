---
title: Fluxos de trabalho procedurais
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10cf83264fbdc2ed3dc088c11865c630c0b8f4f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="procedural-workflows"></a><span data-ttu-id="00bfe-102">Fluxos de trabalho procedurais</span><span class="sxs-lookup"><span data-stu-id="00bfe-102">Procedural Workflows</span></span>
<span data-ttu-id="00bfe-103">Fluxos de trabalho procedurais usam métodos de controle de fluxo semelhantes a esses elementos encontrados em idiomas procedurais.</span><span class="sxs-lookup"><span data-stu-id="00bfe-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="00bfe-104">Essas construções incluem `While` e `If`.</span><span class="sxs-lookup"><span data-stu-id="00bfe-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="00bfe-105">Esses fluxos de trabalho podem ser compostos livremente usando outras atividades de controle de fluxo como <xref:System.Activities.Statements.Flowchart> e <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="00bfe-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="00bfe-106">Fluxo de controle de execução</span><span class="sxs-lookup"><span data-stu-id="00bfe-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="00bfe-107">A biblioteca de atividade de fluxo de trabalho tem atividades para modelar a maioria dos métodos de controle de fluxo usados em idiomas procedurais.</span><span class="sxs-lookup"><span data-stu-id="00bfe-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="00bfe-108">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="00bfe-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="00bfe-109">Para usar atividades de fluxo de controle, arraste e solte-os do **atividade** caixa de ferramentas em uma atividade composta dentro da janela do designer.</span><span class="sxs-lookup"><span data-stu-id="00bfe-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00bfe-110">Se usando [!INCLUDE[dublin](../../../includes/dublin-md.md)] para hospedar fluxos de trabalho em uma Web farm, AppFabric moverá instâncias entre servidores diferentes de AppFabric.</span><span class="sxs-lookup"><span data-stu-id="00bfe-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="00bfe-111">Isso requer que os recursos podem ser compartilhado entre todos os nós.</span><span class="sxs-lookup"><span data-stu-id="00bfe-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="00bfe-112">Nenhuma das atividades padrão de fluxo de trabalho de REDE 4 contêm todas as operações que acessam recursos locais.</span><span class="sxs-lookup"><span data-stu-id="00bfe-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="00bfe-113">Desde que AppFabric não oferece nenhum mecanismo marcar um fluxo de trabalho ainda, como um desenvolvedor não deve criar as atividades personalizados que elas falham quando um fluxo de trabalho é movido.</span><span class="sxs-lookup"><span data-stu-id="00bfe-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bfe-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00bfe-114">See Also</span></span>  
 [<span data-ttu-id="00bfe-115">Fluxos de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="00bfe-115">Flowchart Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
