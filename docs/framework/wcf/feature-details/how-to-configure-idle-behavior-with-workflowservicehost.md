---
title: 'Como: configurar o comportamento ocioso com WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: a676f03b4e6f9dd210b843a6f3bf00c735889500
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330149"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Como: configurar o comportamento ocioso com WorkflowServiceHost
Fluxos de trabalho ficar ociosos quando encontra um indicador que deve ser retomado por algum estímulo externo, por exemplo, quando a instância de fluxo de trabalho está aguardando que uma mensagem seja entregue usando um <xref:System.ServiceModel.Activities.Receive> atividade. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> é um comportamento que permite que você especifique o tempo entre quando uma instância de serviço fica inativo e quando a instância é persistentes ou descarregada. Ele contém duas propriedades que permitem que você defina esses intervalos de tempo. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho aparece ociosa e quando a instância do serviço de fluxo de trabalho é mantida. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Especifica o período de tempo entre quando o fluxo de trabalho de um instância de serviço fica inativo e quando a instância do serviço de fluxo de trabalho é descarregada, onde descarregar significa persistir a instância para o armazenamento de instância e removê-la da memória. Este tópico explica como configurar o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> em um arquivo de configuração.  
  
### <a name="to-configure-workflowidlebehavior"></a>Para configurar WorkflowIdleBehavior  
  
1. Adicionar um <`workflowIdle`> elemento a ser o <`behavior`> elemento dentro de <`serviceBehaviors`> elemento, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     O `timeToUnload` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho aparece ociosa e quando o serviço de fluxo de trabalho é descarregado. O `timeToPersist` atributo especifica o período de tempo entre quando uma instância de serviço de fluxo de trabalho aparece ociosa e quando a instância do serviço de fluxo de trabalho é mantida. O valor padrão para `timeToUnload` é de 1 minuto. O valor padrão para `timeToPersist` é <xref:System.TimeSpan.MaxValue>. Se você quiser manter instâncias ociosas na memória, mas mantê-las para robustez, defina valores para que `timeToPersist`  <  `timeToUnload`. Se você quiser impedir que instâncias ociosas sendo descarregado, defina `timeToUnload` para <xref:System.TimeSpan.MaxValue>. Para obter mais informações sobre <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, consulte [extensibilidade de Host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  O exemplo de configuração anterior está usando a configuração simplificada. Para obter mais informações, consulte [simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Para alterar o comportamento ocioso no código  
  
-   O exemplo a seguir altera o tempo de espera antes de persistir e descarregar programaticamente.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
