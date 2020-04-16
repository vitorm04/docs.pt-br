---
title: Como configurar rastreamento com WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 3f78b77849d6da7dfff3bdcba90bb4d5200186a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464150"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Como configurar rastreamento com WorkflowServiceHost
Este tópico explica como configurar [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] o rastreamento de <xref:System.ServiceModel.Activities.WorkflowServiceHost>um fluxo de trabalho hospedado em . Ele é configurado através de um arquivo Web.config especificando um comportamento de serviço.  
  
### <a name="configure-tracking-in-configuration"></a>Configurar rastreamento na configuração  
  
1. Adicione <xref:System.Activities.Tracking.EtwTrackingParticipant> o uso `behavior` do elemento <> em um arquivo de configuração, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > A amostra de configuração anterior está usando configuração simplificada. Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     A amostra de <xref:System.Activities.Tracking.EtwTrackingParticipant> configuração anterior adiciona a e especifica um nome de perfil de rastreamento. Os perfis de rastreamento são `trackingProfile` criados em `tracking` um elemento> <dentro de um elemento> <. O perfil de rastreamento contém consultas de rastreamento que permitem que um participante de rastreamento se inscreva em eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução. O exemplo a seguir mostra como criar um perfil de rastreamento.  
  
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
  
     Para obter mais informações sobre o rastreamento de perfis, consulte [Perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obter mais informações sobre rastreamento em geral, consulte [Workflow Tracking and Ttracking](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurar rastreamento em código  
  
1. Adicione <xref:System.Activities.Tracking.EtwTrackingParticipant> o <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> uso do comportamento em código, como mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     A amostra de <xref:System.Activities.Tracking.EtwTrackingParticipant> código anterior adiciona a e especifica um nome de perfil de rastreamento. Os perfis de rastreamento são `trackingProfile` criados em `tracking` um elemento <> dentro de um elemento <> como mostrado na seção anterior.  
  
     Para obter mais informações sobre o rastreamento de perfis, consulte [Perfis de rastreamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obter mais informações sobre rastreamento em geral, consulte [Workflow Tracking and Ttracking](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Para um exemplo de configuração de rastreamento programática, consulte [Configuração de rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Confira também

- [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Acompanhando perfis](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
