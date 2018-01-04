---
title: "Visão geral de fluxo de trabalho do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dce6962feb0f425958f89182ee7695332389b567
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-overview"></a>Visão geral de fluxo de trabalho do Windows
Um fluxo de trabalho é um conjunto de unidades elementares chamado *atividades* que são armazenados como um modelo que descreve um processo do mundo real. Fluxos de trabalho fornecem uma maneira de descrever a ordem de relações de execução e dependentes entre partes de trabalho ou longo tempo. Este trabalho passa pelo modelo do início ao final, e as atividades podem ser executadas por pessoas ou funções do sistema.  
  
## <a name="workflow-run-time-engine"></a>Mecanismo de fluxo de trabalho  
 Cada instância em execução de fluxo de trabalho é criado e mantido por um mecanismo em processo de tempo de execução que o processo host interage com o direto do seguinte:  
  
-   <xref:System.Activities.WorkflowInvoker>, que chama o fluxo de trabalho como um método.  
  
-   <xref:System.Activities.WorkflowApplication> para o controle explícito sobre a execução de uma única instância de fluxo de trabalho.  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> para interações mensagem- com base em cenários de várias instâncias.  
  
 Cada uma dessas classes envolve o tempo de execução de atividade de núcleo representado como <xref:System.Activities.ActivityInstance> responsável pela atividade de execução. Pode haver vários objetos de <xref:System.Activities.ActivityInstance> dentro de um domínio de aplicativo executando simultaneamente.  
  
 Cada um dos três objetos de precedência de interação host é criado de uma árvore de atividades conhecido como um programa de fluxo de trabalho. Usando esses tipos ou host personalizado que quebra <xref:System.Activities.ActivityInstance>, os fluxos de trabalho podem ser executados em qualquer processo do Windows que inclui aplicativos de console, aplicativos com base em formulários, Serviços do Windows, sites de [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] , e serviços de [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
 ![Componentes de fluxo de trabalho no processo de host](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Componentes de fluxo de trabalho no processo do host  
  
## <a name="interaction-between-workflow-components"></a>Interação entre componentes de fluxo de trabalho  
 O diagrama a seguir demonstra como os componentes de fluxo de trabalho interagem um com o outro.  
  
 ![Interação de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 No diagrama anterior, o método de <xref:System.Activities.WorkflowInvoker.Invoke%2A> da classe de <xref:System.Activities.WorkflowInvoker> é usado para chamar várias instâncias de fluxo de trabalho. <xref:System.Activities.WorkflowInvoker> é usado para fluxos de trabalho leve que não precisam o gerenciamento de host; fluxos de trabalho que precisam o gerenciamento de host (como a ressunção de <xref:System.Activities.Bookmark> ) devem ser executados usando <xref:System.Activities.WorkflowApplication.Run%2A> em vez disso. Não é necessário esperar uma instância de fluxo de trabalho para terminar antes de chamar outra; suporte de mecanismo de tempo de execução que executam várias o fluxo de trabalho instância como exemplo simultaneamente.  Fluxos de trabalho são chamados como segue:  
  
-   Uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma atividade do filho de <xref:System.Activities.Statements.WriteLine> . <xref:System.Activities.Variable> de atividade pai é associado a <xref:System.Activities.InArgument> de atividade filho. [!INCLUDE[crabout](../../../includes/crabout-md.md)]sobre variáveis, argumentos e associação, consulte [variáveis e argumentos](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
-   Uma atividade `ReadLine`personalizado chamado. <xref:System.Activities.OutArgument> de atividade de `ReadLine` é retornado para o método chamando de <xref:System.Activities.WorkflowInvoker.Invoke%2A> .  
  
-   Uma atividade personalizada que derive da classe abstrata de <xref:System.Activities.CodeActivity> . <xref:System.Activities.CodeActivity> pode acessar os recursos de tempo de execução (como o rastreamento e as propriedades) que usam <xref:System.Activities.CodeActivityContext> que está disponível como um parâmetro do método de <xref:System.Activities.CodeActivity.Execute%2A> . [!INCLUDE[crabout](../../../includes/crabout-md.md)]Esses recursos de tempo de execução, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [propriedades de execução de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).  
  
## <a name="see-also"></a>Consulte também  
 [O BizTalk Server 2006 ou WF? Escolha a ferramenta de fluxo de trabalho para o seu projeto](http://go.microsoft.com/fwlink/?LinkId=154901)
