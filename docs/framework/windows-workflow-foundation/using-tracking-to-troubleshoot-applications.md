---
title: Usando o controle para solucionar problemas de aplicativos
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b64b92de9cb36807a2bf1eb7ff57f9f6e1a07156
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988928"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="a2de7-102">Usando o controle para solucionar problemas de aplicativos</span><span class="sxs-lookup"><span data-stu-id="a2de7-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="a2de7-103">Windows Workflow Foundation (WF) permite que você acompanhe informações relacionadas ao fluxo de trabalho para fornecer detalhes sobre a execução de um aplicativo ou serviço Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="a2de7-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="a2de7-104">Windows Workflow Foundation hosts são capazes de capturar eventos de fluxo de trabalho durante a execução de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a2de7-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="a2de7-105">Se o fluxo de trabalho gerar falhas ou exceções, você poderá usar os detalhes de rastreamento de Windows Workflow Foundation para solucionar problemas de processamento.</span><span class="sxs-lookup"><span data-stu-id="a2de7-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="a2de7-106">Solução de problemas um WF usando o rastreamento de WF</span><span class="sxs-lookup"><span data-stu-id="a2de7-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="a2de7-107">Para detectar falhas no processamento de uma atividade de Windows Workflow Foundation, você pode habilitar o acompanhamento com um perfil de controle que consulta um <xref:System.Activities.Tracking.ActivityStateRecord> com o estado de falha.</span><span class="sxs-lookup"><span data-stu-id="a2de7-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="a2de7-108">A consulta correspondente é especificada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a2de7-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="a2de7-109">Se uma falha é propagada e tratado em um manipulador de falha (como uma atividade de <xref:System.Activities.Statements.TryCatch> ) pode ser detectado usando <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="a2de7-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="a2de7-110"><xref:System.Activities.Tracking.FaultPropagationRecord> indica a atividade de origem de falha e o nome do manipulador de falha.</span><span class="sxs-lookup"><span data-stu-id="a2de7-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="a2de7-111">O <xref:System.Activities.Tracking.FaultPropagationRecord> contém detalhes de falha na forma da pilha de exceção para a falha.</span><span class="sxs-lookup"><span data-stu-id="a2de7-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="a2de7-112">A consulta para assinar um <xref:System.Activities.Tracking.FaultPropagationRecord> é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a2de7-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="a2de7-113">Se uma falha não é tratada no fluxo de trabalho resulta em uma exceção não tratada na instância do fluxo de trabalho e a instância de fluxo de trabalho é anulada.</span><span class="sxs-lookup"><span data-stu-id="a2de7-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="a2de7-114">Para entender os detalhes da exceção sem tratamento, o perfil de rastreamento deve consultar o registro de instância do fluxo `state name="UnhandledException"` de trabalho com o, conforme especificado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a2de7-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="a2de7-115">Quando uma instância de fluxo de trabalho encontra uma exceção sem tratamento <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> , um objeto é emitido se o rastreamento de Windows Workflow Foundation tiver sido habilitado.</span><span class="sxs-lookup"><span data-stu-id="a2de7-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="a2de7-116">Esse registro de rastreamento contém os detalhes de falha na forma da pilha de exceção.</span><span class="sxs-lookup"><span data-stu-id="a2de7-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="a2de7-117">Ele tem detalhes da origem da falha (por exemplo, a atividade) que falharam e resultaram na exceção sem tratamento. Para assinar eventos de falha de um Windows Workflow Foundation, habilite o acompanhamento adicionando um participante de controle.</span><span class="sxs-lookup"><span data-stu-id="a2de7-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="a2de7-118">Configurar esse participante com um perfil de rastreamento que consultas para `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, e `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="a2de7-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="a2de7-119">Se você estiver ativado usando o participante de rastreamento de ETW, os eventos de falha são emitidas a uma sessão de ETW.</span><span class="sxs-lookup"><span data-stu-id="a2de7-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="a2de7-120">Eventos podem ser exibidos usando o visualizador de eventos do visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a2de7-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="a2de7-121">Isso pode ser encontrado no nó **Visualizador de eventos-> logs de aplicativos e serviços-> Microsoft-> Windows-> Application Server – Applications** no canal analítico.</span><span class="sxs-lookup"><span data-stu-id="a2de7-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2de7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2de7-122">See also</span></span>

- [<span data-ttu-id="a2de7-123">Monitoramento do Windows Server app Fabric</span><span class="sxs-lookup"><span data-stu-id="a2de7-123">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="a2de7-124">Monitorando aplicativos com o app Fabric</span><span class="sxs-lookup"><span data-stu-id="a2de7-124">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
