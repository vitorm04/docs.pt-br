---
title: Como configurar persistência com WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 628a6b57b2d356aadadd96ebec312ef979aca6df
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501623"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Como configurar persistência com WorkflowServiceHost
Este tópico descreve como configurar o recurso de Store de instância de fluxo de trabalho do SQL para habilitar a persistência para fluxos de trabalho hospedados em <xref:System.ServiceModel.Activities.WorkflowServiceHost> usando um arquivo de configuração. Antes de usar o recurso de Store de instância de fluxo de trabalho do SQL, você deve criar um banco de dados SQL é usado para persistir instâncias de fluxo de trabalho. Para obter mais informações, consulte [como: habilitar a persistência do SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Para configurar o Store de instância de fluxo de trabalho do SQL na configuração  
  
1.  As propriedades de instância store de fluxo de trabalho do SQL podem ser configuradas por meio de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, um comportamento de serviço que permite que você altere as configurações por meio de configuração XML. O exemplo de configuração a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho do SQL usando o <`sqlWorkflowInstanceStore`> elemento de comportamento em um arquivo de configuração.  
  
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
  
     Para obter mais informações sobre como configurar o armazenamento de instância de fluxo de trabalho do SQL, consulte [como: habilitar a persistência do SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Para obter mais informações sobre as configurações individuais para o <`sqlWorkflowInstanceStore`> elemento de comportamento, consulte [Store de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server AppFabric fornece seu próprio repositório de persistência. Para obter mais informações, consulte [persistência da tela de aplicativo do Windows Server](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  O exemplo de configuração anterior usa a configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Configurar o Store de instância de fluxo de trabalho do SQL no código  
  
1.  As propriedades de instância store de fluxo de trabalho do SQL podem ser configuradas por meio de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, um comportamento de serviço que permite que você altere as configurações por meio de código. O exemplo a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho do SQL usando o <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento em um código  
  
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
  
     Para obter mais informações sobre como configurar o armazenamento de instância de fluxo de trabalho do SQL, consulte [como: habilitar a persistência do SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Para obter mais informações sobre as configurações individuais para o <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento, consulte [Store de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server AppFabric fornece seu próprio repositório de persistência. Para obter mais informações, consulte [persistência da tela de aplicativo do Windows Server](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  O exemplo de configuração anterior usa a configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Para obter um exemplo de como configurar a persistência de forma programática, consulte [como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Persistência de malha de aplicativos do Windows Server](https://go.microsoft.com/fwlink/?LinkId=193121)
