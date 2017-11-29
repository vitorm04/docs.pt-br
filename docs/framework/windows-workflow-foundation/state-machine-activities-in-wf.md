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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5056557c9fee74e9a16b235220c797e1f6356ce3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
