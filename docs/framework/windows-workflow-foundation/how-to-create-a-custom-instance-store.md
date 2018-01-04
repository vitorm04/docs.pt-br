---
title: "Como: Crie uma instância personalizado Store"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db9f09236764697aff4e57ace593827193c6e07d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-instance-store"></a><span data-ttu-id="af998-102">Como: Crie uma instância personalizado Store</span><span class="sxs-lookup"><span data-stu-id="af998-102">How to: Create a Custom Instance Store</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="af998-103"> contém <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, um armazenamento de instância que usa o SQL Server para persistir dados de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af998-103"> contains <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, an instance store that uses SQL Server to persist workflow data.</span></span> <span data-ttu-id="af998-104">Se seu aplicativo é necessário manter dados de fluxo de trabalho para outro meio, como um base de dados diferente ou um sistema de arquivos, você pode implementar um armazenamento personalizado de instância.</span><span class="sxs-lookup"><span data-stu-id="af998-104">If your application is required to persist workflow data to another medium, such as a different database or a file system, you can implement a custom instance store.</span></span> <span data-ttu-id="af998-105">Um armazenamento personalizado de instância é criado estendendo a classe abstrata de <xref:System.Runtime.DurableInstancing.InstanceStore> e implementar métodos que são necessários para a implementação.</span><span class="sxs-lookup"><span data-stu-id="af998-105">A custom instance store is created by extending the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class and implementing the methods that are required for the implementation.</span></span> <span data-ttu-id="af998-106">Para uma implementação completa de um repositório de instância personalizada, consulte o [processo de compra corporativo](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="af998-106">For a complete implementation of a custom instance store, see the [Corporate Purchase Process](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) sample.</span></span>  
  
## <a name="implementing-the-begintrycommand-method"></a><span data-ttu-id="af998-107">Implementando o método de BeginTryCommand</span><span class="sxs-lookup"><span data-stu-id="af998-107">Implementing the BeginTryCommand method</span></span>  
 <span data-ttu-id="af998-108">O <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> é enviado ao armazenamento de instância pelo mecanismo de persistência.</span><span class="sxs-lookup"><span data-stu-id="af998-108">The <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> is sent to the instance store by the persistence engine.</span></span> <span data-ttu-id="af998-109">O tipo de parâmetro de `command` indica que comando está sendo executado; este parâmetro pode ser um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="af998-109">The type of the `command` parameter indicates which command is being executed; this parameter can be of the following types:</span></span>  
  
-   <span data-ttu-id="af998-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: O mecanismo de persistência envia este comando no armazenamento de instância quando um fluxo de trabalho deve ser mantido para o suporte de memória.</span><span class="sxs-lookup"><span data-stu-id="af998-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be persisted to the storage medium.</span></span> <span data-ttu-id="af998-111">Os dados de persistência de fluxo de trabalho são fornecidos para o método no membro de <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> de parâmetro de `command` .</span><span class="sxs-lookup"><span data-stu-id="af998-111">The workflow persistence data is provided to the method in the <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> member of the `command` parameter.</span></span>  
  
-   <span data-ttu-id="af998-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: O mecanismo de persistência envia este comando no armazenamento de instância quando um fluxo de trabalho deve ser carregado suporte de memória.</span><span class="sxs-lookup"><span data-stu-id="af998-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be loaded from the storage medium.</span></span> <span data-ttu-id="af998-113">A identificação de instância de fluxo de trabalho a ser carregado é fornecido para o método no parâmetro de `instanceId` de propriedade de <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> de parâmetro de `context` .</span><span class="sxs-lookup"><span data-stu-id="af998-113">The instance ID of the workflow to be loaded is provided to the method in the `instanceId` parameter of the <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> property of the `context` parameter.</span></span>  
  
-   <span data-ttu-id="af998-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: O mecanismo de persistência envia este comando no armazenamento de instância quando <xref:System.ServiceModel.Activities.WorkflowServiceHost> deve ser registrada como um proprietário de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="af998-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when a <xref:System.ServiceModel.Activities.WorkflowServiceHost> must be registered as a lock owner.</span></span> <span data-ttu-id="af998-115">A identificação de instância de fluxo de trabalho atual deve ser fornecido para o armazenamento de instância usando o método de <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> de parâmetro de `context` .</span><span class="sxs-lookup"><span data-stu-id="af998-115">The instance ID of the current workflow should be provided to the instance store using <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> method of the `context` parameter.</span></span>  
  
     <span data-ttu-id="af998-116">O seguinte trecho de código demonstra como implementar o comando de CreateWorkflowOwner atribuir um proprietário explícito de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="af998-116">The following code snippet demonstrates how to implement the CreateWorkflowOwner command to assign an explicit lock owner.</span></span>  
  
    ```  
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");  
    ...  
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()  
    {  
        InstanceOwnerMetadata =  
        {  
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },  
        }  
    };  
    InstanceHandle ownerHandle = store.CreateInstanceHandle();  
    store.DefaultInstanceOwner = store.Execute(  
                                   ownerHandle,  
                                   createCommand,  
                                   TimeSpan.FromSeconds(30)).InstanceOwner;  
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });  
    ```  
  
-   <span data-ttu-id="af998-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: O mecanismo de persistência envia este comando no armazenamento de instância quando o ID de instância de um proprietário de bloqueio pode ser removido do armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="af998-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when the instance ID of a lock owner can be removed from the instance store.</span></span> <span data-ttu-id="af998-118">Como com <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, a identificação do proprietário de bloqueio deve ser fornecido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af998-118">As with <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, the ID of the lock owner should be provided by the application.</span></span>  
  
     <span data-ttu-id="af998-119">O trecho de código a seguir demonstra como liberar um bloqueio usando <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span><span class="sxs-lookup"><span data-stu-id="af998-119">The following code snippet demonstrates how to release a lock using <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span></span>  
  
    ```  
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)  
    {  
        handle.Free();  
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);  
        try  
        {  
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.  
            Thread.Sleep(10000);  
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));  
        }  
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }  
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }  
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }  
        catch (Exception ex) { Log.Inform(ex.Message); }  
        finally  
        {  
            handle.Free();  
            store.DefaultInstanceOwner = null;  
        }  
    }  
    ```  
  
     <span data-ttu-id="af998-120">O método anterior deve ser chamado em um bloco try/catch quando uma instância filho é executada.</span><span class="sxs-lookup"><span data-stu-id="af998-120">The above method should be called in a Try/Catch block when a child instance is run.</span></span>  
  
    ```  
    try  
    {  
        childInstance.Run();  
    }  
    catch (Exception)  
    {  
        throw ;  
    }  
    finally  
    {  
        FreeHandleAndDeleteOwner(store, ownerHandle);  
    }  
    ```  
  
-   <span data-ttu-id="af998-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: O mecanismo de persistência envia este comando no armazenamento de instância quando uma instância de fluxo de trabalho deve ser carregadas usando a chave de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af998-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: The persistence engine sends this command to the instance store when a workflow instance is to be loaded using the workflow’s instance key.</span></span> <span data-ttu-id="af998-122">A identificação de chave da instância pode ser determinado usando o parâmetro de <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> de comando.</span><span class="sxs-lookup"><span data-stu-id="af998-122">The ID of the instance key can be determined by using the <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parameter of the command.</span></span>  
  
-   <span data-ttu-id="af998-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: O mecanismo de persistência envia este comando no armazenamento de instância recuperar parâmetros de ativação para fluxos de trabalho persistidos para criar um host de fluxo de trabalho que pode carregar em fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af998-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: The persistence engine sends this command to the instance store to retrieve activation parameters for persisted workflows in order to create a workflow host that can then load workflows.</span></span> <span data-ttu-id="af998-124">Este comando é enviado pelo mecanismo em resposta ao armazenamento de instância que aumenta <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> ao host quando encontra uma instância que pode ser ativada.</span><span class="sxs-lookup"><span data-stu-id="af998-124">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> to the host when it locates an instance that can be activated.</span></span> <span data-ttu-id="af998-125">O armazenamento de instância deve ser monitorado para determinar se há fluxos de trabalho que podem ser ativados.</span><span class="sxs-lookup"><span data-stu-id="af998-125">The instance store should be polled to determine if there are workflows that can be activated.</span></span>  
  
-   <span data-ttu-id="af998-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: O mecanismo de persistência envia este comando no armazenamento de instância carregar instâncias praticáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af998-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: The persistence engine sends this command to the instance store to load runnable workflow instances.</span></span> <span data-ttu-id="af998-127">Este comando é enviado pelo mecanismo em resposta ao armazenamento de instância que aumenta <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> ao host quando encontra uma instância que pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="af998-127">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> to the host when it locates an instance that can be run.</span></span> <span data-ttu-id="af998-128">O armazenamento de instância deve pesquisando para fluxos de trabalho que podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="af998-128">The instance store should poll for workflows that can be run.</span></span> <span data-ttu-id="af998-129">O trecho de código a seguir demonstra pesquisando um armazenamento de instância para fluxos de trabalho que podem ser executados ou ativado.</span><span class="sxs-lookup"><span data-stu-id="af998-129">The following code snippet demonstrates polling an instance store for workflows that can be run or activated.</span></span>  
  
    ```  
    public void PollForEvents()  
    {  
        InstanceOwner[] storeOwners = this.GetInstanceOwners();  
  
        foreach (InstanceOwner owner in storeOwners)  
        {  
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))  
            {  
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))  
                {  
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivable);  
                    if (hasRunnable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))  
                {  
                   bool hasActivable = GetActivableEvents(this.StoreId, owner.InstanceOwnerId);  
                   if (hasActivable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="af998-130">No trecho de código anterior, o armazenamento de instância consulta os eventos disponíveis e examina cada um para determinar se ele é um evento de <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> .</span><span class="sxs-lookup"><span data-stu-id="af998-130">In the above code snippet, the instance store queries the events available and examines each one to determine if it is a <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> event.</span></span> <span data-ttu-id="af998-131">Se um for encontrado, o <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> é chamado para sinalizar o host para enviar um comando para o armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="af998-131">If one is found, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> is called to signal the host to send a command to the instance store.</span></span>  <span data-ttu-id="af998-132">O trecho de código a seguir demonstra uma implementação de um manipulador para este comando.</span><span class="sxs-lookup"><span data-stu-id="af998-132">The following code snippet demonstrates an implementation of a handler for this command.</span></span>  
  
    ```  
    If (command is TryLoadRunnableWorkflowCommand)  
    {  
        Owner owner;  
        CheckOwner(context, command.Name, out owner);                          
        // Checking instance.Owner is like an InstanceLockQueryResult.  
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));  
  
        XName ownerService = null;  
        InstanceValue value;  
        Instance runnableInstance = default(Instance);  
        bool foundRunnableInstance = false;  
  
        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);  
        if (value != null && value.Value is XName)  
        {  
            ownerService = (XName)value.Value;  
        }  
  
        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)  
        {  
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)  
            {  
                continue;  
            }  
  
            if (ownerService != null)  
            {  
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);  
                if (value == null || ((XName)value.Value) != ownerService)  
                {  
                    continue;  
                }  
            }  
  
            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);  
            if (value != null && value.Value != null && value.Value is string)  
            {  
                continue;  
            }  
  
            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);  
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")  
            {  
                runnableInstance = instance.Value;  
                foundRunnableInstance = true;  
            }  
  
            if (!foundRunnableInstance)  
            {  
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);  
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)  
                {                          
                    runnableInstance = instance.Value;  
                    foundRunnableInstance = true;  
                }  
            }  
  
            if (foundRunnableInstance)  
            {  
                runnableInstance.LockVersion++;  
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;  
                MemoryStore.instances[instance.Key] = runnableInstance;  
                context.BindInstance(instance.Key);  
                context.BindAcquiredLock(runnableInstance.LockVersion);  
  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)  
                {  
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)  
                {  
                    if (keyEntry.Value.Completed)  
                    {  
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                    else  
                    {  
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                }  
            }  
  
            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);  
            break;  
        }  
    }  
    ```  
  
     <span data-ttu-id="af998-133">No trecho de código anterior, o armazenamento de instância procura pelas instâncias praticáveis.</span><span class="sxs-lookup"><span data-stu-id="af998-133">In the above code snippet, the instance store searches for runnable instances.</span></span> <span data-ttu-id="af998-134">Se uma instância é encontrada, está associado ao contexto de execução e carregado.</span><span class="sxs-lookup"><span data-stu-id="af998-134">If an instance is found, it is bound to the execution context and loaded.</span></span>  
  
## <a name="using-a-custom-instance-store"></a><span data-ttu-id="af998-135">Usando um armazenamento personalizado de instância</span><span class="sxs-lookup"><span data-stu-id="af998-135">Using a custom instance store</span></span>  
 <span data-ttu-id="af998-136">Para implementar um armazenamento personalizado de instância, atribua uma instância da instância a <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, e implementar o método <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="af998-136">To implement a custom instance store, assign an instance of the instance store to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, and implement the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> method.</span></span>  <span data-ttu-id="af998-137">Consulte o [como: criar e executar um fluxo de trabalho de execução longa](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) tutorial para obter informações específicas.</span><span class="sxs-lookup"><span data-stu-id="af998-137">See the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) tutorial for specifics.</span></span>  
  
## <a name="a-sample-instance-store"></a><span data-ttu-id="af998-138">Um armazenamento de instância de exemplo</span><span class="sxs-lookup"><span data-stu-id="af998-138">A sample instance store</span></span>  
 <span data-ttu-id="af998-139">O exemplo de código a seguir é uma implementação de armazenamento de instância completa, obtida de [processo de compra corporativo](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="af998-139">The following code sample is a complete instance store implementation, taken from the [Corporate Purchase Process](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) sample.</span></span> <span data-ttu-id="af998-140">Esse armazenamento de instância persistir dados de fluxo de trabalho a um arquivo XML usando.</span><span class="sxs-lookup"><span data-stu-id="af998-140">This instance store persists workflow data to a file using XML.</span></span>  
  
```  
using System;  
using System.Activities.DurableInstancing;  
using System.Collections.Generic;  
using System.IO;  
using System.Runtime.DurableInstancing;  
using System.Runtime.Serialization;  
using System.ServiceModel.Persistence;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.WF.PurchaseProcess  
{  
  
    public class XmlWorkflowInstanceStore : InstanceStore  
    {  
        Guid ownerInstanceID;  
  
        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())  
        {  
  
        }  
  
        public XmlWorkflowInstanceStore(Guid id)  
        {  
            ownerInstanceID = id;  
        }  
  
        //Synchronous version of the Begin/EndTryCommand functions  
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)  
        {  
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));  
        }  
  
        //The persistence engine will send a variety of commands to the configured InstanceStore,  
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.  
        //This method is where we will handle those commands  
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)  
        {  
            IDictionary<XName, InstanceValue> data = null;  
  
            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle  
            if (command is CreateWorkflowOwnerCommand)  
            {  
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());  
            }  
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key  
            else if (command is SaveWorkflowCommand)  
            {  
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;  
                data = saveCommand.InstanceData;  
  
                Save(data);  
            }  
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle  
            else if (command is LoadWorkflowCommand)  
            {  
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
  
                try  
                {  
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))  
                    {  
                        data = LoadInstanceDataFromFile(inputStream);  
                        //load the data into the persistence Context  
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);  
                    }  
                }  
                catch (Exception exception)  
                {  
                    throw new PersistenceException(exception.Message);  
                }  
            }  
  
            return new CompletedAsyncResult<bool>(true, callback, state);  
        }  
  
        protected override bool EndTryCommand(IAsyncResult result)  
        {  
            return CompletedAsyncResult<bool>.End(result);  
        }  
  
        //Reads data from xml file and creates a dictionary based off of that.  
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)  
        {  
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();  
  
            NetDataContractSerializer s = new NetDataContractSerializer();  
  
            XmlReader rdr = XmlReader.Create(inputStream);  
            XmlDocument doc = new XmlDocument();  
            doc.Load(rdr);  
  
            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");  
            foreach (XmlElement instanceElement in instances)  
            {  
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");  
                XName key = (XName)DeserializeObject(s, keyElement);  
  
                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");  
                object value = DeserializeObject(s, valueElement);  
                InstanceValue instVal = new InstanceValue(value);  
  
                data.Add(key, instVal);  
            }  
  
            return data;  
        }  
  
        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)  
        {  
            object deserializedObject = null;  
  
            MemoryStream stm = new MemoryStream();  
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);  
            element.WriteContentTo(wtr);  
            wtr.Flush();  
            stm.Position = 0;  
  
            deserializedObject = serializer.Deserialize(stm);  
  
            return deserializedObject;  
        }  
  
        //Saves the persistence data to an xml file.  
        void Save(IDictionary<XName, InstanceValue> instanceData)  
        {  
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
            XmlDocument doc = new XmlDocument();  
            doc.LoadXml("<InstanceValues/>");  
  
            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)  
            {  
                XmlElement newInstance = doc.CreateElement("InstanceValue");  
  
                XmlElement newKey = SerializeObject("key", valPair.Key, doc);  
                newInstance.AppendChild(newKey);  
  
                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);  
                newInstance.AppendChild(newValue);  
  
                doc.DocumentElement.AppendChild(newInstance);  
            }  
            doc.Save(fileName);  
       }  
  
        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)  
        {  
            NetDataContractSerializer s = new NetDataContractSerializer();  
            XmlElement newElement = doc.CreateElement(elementName);  
            MemoryStream stm = new MemoryStream();  
  
            s.Serialize(stm, o);  
            stm.Position = 0;  
            StreamReader rdr = new StreamReader(stm);  
            newElement.InnerXml = rdr.ReadToEnd();  
  
            return newElement;  
        }  
    }  
}  
```
