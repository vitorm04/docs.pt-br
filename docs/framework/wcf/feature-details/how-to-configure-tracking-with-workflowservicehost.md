---
title: Como configurar rastreamento com WorkflowServiceHost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a237be3f6e4d59cbaa2d3c0144eaeb4369748ecd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="73819-102">Como configurar rastreamento com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="73819-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="73819-103">Este tópico explica como configurar o controle para um [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fluxo de trabalho hospedados em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="73819-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="73819-104">Ele é configurado por meio de um arquivo Web. config, especificando um comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="73819-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="73819-105">Configurar o controle de configuração</span><span class="sxs-lookup"><span data-stu-id="73819-105">Configure Tracking in Configuration</span></span>  
  
1.  <span data-ttu-id="73819-106">Adicionar o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <`behavior`> elemento em um arquivo de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="73819-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="73819-107">O exemplo de configuração anterior estiver usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="73819-107">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="73819-108">[Simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="73819-108"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="73819-109">O exemplo anterior de configuração adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="73819-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="73819-110">Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento.</span><span class="sxs-lookup"><span data-stu-id="73819-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="73819-111">O perfil de rastreamento contém as consultas de controle que permite que um participante de rastreamento para assinar eventos de fluxo de trabalho que são emitidos quando muda o estado de uma instância de fluxo de trabalho em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="73819-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="73819-112">O exemplo a seguir mostra como criar um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="73819-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="73819-113">Controlando perfis, consulte [perfis controle](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="73819-113"> tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="73819-114">controle em geral, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="73819-114"> tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="73819-115">Configurar o controle no código</span><span class="sxs-lookup"><span data-stu-id="73819-115">Configure Tracking in Code</span></span>  
  
1.  <span data-ttu-id="73819-116">Adicionar o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> comportamento no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="73819-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="73819-117">O exemplo de código anterior adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="73819-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="73819-118">Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento conforme mostrado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="73819-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="73819-119">Controlando perfis, consulte [perfis controle](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="73819-119"> tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="73819-120">controle em geral, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="73819-120"> tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="73819-121">Para obter um exemplo de configuração de rastreamento programaticamente, consulte [configurar rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="73819-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73819-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73819-122">See Also</span></span>  
 [<span data-ttu-id="73819-123">Configuração simplificada para serviços WCF</span><span class="sxs-lookup"><span data-stu-id="73819-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [<span data-ttu-id="73819-124">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="73819-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="73819-125">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="73819-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
