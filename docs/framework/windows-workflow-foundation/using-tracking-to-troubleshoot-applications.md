---
title: Usando o controle para solucionar problemas de aplicativos
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: adc9a159b8887b0198cf19891f73fdee2a48437b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="25864-102">Usando o controle para solucionar problemas de aplicativos</span><span class="sxs-lookup"><span data-stu-id="25864-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="25864-103">Windows Workflow Foundation (WF) permite controlar informações relacionadas a fluxo de trabalho para fornecer detalhes de execução de um aplicativo do Windows Workflow Foundation ou o serviço.</span><span class="sxs-lookup"><span data-stu-id="25864-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="25864-104">Hosts do Windows Workflow Foundation são capazes de capturar eventos de fluxo de trabalho durante a execução de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="25864-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="25864-105">Se o fluxo de trabalho gerar falhas ou exceções, você pode usar o Windows Workflow Foundation detalhes de rastreamento para solucionar problemas de seu processamento.</span><span class="sxs-lookup"><span data-stu-id="25864-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="25864-106">Solução de problemas um WF usando o rastreamento de WF</span><span class="sxs-lookup"><span data-stu-id="25864-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="25864-107">Para detectar falhas de processamento de uma atividade do Windows Workflow Foundation, você pode habilitar o controle com um perfil de rastreamento que consulta um <xref:System.Activities.Tracking.ActivityStateRecord> com o estado com falha.</span><span class="sxs-lookup"><span data-stu-id="25864-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="25864-108">A consulta correspondente é especificada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="25864-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="25864-109">Se uma falha é propagada e tratado em um manipulador de falha (como uma atividade de <xref:System.Activities.Statements.TryCatch> ) pode ser detectado usando <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="25864-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="25864-110"><xref:System.Activities.Tracking.FaultPropagationRecord> indica a atividade de origem de falha e o nome do manipulador de falha.</span><span class="sxs-lookup"><span data-stu-id="25864-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="25864-111"><xref:System.Activities.Tracking.FaultPropagationRecord> contém detalhes de falha no formulário da pilha de exceção para a falha. A consulta para assinar <xref:System.Activities.Tracking.FaultPropagationRecord> é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="25864-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="25864-112">Se uma falha não é tratada no fluxo de trabalho resulta em uma exceção não tratada na instância do fluxo de trabalho e a instância de fluxo de trabalho é anulada.</span><span class="sxs-lookup"><span data-stu-id="25864-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="25864-113">Para entender os detalhes da exceção sem tratamento, o perfil de rastreamento deve consultar o registro de instância de fluxo de trabalho com `state name="UnhandledException"` conforme especificado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="25864-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="25864-114">Quando uma instância de fluxo de trabalho encontra uma exceção sem tratamento, um <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objeto é emitido se o controle do Windows Workflow Foundation foi habilitado.</span><span class="sxs-lookup"><span data-stu-id="25864-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="25864-115">Esse registro de rastreamento contém os detalhes de falha na forma da pilha de exceção.</span><span class="sxs-lookup"><span data-stu-id="25864-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="25864-116">Ele tem detalhes da fonte de falha (por exemplo, a atividade) que falha e resultou na exceção não tratada. Para assinar eventos de falha de um Windows Workflow Foundation, habilite o rastreamento adicionando um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="25864-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="25864-117">Configurar esse participante com um perfil de rastreamento que consultas para `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, e `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="25864-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="25864-118">Se você estiver ativado usando o participante de rastreamento de ETW, os eventos de falha são emitidas a uma sessão de ETW.</span><span class="sxs-lookup"><span data-stu-id="25864-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="25864-119">Eventos podem ser exibidos usando o visualizador de eventos do visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="25864-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="25864-120">Isso pode ser encontrado sob o nó **aplicativos -> do Visualizador de eventos e Logs de serviços -> Microsoft -> Windows -> aplicativos de servidor de aplicativo** no canal analítico.</span><span class="sxs-lookup"><span data-stu-id="25864-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25864-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25864-121">See Also</span></span>  
 [<span data-ttu-id="25864-122">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="25864-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="25864-123">Monitoramento de aplicativos com App Fabric</span><span class="sxs-lookup"><span data-stu-id="25864-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
