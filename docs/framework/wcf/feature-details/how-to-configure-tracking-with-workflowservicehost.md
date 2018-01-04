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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b9bba3c589ca0232171bab58c26b19c7312a313
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Como configurar rastreamento com WorkflowServiceHost
Este tópico explica como configurar o controle para um [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fluxo de trabalho hospedados em <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ele é configurado por meio de um arquivo Web. config, especificando um comportamento de serviço.  
  
### <a name="configure-tracking-in-configuration"></a>Configurar o controle de configuração  
  
1.  Adicionar o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <`behavior`> elemento em um arquivo de configuração, conforme mostrado no exemplo a seguir.  
  
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
    >  O exemplo de configuração anterior estiver usando a configuração simplificada. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     O exemplo anterior de configuração adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil. Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento. O perfil de rastreamento contém as consultas de controle que permite que um participante de rastreamento para assinar eventos de fluxo de trabalho que são emitidos quando muda o estado de uma instância de fluxo de trabalho em tempo de execução. O exemplo a seguir mostra como criar um perfil de rastreamento.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Controlando perfis, consulte [perfis controle](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]controle em geral, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurar o controle no código  
  
1.  Adicionar o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> comportamento no código, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     O exemplo de código anterior adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil. Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento conforme mostrado na seção anterior.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Controlando perfis, consulte [perfis controle](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]controle em geral, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Para obter um exemplo de configuração de rastreamento programaticamente, consulte [configurar rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também  
 [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Acompanhando perfis](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
