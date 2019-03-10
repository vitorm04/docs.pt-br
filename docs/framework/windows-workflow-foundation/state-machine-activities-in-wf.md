---
title: Atividades do computador de estado em WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: eee507f873cde3aabce09c9b3fdb1620cd79fdab
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710310"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="30b20-102">Atividades do computador de estado em WF</span><span class="sxs-lookup"><span data-stu-id="30b20-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="30b20-103">fornece vários sistema forneceu atividades e designer de atividade criando fluxos de trabalho do computador de estado.</span><span class="sxs-lookup"><span data-stu-id="30b20-103">provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="30b20-104">Executes continha atividades usando o paradigma familiar do computador de estado.</span><span class="sxs-lookup"><span data-stu-id="30b20-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="30b20-105">Representa um estado em uma máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="30b20-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="30b20-106">Representa um estado de terminação em um computador de estado.</span><span class="sxs-lookup"><span data-stu-id="30b20-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="30b20-107"><xref:System.Activities.Core.Presentation.FinalState> é um designer de atividade que quando usado criar <xref:System.Activities.Statements.State> pré-configurado como um estado de terminação.</span><span class="sxs-lookup"><span data-stu-id="30b20-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="30b20-108">Para obter mais informações, consulte [Designer de atividade de FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="30b20-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="30b20-109">Representa a transição entre dois estados.</span><span class="sxs-lookup"><span data-stu-id="30b20-109">Represents the transition between two states.</span></span> <span data-ttu-id="30b20-110">Não há nenhuma **caixa de ferramentas** item para <xref:System.Activities.Statements.Transition>; as transições são criados no designer de fluxo de trabalho arrastando e soltando uma linha entre dois estados, ou soltando um estado em triângulos que aparecem quando um estado é focalizado sobre outro .</span><span class="sxs-lookup"><span data-stu-id="30b20-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="30b20-111">Para obter mais informações, consulte [Designer de atividade Transition](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="30b20-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30b20-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30b20-112">See also</span></span>
- [<span data-ttu-id="30b20-113">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="30b20-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
