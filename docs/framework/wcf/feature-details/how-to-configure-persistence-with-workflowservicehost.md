---
title: "Como configurar persistência com WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41211eb1d104e0e540e257cffd4647c6fff9fb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Como configurar persistência com WorkflowServiceHost
Este tópico descreve como configurar o recurso de armazenamento de instância de fluxo de trabalho do SQL para habilitar a persistência para fluxos de trabalho hospedados em <xref:System.ServiceModel.Activities.WorkflowServiceHost> usando um arquivo de configuração. Antes de usar o recurso de armazenamento de instância de fluxo de trabalho do SQL, você deve criar um banco de dados SQL é usado para manter instâncias de fluxo de trabalho. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Para configurar o armazenamento de instância de fluxo de trabalho do SQL na configuração  
  
1.  As propriedades do repositório de instância de fluxo de trabalho SQL podem ser configuradas por meio de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, um comportamento de serviço que permite que você altere as configurações por meio de configuração XML. O exemplo de configuração a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho do SQL usando o <`sqlWorkflowInstanceStore`> elemento de comportamento em um arquivo de configuração.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar o armazenamento de instância de fluxo de trabalho do SQL, consulte [como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]as configurações individuais para o <`sqlWorkflowInstanceStore`> elemento de comportamento, consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric fornece seu próprio repositório de persistência. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Persistência de malha de aplicativos do Windows Server](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  O exemplo de configuração anterior usa a configuração simplificada. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplificado da configuração](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Para configurar o armazenamento de instância de fluxo de trabalho do SQL em código  
  
1.  As propriedades do repositório de instância de fluxo de trabalho SQL podem ser configuradas por meio de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, um comportamento de serviço que permite que você altere as configurações por meio de código. O exemplo a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho do SQL usando o <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento em um código  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar o armazenamento de instância de fluxo de trabalho do SQL, consulte [como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]as configurações individuais para o <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento, consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric fornece seu próprio repositório de persistência. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Persistência de malha de aplicativos do Windows Server](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  O exemplo de configuração anterior usa a configuração simplificada. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplificado da configuração](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Para obter um exemplo de como configurar persistência programaticamente, consulte [como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Persistência de malha de aplicativos do Windows Server](http://go.microsoft.com/fwlink/?LinkId=193121)
