---
title: Usando o controle para solucionar problemas de aplicativos
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: ee9aaaae80f213f026a222ac1754ae8b4fdf2d37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517037"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Usando o controle para solucionar problemas de aplicativos
Windows Workflow Foundation (WF) permite controlar informações relacionadas a fluxo de trabalho para fornecer detalhes de execução de um aplicativo do Windows Workflow Foundation ou o serviço. Hosts do Windows Workflow Foundation são capazes de capturar eventos de fluxo de trabalho durante a execução de uma instância de fluxo de trabalho. Se o fluxo de trabalho gerar falhas ou exceções, você pode usar o Windows Workflow Foundation detalhes de rastreamento para solucionar problemas de seu processamento.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Solução de problemas um WF usando o rastreamento de WF  
 Para detectar falhas de processamento de uma atividade do Windows Workflow Foundation, você pode habilitar o controle com um perfil de rastreamento que consulta um <xref:System.Activities.Tracking.ActivityStateRecord> com o estado com falha. A consulta correspondente é especificada no código a seguir.  
  
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
  
 Quando uma instância de fluxo de trabalho encontra uma exceção sem tratamento, um <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objeto é emitido se o controle do Windows Workflow Foundation foi habilitado.  
  
 Esse registro de rastreamento contém os detalhes de falha na forma da pilha de exceção. Ele tem detalhes da fonte de falha (por exemplo, a atividade) que falha e resultou na exceção não tratada. Para assinar eventos de falha de um Windows Workflow Foundation, habilite o rastreamento adicionando um participante de rastreamento. Configurar esse participante com um perfil de rastreamento que consultas para `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, e `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Se você estiver ativado usando o participante de rastreamento de ETW, os eventos de falha são emitidas a uma sessão de ETW. Eventos podem ser exibidos usando o visualizador de eventos do visualizador de eventos. Isso pode ser encontrado sob o nó **aplicativos -> do Visualizador de eventos e Logs de serviços -> Microsoft -> Windows -> aplicativos de servidor de aplicativo** no canal analítico.  
  
## <a name="see-also"></a>Consulte também  
 [Monitoramento do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitoramento de aplicativos com App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
