---
title: Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5cf06b90169e3915af48396aa2f6c426f1329a95
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite que você especifique a ação a ser tomada se uma exceção não tratada ocorrer dentro de um fluxo de trabalho hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Este tópico mostra como configurar esse comportamento em um arquivo de configuração.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Para configurar WorkflowUnhandledExceptionBehavior  
  
1.  Adicionar um <`workflowUnhandledException`> elemento em um <`behavior`> elemento dentro de um <`serviceBehaviors`> elemento, usando o `action` atributo para especificar a ação a ser tomada quando uma exceção não tratada ocorre conforme mostrado no exemplo a seguir.  
  
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
    >  O exemplo de configuração anterior estiver usando a configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     O `action` atributo do <`workflowUnhandledException`> elemento pode ser definido como um dos seguintes valores:  
  
     **Abandono**  
     Anula a instância na memória sem tocar o estado da instância persistente (isto é, reverter para o último ponto de persistência).  
  
     **abandonAndSuspend**  
     Anula a instância na memória e atualiza a instância persistente para ser suspenso.  
  
     **cancel**  
     Chama manipuladores de cancelamento para a instância e, em seguida, conclui a instância na memória, o que também pode removê-lo do repositório de instância  
  
     **terminate**  
     Conclui a instância na memória e a remove do repositório de instância.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consulte [extensibilidade de Host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
