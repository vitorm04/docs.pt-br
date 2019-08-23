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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Como: configurar o acompanhamento com WorkflowServiceHost
Este tópico explica como configurar o acompanhamento de um [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fluxo de trabalho <xref:System.ServiceModel.Activities.WorkflowServiceHost>hospedado no. Ele é configurado por meio de um arquivo Web. config especificando um comportamento de serviço.  
  
### <a name="configure-tracking-in-configuration"></a>Configurar o controle na configuração  
  
1. Adicione o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o elemento`behavior`< > em um arquivo de configuração, conforme mostrado no exemplo a seguir.  
  
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
    > O exemplo de configuração anterior está usando uma configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     O exemplo de configuração anterior adiciona <xref:System.Activities.Tracking.EtwTrackingParticipant> um e especifica um nome de perfil de controle. Os perfis de rastreamento são criados em`trackingProfile`um elemento < > dentro`tracking`de um elemento > <. O perfil de controle contém consultas de acompanhamento que permitem que um participante de controle assine eventos de fluxo de trabalho emitidos quando o estado de uma instância de fluxo de trabalho é alterado no tempo de execução. O exemplo a seguir mostra como criar um perfil de controle.  
  
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
  
     Para obter mais informações sobre perfis de rastreamento, consulte [perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obter mais informações sobre o rastreamento em geral, consulte rastreamento [e acompanhamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurar o acompanhamento no código  
  
1. Adicione o <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> comportamento no código, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     O exemplo de código anterior adiciona <xref:System.Activities.Tracking.EtwTrackingParticipant> um e especifica um nome de perfil de controle. Os perfis de rastreamento são criados em`trackingProfile`um elemento < > dentro`tracking`de um elemento < >, conforme mostrado na seção anterior.  
  
     Para obter mais informações sobre perfis de rastreamento, consulte [perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obter mais informações sobre o rastreamento em geral, consulte rastreamento [e acompanhamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Para obter um exemplo de como configurar o acompanhamento programaticamente, consulte Configurando [o acompanhamento de um fluxo](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
  
## <a name="see-also"></a>Consulte também

- [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Acompanhando perfis](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
