---
title: 'Como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: bbbd2e6a5eb3babeb1a4d06976fdefd621581766
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837682"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="21f2c-102">Como: Ativar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="21f2c-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="21f2c-103">Este tópico descreve como configurar o recurso de Store de instância de fluxo de trabalho SQL para ativar persistência para os fluxos de trabalho e fluxo de trabalho serviços de aplicativos por meio e usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="21f2c-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="21f2c-104">A tela de aplicativo Windows Server simplifica o processo de configurar a persistência.</span><span class="sxs-lookup"><span data-stu-id="21f2c-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="21f2c-105">Para obter mais informações, consulte [configuração de persistência do App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="21f2c-105">For more information, see [App Fabric Persistence Configuration](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="21f2c-106">Antes de usar o recurso de Store de instância de fluxo de trabalho SQL, crie um base de dados que o recurso usa para manter instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="21f2c-107">Arquivos de script SQL das cópias do programa de instalação de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] associados com o recurso de Store de instância de fluxo de trabalho SQL ao %WINDIR% \ Microsoft.NET \ Framework \ v4.xxx pasta \ \ EN SQL.</span><span class="sxs-lookup"><span data-stu-id="21f2c-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="21f2c-108">Executar esses arquivos de script em um base de dados SQL Server 2005 ou SQL Server 2008 que você deseja a instância Store de fluxo de trabalho SQL para usar para persistir instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="21f2c-109">Execute o arquivo de SqlWorkflowInstanceStoreSchema.sql primeiro e execute o arquivo de SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="21f2c-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="21f2c-110">Para limpar o base de dados de persistência para ter um base de dados atualizado, executar os scripts em %WINDIR% \ Microsoft.NET \ Framework \ \ \ v4.xxx SQL EN na seguinte ordem.</span><span class="sxs-lookup"><span data-stu-id="21f2c-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="21f2c-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="21f2c-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="21f2c-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="21f2c-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21f2c-113">Se você não criar um base de dados de persistência, o recurso de Store de instância de fluxo de trabalho do SQL gerencie uma exceção similar à seguinte quando um host tenta manter fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="21f2c-114">System.Data.SqlClient.SqlException: Não foi possível encontrar o procedimento armazenado “System.Activities.DurableInstancing.CreateLockOwner”</span><span class="sxs-lookup"><span data-stu-id="21f2c-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="21f2c-115">As seguintes seções descrevem como ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho usando a instância Store de fluxo de trabalho SQL.</span><span class="sxs-lookup"><span data-stu-id="21f2c-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="21f2c-116">Para obter mais informações sobre as propriedades do repositório de instâncias do fluxo de trabalho SQL, consulte [Propriedades do repositório de instâncias do fluxo de trabalho SQL](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="21f2c-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="21f2c-117">Ativando a persistência para fluxos de trabalho são hospedados que usam WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="21f2c-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="21f2c-118">Você pode ativar persistência para fluxos de trabalho são hospedados que usam <xref:System.Activities.WorkflowApplication> programaticamente usando o modelo de objeto de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .</span><span class="sxs-lookup"><span data-stu-id="21f2c-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="21f2c-119">O procedimento a seguir contém as etapas para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="21f2c-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="21f2c-120">Para ativar persistência para fluxos de trabalho são hospedados</span><span class="sxs-lookup"><span data-stu-id="21f2c-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="21f2c-121">Adicione uma referência a System. Activities. DurableInstancing. dll.</span><span class="sxs-lookup"><span data-stu-id="21f2c-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="21f2c-122">Adicione a seguinte declaração na parte superior do arquivo de origem após a existência declarações “using”.</span><span class="sxs-lookup"><span data-stu-id="21f2c-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="21f2c-123">Construir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> e o atribui a <xref:System.Activities.WorkflowApplication.InstanceStore%2A> de <xref:System.Activities.WorkflowApplication> conforme mostrado no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="21f2c-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="21f2c-124">Dependendo de sua edição do SQL Server, o nome do servidor da cadeia de conexão pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="21f2c-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="21f2c-125">Chamar o método de <xref:System.Activities.WorkflowApplication.Persist%2A> no objeto de <xref:System.Activities.WorkflowApplication> para manter um fluxo de trabalho, ou o método de <xref:System.Activities.WorkflowApplication.Unload%2A> para persistir e descarregar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="21f2c-126">Você também pode manipular o evento de <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> gerado pelo objeto de <xref:System.Activities.WorkflowApplication> e retornar<xref:System.Activities.PersistableIdleAction.Persist> (ou <xref:System.Activities.PersistableIdleAction.Unload>) o membro apropriado de <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="21f2c-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="21f2c-127">Consulte a etapa [como: criar e executar um fluxo de trabalho de longa execução](how-to-create-and-run-a-long-running-workflow.md) do [tutorial de introdução](getting-started-tutorial.md) para obter instruções passo a passo.</span><span class="sxs-lookup"><span data-stu-id="21f2c-127">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="21f2c-128">Ativando a persistência para os serviços são hospedados de fluxo de trabalho que usam o WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="21f2c-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="21f2c-129">Você pode ativar persistência para os serviços são hospedados de fluxo de trabalho que usam <xref:System.ServiceModel.WorkflowServiceHost> programaticamente usando a classe de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ou da classe <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> .</span><span class="sxs-lookup"><span data-stu-id="21f2c-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="21f2c-130">Usando a classe de SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="21f2c-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="21f2c-131">O procedimento a seguir contém as etapas para usar a classe de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> para ativar persistência para serviços são hospedados de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="21f2c-132">Para ativar persistência usando SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="21f2c-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="21f2c-133">Adicione uma referência ao System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="21f2c-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="21f2c-134">Adicione a seguinte declaração na parte superior do arquivo de origem após a existência declarações “using”.</span><span class="sxs-lookup"><span data-stu-id="21f2c-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="21f2c-135">Crie uma instância de `WorkflowServiceHost` e adicionar pontos de extremidade para o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="21f2c-136">Criar um objeto de `SqlWorkflowInstanceStoreBehavior` e para definir propriedades do objeto de comportamento.</span><span class="sxs-lookup"><span data-stu-id="21f2c-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="21f2c-137">Abra o host serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21f2c-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="21f2c-138">Usando a propriedade de DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="21f2c-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="21f2c-139">Quando `SqlWorkflowInstanceStoreBehavior` é aplicado, `DurableInstancingOptions.InstanceStore` em `WorkflowServiceHost` está definido para o objeto de `SqlWorkflowInstanceStore` criado usando os valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="21f2c-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="21f2c-140">Você pode fazer o mesmo para definir programaticamente a propriedade de <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> de `WorkflowServiceHost` sem usar a classe de `SqlWorkflowInstanceStoreBehavior` conforme mostrado no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="21f2c-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="21f2c-141">Ativando a persistência para os serviços Estar- hospedados de fluxo de trabalho que usam o WorkflowServiceHost usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="21f2c-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="21f2c-142">Você pode ativar persistência para serviços são hospedados hospedado ou do Windows do processo de ativação de serviço (-) WAS de fluxo de trabalho usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="21f2c-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="21f2c-143">Um serviço Estar- hospedado de fluxo de trabalho usa o WorkflowServiceHost como serviços são hospedados de fluxo de trabalho fazem.</span><span class="sxs-lookup"><span data-stu-id="21f2c-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="21f2c-144">O `SqlWorkflowInstanceStoreBehavior`, um comportamento de serviço que permite alterar convenientemente as propriedades de [armazenamento da instância do fluxo de trabalho SQL](sql-workflow-instance-store.md) por meio da configuração XML.</span><span class="sxs-lookup"><span data-stu-id="21f2c-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="21f2c-145">Para serviços Estar- hospedados de fluxo de trabalho, use o arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="21f2c-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="21f2c-146">O seguinte exemplo de configuração mostra como configurar a instância Store de fluxo de trabalho do SQL usando o elemento do comportamento de `sqlWorkflowInstanceStore` em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="21f2c-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="21f2c-147">Se você não definir valores para `connectionString` ou propriedade de `connectionStringName` , a instância Store de fluxo de trabalho do SQL usa a cadeia de conexão chamado padrão `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="21f2c-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="21f2c-148">Quando `SqlWorkflowInstanceStoreBehavior` é aplicado, `DurableInstancingOptions.InstanceStore` em `WorkflowServiceHost` está definido para o objeto de `SqlWorkflowInstanceStore` criado usando os valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="21f2c-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="21f2c-149">Você pode fazer o mesmo programaticamente para usar `SqlWorkflowInstanceStore` com `WorkflowServiceHost` sem usar o elemento do comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="21f2c-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="21f2c-150">É recomendável que você não armazene informações sigilosas como nomes de usuário e senhas no arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="21f2c-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="21f2c-151">Se você armazenar informações confidenciais no arquivo web.config, você deve proteger o acesso ao arquivo web.config usando listas de controle de acesso (ACLs) do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="21f2c-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="21f2c-152">Além disso, você também pode proteger os valores de configuração em um arquivo de configuração, conforme mencionado na [criptografia de informações de configuração usando a configuração protegida](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="21f2c-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="21f2c-153">Elementos Machine.config relacionados ao recurso de Store de instância de fluxo de trabalho do SQL</span><span class="sxs-lookup"><span data-stu-id="21f2c-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="21f2c-154">A instalação de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] adicione os seguintes elementos relacionados ao recurso de Store de instância de fluxo de trabalho SQL ao arquivo Machine.config:</span><span class="sxs-lookup"><span data-stu-id="21f2c-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="21f2c-155">Adiciona o seguinte elemento de extensão de comportamento ao arquivo Machine. config para que você possa usar o elemento de comportamento de serviço \<sqlWorkflowInstanceStore > no arquivo de configuração para configurar a persistência para seus serviços.</span><span class="sxs-lookup"><span data-stu-id="21f2c-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
