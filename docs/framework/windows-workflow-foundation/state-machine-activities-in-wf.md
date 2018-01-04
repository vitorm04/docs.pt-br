---
title: Atividades do computador de estado em WF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62a211b51f37b306ffcc6b3b9a1ac65ccadd9db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="95641-102">Atividades do computador de estado em WF</span><span class="sxs-lookup"><span data-stu-id="95641-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="95641-103"> fornece vários sistema forneceu atividades e designer de atividade criando fluxos de trabalho do computador de estado.</span><span class="sxs-lookup"><span data-stu-id="95641-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="95641-104">Executes continha atividades usando o paradigma familiar do computador de estado.</span><span class="sxs-lookup"><span data-stu-id="95641-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="95641-105">Representa um estado em uma máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="95641-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="95641-106">Representa um estado de terminação em um computador de estado.</span><span class="sxs-lookup"><span data-stu-id="95641-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="95641-107"><xref:System.Activities.Core.Presentation.FinalState> é um designer de atividade que quando usado criar <xref:System.Activities.Statements.State> pré-configurado como um estado de terminação.</span><span class="sxs-lookup"><span data-stu-id="95641-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="95641-108">Para obter mais informações, consulte [Designer de atividade de FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="95641-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="95641-109">Representa a transição entre dois estados.</span><span class="sxs-lookup"><span data-stu-id="95641-109">Represents the transition between two states.</span></span> <span data-ttu-id="95641-110">Não há nenhum **caixa de ferramentas** item para <xref:System.Activities.Statements.Transition>; transições são criadas no designer de fluxo de trabalho arrastando e soltando uma linha entre dois estados ou descartando um estado de triângulos que aparecem quando um estado é colocado em detrimento de outro .</span><span class="sxs-lookup"><span data-stu-id="95641-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="95641-111">Para obter mais informações, consulte [Designer de atividade de transição](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="95641-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95641-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95641-112">See Also</span></span>  
 [<span data-ttu-id="95641-113">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="95641-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
