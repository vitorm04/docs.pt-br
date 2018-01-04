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
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="92261-102">Como configurar persistência com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="92261-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="92261-103">Este tópico descreve como configurar o recurso de armazenamento de instância de fluxo de trabalho do SQL para habilitar a persistência para fluxos de trabalho hospedados em <xref:System.ServiceModel.Activities.WorkflowServiceHost> usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="92261-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="92261-104">Antes de usar o recurso de armazenamento de instância de fluxo de trabalho do SQL, você deve criar um banco de dados SQL é usado para manter instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="92261-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="92261-105">[Como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="92261-105"> [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="92261-106">Para configurar o armazenamento de instância de fluxo de trabalho do SQL na configuração</span><span class="sxs-lookup"><span data-stu-id="92261-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="92261-107">As propriedades do repositório de instância de fluxo de trabalho SQL podem ser configuradas por meio de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, um comportamento de serviço que permite que você altere as configurações por meio de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="92261-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="92261-108">O exemplo de configuração a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho do SQL usando o <`sqlWorkflowInstanceStore`> elemento de comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="92261-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="92261-109">como configurar o armazenamento de instância de fluxo de trabalho do SQL, consulte [como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="92261-109"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="92261-110">as configurações individuais para o <`sqlWorkflowInstanceStore`> elemento de comportamento, consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="92261-110"> the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="92261-111">Windows Server App Fabric fornece seu próprio repositório de persistência.</span><span class="sxs-lookup"><span data-stu-id="92261-111">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="92261-112">[Persistência de malha de aplicativos do Windows Server](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="92261-112"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92261-113">O exemplo de configuração anterior usa a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="92261-113">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="92261-114">[Simplificado da configuração](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="92261-114"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="92261-115">Para configurar o armazenamento de instância de fluxo de trabalho do SQL em código</span><span class="sxs-lookup"><span data-stu-id="92261-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="92261-116">As propriedades do repositório de instância de fluxo de trabalho SQL podem ser configuradas por meio de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, um comportamento de serviço que permite que você altere as configurações por meio de código.</span><span class="sxs-lookup"><span data-stu-id="92261-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="92261-117">O exemplo a seguir mostra como configurar o armazenamento de instância de fluxo de trabalho do SQL usando o <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento em um código</span><span class="sxs-lookup"><span data-stu-id="92261-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="92261-118">como configurar o armazenamento de instância de fluxo de trabalho do SQL, consulte [como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="92261-118"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="92261-119">as configurações individuais para o <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elemento de comportamento, consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="92261-119"> the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="92261-120">Windows Server App Fabric fornece seu próprio repositório de persistência.</span><span class="sxs-lookup"><span data-stu-id="92261-120">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="92261-121">[Persistência de malha de aplicativos do Windows Server](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="92261-121"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92261-122">O exemplo de configuração anterior usa a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="92261-122">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="92261-123">[Simplificado da configuração](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="92261-123"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="92261-124">Para obter um exemplo de como configurar persistência programaticamente, consulte [como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="92261-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92261-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92261-125">See Also</span></span>  
 [<span data-ttu-id="92261-126">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="92261-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="92261-127">Persistência de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="92261-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="92261-128">Persistência de malha de aplicativos do Windows Server</span><span class="sxs-lookup"><span data-stu-id="92261-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)
