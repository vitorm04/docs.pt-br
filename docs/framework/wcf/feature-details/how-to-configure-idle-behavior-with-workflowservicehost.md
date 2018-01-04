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
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Como configurar comportamento ocioso com WorkflowServiceHost
Fluxos de trabalho ficar ociosos quando encontra um indicador que deve ser retomado por algum estímulo externo, por exemplo, quando a instância de fluxo de trabalho está aguardando que uma mensagem seja entregue usando um <xref:System.ServiceModel.Activities.Receive> atividade. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>é um comportamento que permite que você especifique o tempo entre quando uma instância de serviço fica ociosa e quando a instância é persistida ou descarregada. Ele contém duas propriedades que permitem definir esses intervalos de tempo. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>Especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é mantida. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>Especifica o período de tempo entre quando um fluxo de trabalho de instância do serviço fica ocioso e quando a instância do serviço de fluxo de trabalho é descarregada, onde unload significa manter a instância para o armazenamento de instância e removê-lo da memória. Este tópico explica como configurar o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> em um arquivo de configuração.  
  
### <a name="to-configure-workflowidlebehavior"></a>Para configurar WorkflowIdleBehavior  
  
1.  Adicionar um <`workflowIdle`> elemento para o <`behavior`> elemento dentro do <`serviceBehaviors`> elemento conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     O `timeToUnload` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando o serviço de fluxo de trabalho é descarregado. O `timeToPersist` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é mantida. O valor padrão para `timeToUnload` é de 1 minuto. O valor padrão para `timeToPersist` é <xref:System.TimeSpan.MaxValue>. Se você quiser manter instâncias ociosas na memória, mas mantê-las para eficiência, defina valores para que `timeToPersist`  <  `timeToUnload`. Se você quiser impedir que instâncias ociosas que está sendo descarregado, defina `timeToUnload` para <xref:System.TimeSpan.MaxValue>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, consulte [extensibilidade de Host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  O exemplo de configuração anterior estiver usando a configuração simplificada. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Para alterar o comportamento ocioso no código  
  
-   O exemplo a seguir altera o tempo de espera antes de persistir e descarregar programaticamente.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
