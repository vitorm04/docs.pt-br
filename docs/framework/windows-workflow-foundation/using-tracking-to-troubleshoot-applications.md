---
title: Usando o controle para solucionar problemas de aplicativos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb8971c344ff24120b5f85dceb518b0944bd5feb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Usando o controle para solucionar problemas de aplicativos
[!INCLUDE[wf](../../../includes/wf-md.md)] permite controlar informações fluxo de trabalho- relacionado para fornecer detalhes a execução de um aplicativo ou um serviço de [!INCLUDE[wf2](../../../includes/wf2-md.md)] . hosts de[!INCLUDE[wf2](../../../includes/wf2-md.md)] pode capturar eventos de fluxo de trabalho durante a execução de uma instância de fluxo de trabalho. Se seu fluxo de trabalho gerencia falhas ou exceções, você pode usar [!INCLUDE[wf2](../../../includes/wf2-md.md)] que acompanha detalhes a solucionar seu processamento.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Solução de problemas um WF usando o rastreamento de WF  
 Para detectar falhas dentro do processamento de uma atividade de [!INCLUDE[wf2](../../../includes/wf2-md.md)] , você pode ativar o rastreamento com um perfil de rastreamento que consultas para <xref:System.Activities.Tracking.ActivityStateRecord> com o estado Faulted. A consulta correspondente é especificada no código a seguir.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Se uma falha é propagada e tratado em um manipulador de falha (como uma atividade de <xref:System.Activities.Statements.TryCatch> ) pode ser detectado usando <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> indica a atividade de origem de falha e o nome do manipulador de falha. <xref:System.Activities.Tracking.FaultPropagationRecord> contém detalhes de falha no formulário da pilha de exceção para a falha. A consulta para assinar <xref:System.Activities.Tracking.FaultPropagationRecord> é mostrada no exemplo a seguir.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Se uma falha não é tratada no fluxo de trabalho resulta em uma exceção não tratada na instância do fluxo de trabalho e a instância de fluxo de trabalho é anulada. Para entender os detalhes da exceção sem tratamento, o perfil de rastreamento deve consultar o registro de instância de fluxo de trabalho com `state name="UnhandledException"` conforme especificado no exemplo a seguir.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Quando uma instância de fluxo de trabalho encontra uma exceção não tratada, um objeto de <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> é emitida se deve controlar de [!INCLUDE[wf2](../../../includes/wf2-md.md)] foi ativado.  
  
 Esse registro de rastreamento contém os detalhes de falha na forma da pilha de exceção. Tem detalhes de origem de falha (por exemplo, a atividade) que criticou e fez a exceção não tratada. Para assinar eventos falha de [!INCLUDE[wf2](../../../includes/wf2-md.md)], ative o rastreamento adicionando um participante de rastreamento. Configurar esse participante com um perfil de rastreamento que consultas para `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, e `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Se você estiver ativado usando o participante de rastreamento de ETW, os eventos de falha são emitidas a uma sessão de ETW. Eventos podem ser exibidos usando o visualizador de eventos do visualizador de eventos. Isso pode ser encontrado sob o nó **aplicativos -> do Visualizador de eventos e Logs de serviços -> Microsoft -> Windows -> aplicativos de servidor de aplicativo** no canal analítico.  
  
## <a name="see-also"></a>Consulte também  
 [Monitoramento do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitoramento de aplicativos com App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
