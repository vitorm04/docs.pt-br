---
title: 'Como: configurar o acompanhamento com WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: e0631cdb47bc88f7f588f4dfe6c44ea3d44f4e60
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336558"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="e6e30-102">Como: configurar o acompanhamento com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="e6e30-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="e6e30-103">Este tópico explica como configurar o controle para um [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fluxo de trabalho hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e6e30-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="e6e30-104">Ele é configurado por meio de um arquivo Web. config, especificando um comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="e6e30-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="e6e30-105">Configurar o controle na configuração</span><span class="sxs-lookup"><span data-stu-id="e6e30-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="e6e30-106">Adicione a <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <`behavior`> elemento em um arquivo de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6e30-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="e6e30-107">O exemplo de configuração anterior está usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="e6e30-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="e6e30-108">Para obter mais informações, consulte [simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="e6e30-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="e6e30-109">O exemplo de configuração anterior adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="e6e30-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="e6e30-110">Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento.</span><span class="sxs-lookup"><span data-stu-id="e6e30-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="e6e30-111">O perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e6e30-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e6e30-112">O exemplo a seguir mostra como criar um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e6e30-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="e6e30-113">Para obter mais informações sobre perfis de rastreamento, consulte [perfis de acompanhamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e6e30-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="e6e30-114">Para obter mais informações sobre o controle em geral, consulte [fluxo de trabalho, controle e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="e6e30-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="e6e30-115">Configurar o acompanhamento no código</span><span class="sxs-lookup"><span data-stu-id="e6e30-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="e6e30-116">Adicione a <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> comportamento no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6e30-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="e6e30-117">Exemplo de código anterior adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="e6e30-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="e6e30-118">Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento, conforme mostrado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e6e30-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="e6e30-119">Para obter mais informações sobre perfis de rastreamento, consulte [perfis de acompanhamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e6e30-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="e6e30-120">Para obter mais informações sobre o controle em geral, consulte [fluxo de trabalho, controle e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="e6e30-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="e6e30-121">Para obter um exemplo de configuração de rastreamento programaticamente, consulte [Configurando o rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e6e30-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e30-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6e30-122">See also</span></span>

- [<span data-ttu-id="e6e30-123">Configuração simplificada para serviços do WCF</span><span class="sxs-lookup"><span data-stu-id="e6e30-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="e6e30-124">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e6e30-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="e6e30-125">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="e6e30-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
