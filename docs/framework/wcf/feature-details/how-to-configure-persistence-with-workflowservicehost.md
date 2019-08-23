---
title: 'Como: configurar a persistência com WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2cae73bd503afec6ddd1faf435645ebc21f4fc76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968478"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Como: configurar a persistência com WorkflowServiceHost
Este tópico descreve como configurar o recurso de repositório de instância do fluxo de trabalho SQL para habilitar a persistência <xref:System.ServiceModel.Activities.WorkflowServiceHost> para fluxos de trabalho hospedados no usando um arquivo de configuração. Antes de usar o recurso de repositório de instância do fluxo de trabalho SQL, você deve criar um banco de dados SQL que é usado para manter instâncias de fluxo de trabalho. Para obter mais informações, confira [Como: Habilitar persistência de SQL para fluxos de trabalho e](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)serviços de fluxo de trabalho.  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Para configurar o repositório de instância do fluxo de trabalho SQL na configuração  
  
1. As propriedades do armazenamento da instância do fluxo de trabalho SQL podem ser <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>configuradas por meio do, um comportamento de serviço que permite alterar as configurações por meio da configuração de XML. O exemplo de configuração a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho`sqlWorkflowInstanceStore`SQL usando o elemento de comportamento < > em um arquivo de configuração.  
  
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
  
     Para obter mais informações sobre como configurar o repositório de instância do fluxo de [trabalho SQL, consulte Como: Habilitar persistência de SQL para fluxos de trabalho e](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)serviços de fluxo de trabalho. Para obter mais informações sobre as configurações individuais para o`sqlWorkflowInstanceStore`elemento de comportamento < >, consulte [repositório de instâncias de fluxo de trabalho SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). O Windows Server app Fabric fornece seu próprio armazenamento de persistência. Para obter mais informações, consulte [persistência do Windows Server app Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > O exemplo de configuração anterior usa configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Para configurar o repositório de instância do fluxo de trabalho SQL no código  
  
1. As propriedades do armazenamento da instância do fluxo de trabalho SQL podem ser <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>configuradas por meio do, um comportamento de serviço que permite que você altere as configurações por meio de código. O exemplo a seguir mostra como configurar o armazenamento de instância do fluxo de trabalho <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> SQL usando o elemento Behavior em um código  
  
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
  
     Para obter mais informações sobre como configurar o repositório de instância do fluxo de [trabalho SQL, consulte Como: Habilitar persistência de SQL para fluxos de trabalho e](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)serviços de fluxo de trabalho. Para obter mais informações sobre as configurações individuais do <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento, consulte [repositório de instância de fluxo de trabalho SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). O Windows Server app Fabric fornece seu próprio armazenamento de persistência. Para obter mais informações, consulte [persistência do Windows Server app Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > O exemplo de configuração anterior usa configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Para obter um exemplo de como configurar a persistência programaticamente, consulte [como: Habilite a persistência para fluxos de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)e serviços de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Persistência do Windows Server app Fabric](https://go.microsoft.com/fwlink/?LinkId=193121)
