---
title: 'Como: configurar o comportamento ocioso com WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: d3fc95e7e92d3fc7c149790d4af00a464ab427f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164015"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="b7e01-102">Como: configurar o comportamento ocioso com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="b7e01-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="b7e01-103">Fluxos de trabalho ficar ociosos quando encontra um indicador que deve ser retomado por algum estímulo externo, por exemplo, quando a instância de fluxo de trabalho está aguardando que uma mensagem seja entregue usando um <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="b7e01-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> <span data-ttu-id="b7e01-104">é um comportamento que permite que você especifique o tempo entre quando uma instância de serviço fica inativo e quando a instância é persistentes ou descarregada.</span><span class="sxs-lookup"><span data-stu-id="b7e01-104">is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="b7e01-105">Ele contém duas propriedades que permitem que você defina esses intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="b7e01-105">It contains two properties that enable you to set these time spans.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> <span data-ttu-id="b7e01-106">Especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho aparece ociosa e quando a instância do serviço de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="b7e01-106">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> <span data-ttu-id="b7e01-107">Especifica o período de tempo entre quando o fluxo de trabalho de um instância de serviço fica inativo e quando a instância do serviço de fluxo de trabalho é descarregada, onde descarregar significa persistir a instância para o armazenamento de instância e removê-la da memória.</span><span class="sxs-lookup"><span data-stu-id="b7e01-107">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="b7e01-108">Este tópico explica como configurar o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b7e01-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="b7e01-109">Para configurar WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="b7e01-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="b7e01-110">Adicionar um <`workflowIdle`> elemento a ser o <`behavior`> elemento dentro de <`serviceBehaviors`> elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7e01-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="b7e01-111">O `timeToUnload` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho aparece ociosa e quando o serviço de fluxo de trabalho é descarregado.</span><span class="sxs-lookup"><span data-stu-id="b7e01-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="b7e01-112">O `timeToPersist` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho aparece ociosa e quando a instância do serviço de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="b7e01-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="b7e01-113">O valor padrão para `timeToUnload` é de 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="b7e01-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="b7e01-114">O valor padrão para `timeToPersist` é <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="b7e01-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="b7e01-115">Se você quiser manter instâncias ociosas na memória, mas mantê-las para robustez, defina valores para que `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="b7e01-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="b7e01-116">Se você quiser impedir que instâncias ociosas sendo descarregado, defina `timeToUnload` para <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="b7e01-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="b7e01-117">Para obter mais informações sobre <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, consulte [extensibilidade de Host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="b7e01-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7e01-118">O exemplo de configuração anterior está usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="b7e01-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="b7e01-119">Para obter mais informações, consulte [simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b7e01-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="b7e01-120">Para alterar o comportamento ocioso no código</span><span class="sxs-lookup"><span data-stu-id="b7e01-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="b7e01-121">O exemplo a seguir altera o tempo de espera antes de persistir e descarregar programaticamente.</span><span class="sxs-lookup"><span data-stu-id="b7e01-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b7e01-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7e01-122">See also</span></span>

- [<span data-ttu-id="b7e01-123">Extensibilidade de host de serviço do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7e01-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="b7e01-124">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="b7e01-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="b7e01-125">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7e01-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
