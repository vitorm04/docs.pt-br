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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Como: configurar o acompanhamento com WorkflowServiceHost
Este tópico explica como configurar o controle para um [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fluxo de trabalho hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ele é configurado por meio de um arquivo Web. config, especificando um comportamento de serviço.  
  
### <a name="configure-tracking-in-configuration"></a>Configurar o controle na configuração  
  
1. Adicione a <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <`behavior`> elemento em um arquivo de configuração, conforme mostrado no exemplo a seguir.  
  
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
    >  O exemplo de configuração anterior está usando a configuração simplificada. Para obter mais informações, consulte [simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     O exemplo de configuração anterior adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil. Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento. O perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução. O exemplo a seguir mostra como criar um perfil de rastreamento.  
  
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
  
     Para obter mais informações sobre perfis de rastreamento, consulte [perfis de acompanhamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obter mais informações sobre o controle em geral, consulte [fluxo de trabalho, controle e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurar o acompanhamento no código  
  
1. Adicione a <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> comportamento no código, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Exemplo de código anterior adiciona um <xref:System.Activities.Tracking.EtwTrackingParticipant> e especifica um controle de nome do perfil. Perfis de rastreamento são criados em um <`trackingProfile`> elemento dentro de um <`tracking`> elemento, conforme mostrado na seção anterior.  
  
     Para obter mais informações sobre perfis de rastreamento, consulte [perfis de acompanhamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obter mais informações sobre o controle em geral, consulte [fluxo de trabalho, controle e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Para obter um exemplo de configuração de rastreamento programaticamente, consulte [Configurando o rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também

- [Configuração simplificada para serviços do WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Controlando perfis](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
