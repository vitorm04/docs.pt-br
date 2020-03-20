---
title: Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185320"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite especificar a ação a ser tomada se <xref:System.ServiceModel.Activities.WorkflowServiceHost>uma exceção não tratada ocorrer dentro de um fluxo de trabalho hospedado em . Este tópico mostra como configurar esse comportamento em um arquivo de configuração.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Para configurar workflowUnhandledExceptionBehavior  
  
1. Adicione um `workflowUnhandledException` elemento <`behavior`> em um `serviceBehaviors` elemento> `action` <dentro de um elemento> <, usando o atributo para especificar a ação a ser tomada quando uma exceção não manuseada ocorre como mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > A amostra de configuração anterior está usando configuração simplificada. Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Esse comportamento pode ser configurado em código, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     O `action` atributo `workflowUnhandledException` do elemento> <pode ser definido como um dos seguintes valores:  
  
     **Abandonar**  
     Aborta a instância na memória sem tocar no estado de instância persistida (ou seja, reverter para o último ponto de persistência).  
  
     **abandonaresuspender**  
     Aborta a instância na memória e atualiza a instância persistida a ser suspensa.  
  
     **Cancelar**  
     Chama os manipuladores de cancelamento, por exemplo, e depois completa a instância na memória, que também pode removê-la do armazenamento de ocorrências  
  
     **Terminar**  
     Completa a ocorrência na memória e a remove do armazenamento de instâncias.  
  
     Para obter <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>mais informações sobre, consulte [Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)Host de serviço de fluxo de trabalho .  
  
## <a name="see-also"></a>Confira também

- [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
