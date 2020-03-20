---
title: Como configurar comportamento ocioso com WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 67be47f97e57792e2f1e14505d3cd121729db33b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185078"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Como configurar comportamento ocioso com WorkflowServiceHost
Os fluxos de trabalho ficam ociosos quando encontram um marcador que deve ser retomado por algum estímulo <xref:System.ServiceModel.Activities.Receive> externo, por exemplo, quando a instância do fluxo de trabalho está esperando que uma mensagem seja entregue usando uma atividade. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>é um comportamento que permite especificar o tempo entre quando uma instância de serviço fica ociosa e quando a instância é persistindo ou descarregada. Ele contém duas propriedades que permitem definir esses intervalos de tempo. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>especifica o intervalo de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância de serviço do fluxo de trabalho é persistiu. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>especifica o intervalo de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância de serviço do fluxo de trabalho é descarregada, onde descarregar significa persistir a instância no armazenamento de instâncias e removê-la da memória. Este tópico explica como <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> configurar o arquivo em um arquivo de configuração.  
  
### <a name="to-configure-workflowidlebehavior"></a>Para configurar workflowIdleBehavior  
  
1. Adicione um `workflowIdle` elemento> `behavior` <ao elemento `serviceBehaviors` <> dentro do elemento> <, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     O `timeToUnload` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando o serviço de fluxo de trabalho é descarregado. O `timeToPersist` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho fica ociosa e quando a instância de serviço do fluxo de trabalho é persistiu. O valor `timeToUnload` padrão é de 1 minuto. O valor padrão para `timeToPersist` é <xref:System.TimeSpan.MaxValue>. Se você quiser manter instâncias ociosas na memória, `timeToPersist`  <  `timeToUnload`mas persista-as para robustez, defina valores para que . Se você quiser evitar que as instâncias ociosas sejam descarregadas, defina-se `timeToUnload` como <xref:System.TimeSpan.MaxValue>. Para obter <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>mais informações sobre, consulte [Extensibilidade do host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > A amostra de configuração anterior está usando configuração simplificada. Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Para alterar o comportamento ocioso em código  
  
- O exemplo a seguir altera o tempo de espera antes de persistir e descarregar programáticamente.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
