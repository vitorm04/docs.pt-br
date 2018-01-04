---
title: Como configurar comportamento ocioso com WorkflowServiceHost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1a0d0d4a8b99a6c0536bba8371234f8d46bc1dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="7db7f-102">Como configurar comportamento ocioso com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="7db7f-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="7db7f-103">Fluxos de trabalho ficar ociosos quando encontra um indicador que deve ser retomado por algum estímulo externo, por exemplo, quando a instância de fluxo de trabalho está aguardando que uma mensagem seja entregue usando um <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="7db7f-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="7db7f-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>é um comportamento que permite que você especifique o tempo entre quando uma instância de serviço fica ociosa e quando a instância é persistida ou descarregada.</span><span class="sxs-lookup"><span data-stu-id="7db7f-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="7db7f-105">Ele contém duas propriedades que permitem definir esses intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="7db7f-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="7db7f-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>Especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="7db7f-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="7db7f-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>Especifica o período de tempo entre quando um fluxo de trabalho de instância do serviço fica ocioso e quando a instância do serviço de fluxo de trabalho é descarregada, onde unload significa manter a instância para o armazenamento de instância e removê-lo da memória.</span><span class="sxs-lookup"><span data-stu-id="7db7f-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="7db7f-108">Este tópico explica como configurar o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7db7f-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="7db7f-109">Para configurar WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="7db7f-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="7db7f-110">Adicionar um <`workflowIdle`> elemento para o <`behavior`> elemento dentro do <`serviceBehaviors`> elemento conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7db7f-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="7db7f-111">O `timeToUnload` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando o serviço de fluxo de trabalho é descarregado.</span><span class="sxs-lookup"><span data-stu-id="7db7f-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="7db7f-112">O `timeToPersist` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="7db7f-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="7db7f-113">O valor padrão para `timeToUnload` é de 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="7db7f-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="7db7f-114">O valor padrão para `timeToPersist` é <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="7db7f-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="7db7f-115">Se você quiser manter instâncias ociosas na memória, mas mantê-las para eficiência, defina valores para que `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="7db7f-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="7db7f-116">Se você quiser impedir que instâncias ociosas que está sendo descarregado, defina `timeToUnload` para <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="7db7f-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7db7f-117"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, consulte [extensibilidade de Host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="7db7f-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7db7f-118">O exemplo de configuração anterior estiver usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="7db7f-118">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7db7f-119">[Simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7db7f-119"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="7db7f-120">Para alterar o comportamento ocioso no código</span><span class="sxs-lookup"><span data-stu-id="7db7f-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="7db7f-121">O exemplo a seguir altera o tempo de espera antes de persistir e descarregar programaticamente.</span><span class="sxs-lookup"><span data-stu-id="7db7f-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7db7f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7db7f-122">See Also</span></span>  
 [<span data-ttu-id="7db7f-123">Extensibilidade de host de serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7db7f-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="7db7f-124">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="7db7f-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="7db7f-125">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7db7f-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
