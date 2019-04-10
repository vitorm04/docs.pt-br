---
title: Inicialização de instancialização
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 1414908025416f4cdd6e5b51c052799631ab52cd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322180"
---
# <a name="instancing-initialization"></a><span data-ttu-id="81c0d-102">Inicialização de instancialização</span><span class="sxs-lookup"><span data-stu-id="81c0d-102">Instancing Initialization</span></span>
<span data-ttu-id="81c0d-103">Este exemplo amplia a [Pooling](../../../../docs/framework/wcf/samples/pooling.md) exemplo definindo uma interface `IObjectControl`, que personaliza a inicialização de um objeto, ativando e desativando-lo.</span><span class="sxs-lookup"><span data-stu-id="81c0d-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="81c0d-104">O cliente invoca métodos que retornam o objeto para o pool e que não retornam o objeto para o pool.</span><span class="sxs-lookup"><span data-stu-id="81c0d-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81c0d-105">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="81c0d-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="81c0d-106">Pontos de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="81c0d-106">Extensibility Points</span></span>  
 <span data-ttu-id="81c0d-107">A primeira etapa na criação de uma extensão do Windows Communication Foundation (WCF) é decidir o ponto de extensibilidade para usar.</span><span class="sxs-lookup"><span data-stu-id="81c0d-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="81c0d-108">No WCF, o termo *EndpointDispatcher* refere-se a um responsável para converter as mensagens de entrada para invocações de método no serviço do usuário e para converter valores de retorno de método em uma mensagem de saída de componente de tempo de execução .</span><span class="sxs-lookup"><span data-stu-id="81c0d-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="81c0d-109">Um serviço WCF cria um EndpointDispatcher para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="81c0d-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="81c0d-110">EndpointDispatcher oferece extensibilidade de escopo (para todas as mensagens recebidas ou enviadas pelo serviço) de ponto de extremidade usando o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> classe.</span><span class="sxs-lookup"><span data-stu-id="81c0d-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="81c0d-111">Essa classe permite que você personalizar várias propriedades que controlam o comportamento do EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="81c0d-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="81c0d-112">Este exemplo destaca o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="81c0d-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="81c0d-113">IInstanceProvider</span></span>  
 <span data-ttu-id="81c0d-114">No WCF, EndpointDispatcher cria instâncias de uma classe de serviço usando um provedor de instância que implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span><span class="sxs-lookup"><span data-stu-id="81c0d-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="81c0d-115">Essa interface tem apenas dois métodos:</span><span class="sxs-lookup"><span data-stu-id="81c0d-115">This interface has only two methods:</span></span>  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A><span data-ttu-id="81c0d-116">: Quando uma mensagem chega, as chamadas de Dispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método para criar uma instância da classe de serviço para processar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="81c0d-116">: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="81c0d-117">A frequência das chamadas para esse método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="81c0d-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="81c0d-118">Por exemplo se o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> estiver definida como <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, uma nova instância da classe de serviço é criada para processar cada mensagem que chega, isso <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> é chamado sempre que uma mensagem chega.</span><span class="sxs-lookup"><span data-stu-id="81c0d-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A><span data-ttu-id="81c0d-119">: Quando a instância de serviço termina de processar a mensagem, EndpointDispatcher chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método.</span><span class="sxs-lookup"><span data-stu-id="81c0d-119">: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="81c0d-120">Como mostra a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, a frequência das chamadas para esse método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="81c0d-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="81c0d-121">O Pool de objetos</span><span class="sxs-lookup"><span data-stu-id="81c0d-121">The Object Pool</span></span>  
 <span data-ttu-id="81c0d-122">O `ObjectPoolInstanceProvider` classe contém a implementação para o pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="81c0d-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="81c0d-123">Essa classe implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface para interagir com a camada de modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="81c0d-124">Quando chama EndpointDispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória.</span><span class="sxs-lookup"><span data-stu-id="81c0d-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="81c0d-125">Se houver um disponível, ele será retornado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-125">If one is available, it is returned.</span></span> <span data-ttu-id="81c0d-126">Caso contrário, `ObjectPoolInstanceProvider` verifica se o `ActiveObjectsCount` propriedade (número de objetos retornados do pool) atingiu o tamanho máximo do pool.</span><span class="sxs-lookup"><span data-stu-id="81c0d-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="81c0d-127">Se não, uma nova instância é criada e retornada ao chamador e `ActiveObjectsCount` subsequentemente é incrementado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="81c0d-128">Caso contrário, uma solicitação de criação do objeto foi enfileirada para um período de tempo configurado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="81c0d-129">A implementação para `GetObjectFromThePool` é mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="81c0d-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="81c0d-130">O custom `ReleaseInstance` implementação adiciona a instância liberada para o pool e diminui a `ActiveObjectsCount` valor.</span><span class="sxs-lookup"><span data-stu-id="81c0d-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="81c0d-131">EndpointDispatcher pode chamar esses métodos de diversos threads e sincronizado, portanto, o acesso a membros de nível de classe no `ObjectPoolInstanceProvider` classe é necessária.</span><span class="sxs-lookup"><span data-stu-id="81c0d-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="81c0d-132">O `ReleaseInstance` método fornece uma *Limpar inicialização* recurso.</span><span class="sxs-lookup"><span data-stu-id="81c0d-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="81c0d-133">Normalmente o pool mantém um número mínimo de objetos para o tempo de vida do pool.</span><span class="sxs-lookup"><span data-stu-id="81c0d-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="81c0d-134">No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para alcançar o limite máximo especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="81c0d-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="81c0d-135">Eventualmente, quando o pool se torna menos ativo esses objetos de excedente podem se tornar uma sobrecarga extra.</span><span class="sxs-lookup"><span data-stu-id="81c0d-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="81c0d-136">Portanto, quando o `activeObjectsCount` chegar a zero um timer de ociosidade é iniciado e que aciona e executa um ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="81c0d-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="81c0d-137">Extensões de camada de ServiceModel são conectadas usando os seguintes comportamentos:</span><span class="sxs-lookup"><span data-stu-id="81c0d-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="81c0d-138">Comportamentos de serviço: Eles permitem a personalização do tempo de execução de todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="81c0d-139">Comportamentos de ponto de extremidade: Eles permitem a personalização de um ponto de extremidade de serviço específico, incluindo EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="81c0d-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
-   <span data-ttu-id="81c0d-140">Comportamentos de contrato: Eles permitem a personalização de um <xref:System.ServiceModel.Dispatcher.ClientRuntime> ou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes no cliente ou o serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
-   <span data-ttu-id="81c0d-141">Comportamentos de operação: Eles permitem a personalização de um <xref:System.ServiceModel.Dispatcher.ClientOperation> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes no cliente ou o serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="81c0d-142">Com a finalidade de um objeto de extensão do pool, um comportamento de ponto de extremidade ou um comportamento de serviço pode ser criado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="81c0d-143">Neste exemplo, usamos um comportamento de serviço, que se aplica a capacidade de cada ponto de extremidade do serviço ao pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="81c0d-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="81c0d-144">Comportamentos de serviço são criados com a implementação de <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span><span class="sxs-lookup"><span data-stu-id="81c0d-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="81c0d-145">Há várias maneiras de tornar o ServiceModel cientes dos comportamentos personalizados:</span><span class="sxs-lookup"><span data-stu-id="81c0d-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="81c0d-146">Usando um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-146">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="81c0d-147">Imperativamente adicionando-o à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="81c0d-148">Estendendo o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="81c0d-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="81c0d-149">Este exemplo usa um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="81c0d-150">Quando o <xref:System.ServiceModel.ServiceHost> é construído, ele examina os atributos usados na definição de tipo de serviço e adiciona os comportamentos disponíveis para a coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="81c0d-151">O <xref:System.ServiceModel.Description.IServiceBehavior> interface possui três métodos: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c0d-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="81c0d-152">Esses métodos são chamados pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> <span data-ttu-id="81c0d-153">é chamado pela primeira vez; Ele permite que o serviço a ser inspecionado para detectar inconsistências.</span><span class="sxs-lookup"><span data-stu-id="81c0d-153">is called first; it allows the service to be inspected for inconsistencies.</span></span> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> <span data-ttu-id="81c0d-154">é chamado em seguida; Esse método só é necessário em cenários muito avançados.</span><span class="sxs-lookup"><span data-stu-id="81c0d-154">is called next; this method is only required in very advanced scenarios.</span></span> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> <span data-ttu-id="81c0d-155">é chamado pela última vez e é responsável por configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="81c0d-155">is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="81c0d-156">Os seguintes parâmetros são passados para <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="81c0d-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
-   `Description`<span data-ttu-id="81c0d-157">: Esse parâmetro fornece a descrição do serviço para o serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="81c0d-157">: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="81c0d-158">Isso pode ser usado para inspecionar os dados de descrição sobre pontos de extremidade do serviço, contratos, associações e outros dados associados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
-   `ServiceHostBase`<span data-ttu-id="81c0d-159">: Esse parâmetro fornece o <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="81c0d-159">: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="81c0d-160">O personalizado <xref:System.ServiceModel.Description.IServiceBehavior> implementação, uma nova instância da `ObjectPoolInstanceProvider` será instanciado e atribuído ao <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> que é anexado ao <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="81c0d-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 <span data-ttu-id="81c0d-161">Além uma <xref:System.ServiceModel.Description.IServiceBehavior> implementação de `ObjectPoolingAttribute` classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo.</span><span class="sxs-lookup"><span data-stu-id="81c0d-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="81c0d-162">Esses membros incluem `MaxSize`, `MinSize`, `Enabled` e `CreationTimeout`, para coincidir com o conjunto de recursos fornecido pelo .NET Enterprise Services ao pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="81c0d-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="81c0d-163">O comportamento do pooling de objeto pode ser adicionado a um serviço WCF, anotando a implementação do serviço com o recém-criado personalizado `ObjectPooling` atributo.</span><span class="sxs-lookup"><span data-stu-id="81c0d-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="81c0d-164">Vinculando a ativação e desativação</span><span class="sxs-lookup"><span data-stu-id="81c0d-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="81c0d-165">O objetivo principal do pool de objetos é otimizar com a criação relativamente cara e inicialização de objetos de curta duração.</span><span class="sxs-lookup"><span data-stu-id="81c0d-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="81c0d-166">Portanto, ele pode fornecer um aumento de desempenho significativo a um aplicativo se usados corretamente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="81c0d-167">Porque o objeto é retornado do pool, o construtor é chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="81c0d-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="81c0d-168">No entanto, alguns aplicativos exigem algum nível de controle para que eles possam inicializar e limpar os recursos usados durante um único contexto.</span><span class="sxs-lookup"><span data-stu-id="81c0d-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="81c0d-169">Por exemplo, um objeto que está sendo usado para um conjunto de cálculos pode redefinir seus campos privados antes de processar o próximo cálculo.</span><span class="sxs-lookup"><span data-stu-id="81c0d-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="81c0d-170">Enterprise Services habilitado esse tipo de inicialização de contexto específico, permitindo que o desenvolvedor de objeto substituir `Activate` e `Deactivate` métodos a partir de <xref:System.EnterpriseServices.ServicedComponent> classe base.</span><span class="sxs-lookup"><span data-stu-id="81c0d-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="81c0d-171">As chamadas de pool do objeto a `Activate` método antes de retornar o objeto do pool.</span><span class="sxs-lookup"><span data-stu-id="81c0d-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> `Deactivate` <span data-ttu-id="81c0d-172">é chamado quando o objeto retorna ao pool.</span><span class="sxs-lookup"><span data-stu-id="81c0d-172">is called when the object returns back to the pool.</span></span> <span data-ttu-id="81c0d-173">O <xref:System.EnterpriseServices.ServicedComponent> classe base também tem uma `boolean` propriedade chamada `CanBePooled`, que pode ser usado para notificar o pool se o objeto pode ser agrupado ainda mais.</span><span class="sxs-lookup"><span data-stu-id="81c0d-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="81c0d-174">Para simular essa funcionalidade, o exemplo declara uma interface pública (`IObjectControl`) que tem os membros mencionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="81c0d-175">Essa interface implementada por classes destinadas a fornecer a inicialização de contexto específico de serviço.</span><span class="sxs-lookup"><span data-stu-id="81c0d-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="81c0d-176">O <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação deve ser modificada para atender a esses requisitos.</span><span class="sxs-lookup"><span data-stu-id="81c0d-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="81c0d-177">Agora, sempre que você obtenha um objeto chamando o `GetInstance` método, você deve verificar se o objeto implementa `IObjectControl.` em caso afirmativo, você deve chamar o `Activate` método adequadamente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="81c0d-178">Ao retornar um objeto para o pool, uma verificação é necessária para o `CanBePooled` propriedade antes de adicionar o objeto de volta para o pool.</span><span class="sxs-lookup"><span data-stu-id="81c0d-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="81c0d-179">Porque o desenvolvedor de serviço pode decidir se um objeto pode ser colocado em pool, a contagem de objetos em um pool em um determinado momento pode ir abaixo do tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="81c0d-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="81c0d-180">Portanto, você deve verificar se a contagem de objeto ficar abaixo do nível mínimo e execute a inicialização necessária do procedimento de limpeza.</span><span class="sxs-lookup"><span data-stu-id="81c0d-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="81c0d-181">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="81c0d-182">Pressione Enter em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="81c0d-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="81c0d-183">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="81c0d-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="81c0d-184">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81c0d-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="81c0d-185">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81c0d-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="81c0d-186">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81c0d-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81c0d-187">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="81c0d-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81c0d-188">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="81c0d-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81c0d-189">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="81c0d-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81c0d-190">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="81c0d-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
