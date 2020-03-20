---
title: Como configurar persistência com WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2974b6bcbb94c5b54d91025aeabe7c2d2e94c7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185048"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Como configurar persistência com WorkflowServiceHost
Este tópico descreve como configurar o recurso SQL Workflow Instance Store para <xref:System.ServiceModel.Activities.WorkflowServiceHost> permitir a persistência de fluxos de trabalho hospedados usando um arquivo de configuração. Antes de usar o recurso SQL Workflow Instance Store, você deve criar um banco de dados SQL que seja usado para persistir instâncias de fluxo de trabalho. Para obter mais informações, consulte [Como: Ativar a persistência do SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Para configurar a configuração de instância do fluxo de trabalho SQL na configuração  
  
1. As propriedades do armazenamento de instância sql de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>fluxo de trabalho podem ser configuradas através do , um comportamento de serviço que permite alterar as configurações através da configuração XML. O exemplo de configuração a seguir mostra como configurar o `sqlWorkflowInstanceStore` armazenamento de instância sql de fluxo de trabalho usando o elemento de comportamento <> em um arquivo de configuração.  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     Para obter mais informações sobre como configurar o armazenamento de instância sql de fluxo de trabalho, consulte [Como: Ativar a persistência do SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Para obter mais informações sobre as `sqlWorkflowInstanceStore` configurações individuais para o elemento de comportamento <>, consulte [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). O Windows Server App Fabric fornece sua própria loja de persistência. Para obter mais informações, consulte [A persistência da malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > O exemplo de configuração anterior usa configuração simplificada. Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Para configurar a loja de instância sql de fluxo de trabalho em código  
  
1. As propriedades do armazenamento de instância sql de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>fluxo de trabalho podem ser configuradas através do , um comportamento de serviço que permite alterar as configurações através do código. O exemplo a seguir mostra como configurar o armazenamento de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> instância sql de fluxo de trabalho usando o elemento de comportamento em um código  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     Para obter mais informações sobre como configurar o armazenamento de instância sql de fluxo de trabalho, consulte [Como: Ativar a persistência do SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Para obter mais informações sobre <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> as configurações individuais para o elemento comportamento, consulte [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). O Windows Server App Fabric fornece sua própria loja de persistência. Para obter mais informações, consulte [A persistência da malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > O exemplo de configuração anterior usa configuração simplificada. Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Para um exemplo de como configurar a persistência programática, consulte [Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Confira também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Persistência da tela de aplicativo Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
