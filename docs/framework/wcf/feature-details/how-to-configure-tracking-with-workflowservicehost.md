---
title: Como configurar rastreamento com WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185066"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="8eb15-102">Como configurar rastreamento com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="8eb15-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="8eb15-103">Este tópico explica como configurar [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] o rastreamento de <xref:System.ServiceModel.Activities.WorkflowServiceHost>um fluxo de trabalho hospedado em .</span><span class="sxs-lookup"><span data-stu-id="8eb15-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8eb15-104">Ele é configurado através de um arquivo Web.config especificando um comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="8eb15-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="8eb15-105">Configurar rastreamento na configuração</span><span class="sxs-lookup"><span data-stu-id="8eb15-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="8eb15-106">Adicione <xref:System.Activities.Tracking.EtwTrackingParticipant> o uso `behavior` do elemento <> em um arquivo de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8eb15-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="8eb15-107">A amostra de configuração anterior está usando configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="8eb15-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8eb15-108">Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="8eb15-109">A amostra de <xref:System.Activities.Tracking.EtwTrackingParticipant> configuração anterior adiciona a e especifica um nome de perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8eb15-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8eb15-110">Os perfis de rastreamento são `trackingProfile` criados em `tracking` um elemento> <dentro de um elemento> <.</span><span class="sxs-lookup"><span data-stu-id="8eb15-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="8eb15-111">O perfil de rastreamento contém consultas de rastreamento que permitem que um participante de rastreamento se inscreva em eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8eb15-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="8eb15-112">O exemplo a seguir mostra como criar um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8eb15-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="8eb15-113">Para obter mais informações sobre o rastreamento de perfis, consulte [Perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="8eb15-114">Para obter mais informações sobre rastreamento em geral, consulte [Workflow Tracking and Ttracking](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="8eb15-115">Configurar rastreamento em código</span><span class="sxs-lookup"><span data-stu-id="8eb15-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="8eb15-116">Adicione <xref:System.Activities.Tracking.EtwTrackingParticipant> o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> uso do comportamento em código, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8eb15-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="8eb15-117">A amostra de <xref:System.Activities.Tracking.EtwTrackingParticipant> código anterior adiciona a e especifica um nome de perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8eb15-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8eb15-118">Os perfis de rastreamento são `trackingProfile` criados em `tracking` um elemento <> dentro de um elemento <> como mostrado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="8eb15-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="8eb15-119">Para obter mais informações sobre o rastreamento de perfis, consulte [Perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="8eb15-120">Para obter mais informações sobre rastreamento em geral, consulte [Workflow Tracking and Ttracking](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="8eb15-121">Para um exemplo de configuração de rastreamento programática, consulte [Configuração de rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb15-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="8eb15-122">See also</span></span>

- [<span data-ttu-id="8eb15-123">Configuração simplificada para serviços WCF</span><span class="sxs-lookup"><span data-stu-id="8eb15-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="8eb15-124">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb15-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="8eb15-125">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8eb15-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
