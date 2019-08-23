---
title: 'Como: configurar o acompanhamento com WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968499"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="723d5-102">Como: configurar o acompanhamento com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="723d5-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="723d5-103">Este tópico explica como configurar o acompanhamento de um [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fluxo de trabalho <xref:System.ServiceModel.Activities.WorkflowServiceHost>hospedado no.</span><span class="sxs-lookup"><span data-stu-id="723d5-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="723d5-104">Ele é configurado por meio de um arquivo Web. config especificando um comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="723d5-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="723d5-105">Configurar o controle na configuração</span><span class="sxs-lookup"><span data-stu-id="723d5-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="723d5-106">Adicione o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o elemento`behavior`< > em um arquivo de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="723d5-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="723d5-107">O exemplo de configuração anterior está usando uma configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="723d5-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="723d5-108">Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="723d5-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="723d5-109">O exemplo de configuração anterior adiciona <xref:System.Activities.Tracking.EtwTrackingParticipant> um e especifica um nome de perfil de controle.</span><span class="sxs-lookup"><span data-stu-id="723d5-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="723d5-110">Os perfis de rastreamento são criados em`trackingProfile`um elemento < > dentro`tracking`de um elemento > <.</span><span class="sxs-lookup"><span data-stu-id="723d5-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="723d5-111">O perfil de controle contém consultas de acompanhamento que permitem que um participante de controle assine eventos de fluxo de trabalho emitidos quando o estado de uma instância de fluxo de trabalho é alterado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="723d5-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="723d5-112">O exemplo a seguir mostra como criar um perfil de controle.</span><span class="sxs-lookup"><span data-stu-id="723d5-112">The following example shows how to create a tracking profile.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="723d5-113">Para obter mais informações sobre perfis de rastreamento, consulte [perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="723d5-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="723d5-114">Para obter mais informações sobre o rastreamento em geral, consulte rastreamento [e acompanhamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="723d5-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="723d5-115">Configurar o acompanhamento no código</span><span class="sxs-lookup"><span data-stu-id="723d5-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="723d5-116">Adicione o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> comportamento no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="723d5-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="723d5-117">O exemplo de código anterior adiciona <xref:System.Activities.Tracking.EtwTrackingParticipant> um e especifica um nome de perfil de controle.</span><span class="sxs-lookup"><span data-stu-id="723d5-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="723d5-118">Os perfis de rastreamento são criados em`trackingProfile`um elemento < > dentro`tracking`de um elemento < >, conforme mostrado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="723d5-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="723d5-119">Para obter mais informações sobre perfis de rastreamento, consulte [perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="723d5-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="723d5-120">Para obter mais informações sobre o rastreamento em geral, consulte rastreamento [e acompanhamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="723d5-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="723d5-121">Para obter um exemplo de como configurar o acompanhamento programaticamente, consulte Configurando [o acompanhamento de um fluxo](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="723d5-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723d5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="723d5-122">See also</span></span>

- [<span data-ttu-id="723d5-123">Configuração simplificada para serviços WCF</span><span class="sxs-lookup"><span data-stu-id="723d5-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="723d5-124">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="723d5-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="723d5-125">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="723d5-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
