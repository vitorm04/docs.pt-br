---
title: Atividades do computador de estado em WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 78727bab0102909e9f1e479210cf4b42801aa3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="state-machine-activities-in-wf"></a>Atividades do computador de estado em WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fornece vários sistema forneceu atividades e designer de atividade criando fluxos de trabalho do computador de estado.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Executes continha atividades usando o paradigma familiar do computador de estado.|  
|<xref:System.Activities.Statements.State>|Representa um estado em uma máquina de estado.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Representa um estado de terminação em um computador de estado. <xref:System.Activities.Core.Presentation.FinalState> é um designer de atividade que quando usado criar <xref:System.Activities.Statements.State> pré-configurado como um estado de terminação. Para obter mais informações, consulte [Designer de atividade de FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Representa a transição entre dois estados. Não há nenhum **caixa de ferramentas** item para <xref:System.Activities.Statements.Transition>; transições são criadas no designer de fluxo de trabalho arrastando e soltando uma linha entre dois estados ou descartando um estado de triângulos que aparecem quando um estado é colocado em detrimento de outro . Para obter mais informações, consulte [Designer de atividade de transição](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
