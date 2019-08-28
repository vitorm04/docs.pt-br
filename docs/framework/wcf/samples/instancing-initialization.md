---
title: Inicialização de instancialização
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 4d6fdfedad9d522230a35014c0ee164e8b24fcfb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039606"
---
# <a name="instancing-initialization"></a><span data-ttu-id="52532-102">Inicialização de instancialização</span><span class="sxs-lookup"><span data-stu-id="52532-102">Instancing Initialization</span></span>
<span data-ttu-id="52532-103">Este exemplo estende o exemplo de [pooling](../../../../docs/framework/wcf/samples/pooling.md) definindo uma interface, `IObjectControl`, que personaliza a inicialização de um objeto ativando-o e desativando-o.</span><span class="sxs-lookup"><span data-stu-id="52532-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="52532-104">O cliente invoca métodos que retornam o objeto ao pool e que não retornam o objeto para o pool.</span><span class="sxs-lookup"><span data-stu-id="52532-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52532-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="52532-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="52532-106">Pontos de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="52532-106">Extensibility Points</span></span>  
 <span data-ttu-id="52532-107">A primeira etapa na criação de uma extensão Windows Communication Foundation (WCF) é decidir o ponto de extensibilidade a ser usado.</span><span class="sxs-lookup"><span data-stu-id="52532-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="52532-108">No WCF, o termo *EndpointDispatcher* refere-se a um componente de tempo de execução responsável pela conversão de mensagens de entrada em invocações de método no serviço do usuário e pela conversão de valores de retorno desse método em uma mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="52532-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="52532-109">Um serviço WCF cria um EndpointDispatcher para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="52532-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="52532-110">O EndpointDispatcher oferece a extensibilidade do escopo do ponto de extremidade (para todas as mensagens recebidas ou <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> enviadas pela serviço) usando a classe.</span><span class="sxs-lookup"><span data-stu-id="52532-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="52532-111">Essa classe permite que você personalize várias propriedades que controlam o comportamento do EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="52532-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="52532-112">Este exemplo se concentra na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="52532-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="52532-113">IInstanceProvider</span></span>  
 <span data-ttu-id="52532-114">No WCF, o EndpointDispatcher cria instâncias de uma classe de serviço usando um provedor de instância que implementa <xref:System.ServiceModel.Dispatcher.IInstanceProvider> a interface.</span><span class="sxs-lookup"><span data-stu-id="52532-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="52532-115">Esta interface tem apenas dois métodos:</span><span class="sxs-lookup"><span data-stu-id="52532-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="52532-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Quando uma mensagem chega, o Dispatcher chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método para criar uma instância da classe de serviço para processar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="52532-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="52532-117">A frequência das chamadas para esse método é determinada pela <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="52532-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="52532-118">Por exemplo, se <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> a propriedade for definida <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>como, uma nova instância da classe de serviço será criada para processar cada mensagem que chega <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> , portanto, é chamado sempre que uma mensagem chega.</span><span class="sxs-lookup"><span data-stu-id="52532-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="52532-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Quando a instância do serviço termina de processar a mensagem, o EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> chama o método.</span><span class="sxs-lookup"><span data-stu-id="52532-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="52532-120">Como no <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, a frequência das chamadas para esse método é determinada <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="52532-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="52532-121">O pool de objetos</span><span class="sxs-lookup"><span data-stu-id="52532-121">The Object Pool</span></span>  
 <span data-ttu-id="52532-122">A `ObjectPoolInstanceProvider` classe contém a implementação para o pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="52532-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="52532-123">Essa classe implementa a <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface para interagir com a camada de modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="52532-124">Quando o EndpointDispatcher chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool na memória.</span><span class="sxs-lookup"><span data-stu-id="52532-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="52532-125">Se houver um disponível, ele será retornado.</span><span class="sxs-lookup"><span data-stu-id="52532-125">If one is available, it is returned.</span></span> <span data-ttu-id="52532-126">Caso contrário `ObjectPoolInstanceProvider` , o verifica `ActiveObjectsCount` se a propriedade (número de objetos retornados do pool) atingiu o tamanho máximo do pool.</span><span class="sxs-lookup"><span data-stu-id="52532-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="52532-127">Caso contrário, uma nova instância será criada e retornada ao chamador e `ActiveObjectsCount` será subsequentemente incrementada.</span><span class="sxs-lookup"><span data-stu-id="52532-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="52532-128">Caso contrário, uma solicitação de criação de objeto será enfileirada por um período de tempo configurado.</span><span class="sxs-lookup"><span data-stu-id="52532-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="52532-129">A implementação do `GetObjectFromThePool` é mostrada no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="52532-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="52532-130">A implementação `ReleaseInstance` personalizada adiciona a instância liberada de volta ao pool e decrementa o `ActiveObjectsCount` valor.</span><span class="sxs-lookup"><span data-stu-id="52532-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="52532-131">O EndpointDispatcher pode chamar esses métodos de threads diferentes e, portanto, o acesso sincronizado aos membros de `ObjectPoolInstanceProvider` nível de classe na classe é necessário.</span><span class="sxs-lookup"><span data-stu-id="52532-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="52532-132">O `ReleaseInstance` método fornece um recurso de *inicialização de limpeza* .</span><span class="sxs-lookup"><span data-stu-id="52532-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="52532-133">Normalmente, o pool mantém um número mínimo de objetos durante o tempo de vida do pool.</span><span class="sxs-lookup"><span data-stu-id="52532-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="52532-134">No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para alcançar o limite máximo especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="52532-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="52532-135">Eventualmente, quando o pool se torna menos ativo, os objetos excedentes podem se tornar uma sobrecarga extra.</span><span class="sxs-lookup"><span data-stu-id="52532-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="52532-136">Portanto, quando `activeObjectsCount` o chega a zero, um temporizador ocioso é iniciado e executa um ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="52532-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="52532-137">As extensões de camada de ServiceModel são conectadas usando os seguintes comportamentos:</span><span class="sxs-lookup"><span data-stu-id="52532-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="52532-138">Comportamentos de serviço: Elas permitem a personalização de todo o tempo de execução do serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="52532-139">Comportamentos de ponto de extremidade: Eles permitem a personalização de um ponto de extremidade de serviço específico, incluindo o EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="52532-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="52532-140">Comportamentos de contrato: Eles permitem a personalização de qualquer uma <xref:System.ServiceModel.Dispatcher.ClientRuntime> das <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes ou do cliente ou do serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="52532-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="52532-141">Comportamentos de operação: Eles permitem a personalização de qualquer uma <xref:System.ServiceModel.Dispatcher.ClientOperation> das <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes ou do cliente ou do serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="52532-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="52532-142">Para fins de uma extensão de pool de objetos, um comportamento de ponto de extremidade ou um comportamento de serviço pode ser criado.</span><span class="sxs-lookup"><span data-stu-id="52532-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="52532-143">Neste exemplo, usamos um comportamento de serviço, que aplica a capacidade de pooling de objetos a todos os pontos de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="52532-144">Os comportamentos de serviço são criados pela <xref:System.ServiceModel.Description.IServiceBehavior> implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="52532-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="52532-145">Há várias maneiras de tornar o ServiceModel ciente dos comportamentos personalizados:</span><span class="sxs-lookup"><span data-stu-id="52532-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="52532-146">Usando um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="52532-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="52532-147">Adicionando imperativamente à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="52532-148">Estendendo o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="52532-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="52532-149">Este exemplo usa um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="52532-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="52532-150">Quando o <xref:System.ServiceModel.ServiceHost> é construído, ele examina os atributos usados na definição de tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="52532-151">A <xref:System.ServiceModel.Description.IServiceBehavior> interface tem três métodos: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> e.`,` <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="52532-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="52532-152">Esses métodos são chamados pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="52532-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="52532-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>é chamado primeiro; Ele permite que o serviço seja inspecionado quanto a inconsistências.</span><span class="sxs-lookup"><span data-stu-id="52532-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="52532-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>é chamado em avançar; Esse método só é necessário em cenários muito avançados.</span><span class="sxs-lookup"><span data-stu-id="52532-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="52532-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>é chamado por último e é responsável por configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="52532-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="52532-156">Os parâmetros a seguir são passados <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>em:</span><span class="sxs-lookup"><span data-stu-id="52532-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="52532-157">`Description`: Esse parâmetro fornece a descrição do serviço para todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="52532-158">Isso pode ser usado para inspecionar dados de descrição sobre os pontos de extremidade do serviço, os contratos, as associações e outros dados associados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="52532-159">`ServiceHostBase`: Esse parâmetro fornece o <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializado no momento.</span><span class="sxs-lookup"><span data-stu-id="52532-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="52532-160">Na implementação personalizada <xref:System.ServiceModel.Description.IServiceBehavior> , uma nova instância do `ObjectPoolInstanceProvider` é instanciada e atribuída à <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.ServiceHostBase>Propriedade em cada <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> uma que está anexada ao.</span><span class="sxs-lookup"><span data-stu-id="52532-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
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
  
 <span data-ttu-id="52532-161">Além de uma <xref:System.ServiceModel.Description.IServiceBehavior> implementação, a `ObjectPoolingAttribute` classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo.</span><span class="sxs-lookup"><span data-stu-id="52532-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="52532-162">Esses membros incluem `MaxSize` `MinSize` ,e`CreationTimeout`,para corresponder ao conjunto de recursos do pool de objetos fornecido pelo .net Enterprise Services. `Enabled`</span><span class="sxs-lookup"><span data-stu-id="52532-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="52532-163">O comportamento do pool de objetos agora pode ser adicionado a um serviço do WCF anotando a implementação do serviço com o atributo `ObjectPooling` personalizado recém-criado.</span><span class="sxs-lookup"><span data-stu-id="52532-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="52532-164">Conectando ativação e desativação</span><span class="sxs-lookup"><span data-stu-id="52532-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="52532-165">O objetivo principal do pool de objetos é otimizar objetos de curta duração com criação e inicialização relativamente caras.</span><span class="sxs-lookup"><span data-stu-id="52532-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="52532-166">Portanto, ele pode dar um aumento considerável no desempenho para um aplicativo, se usado corretamente.</span><span class="sxs-lookup"><span data-stu-id="52532-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="52532-167">Como o objeto é retornado do pool, o construtor é chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="52532-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="52532-168">No entanto, alguns aplicativos exigem algum nível de controle para que possam inicializar e limpar os recursos usados durante um único contexto.</span><span class="sxs-lookup"><span data-stu-id="52532-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="52532-169">Por exemplo, um objeto que está sendo usado para um conjunto de cálculos pode redefinir seus campos particulares antes de processar o próximo cálculo.</span><span class="sxs-lookup"><span data-stu-id="52532-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="52532-170">Os serviços corporativos habilitaram esse tipo de inicialização específica de contexto, permitindo que `Activate` o `Deactivate` desenvolvedor do objeto <xref:System.EnterpriseServices.ServicedComponent> substitua e métodos da classe base.</span><span class="sxs-lookup"><span data-stu-id="52532-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="52532-171">O pool de objetos chama `Activate` o método logo antes de retornar o objeto do pool.</span><span class="sxs-lookup"><span data-stu-id="52532-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="52532-172">`Deactivate`é chamado quando o objeto retorna de volta para o pool.</span><span class="sxs-lookup"><span data-stu-id="52532-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="52532-173">A <xref:System.EnterpriseServices.ServicedComponent> classe base também tem uma `boolean` propriedade chamada `CanBePooled`, que pode ser usada para notificar o pool se o objeto pode ser mais agrupado.</span><span class="sxs-lookup"><span data-stu-id="52532-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="52532-174">Para imitar essa funcionalidade, o exemplo declara uma interface pública (`IObjectControl`) que tem os membros mencionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="52532-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="52532-175">Essa interface é então implementada por classes de serviço destinadas a fornecer inicialização específica de contexto.</span><span class="sxs-lookup"><span data-stu-id="52532-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="52532-176">A <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação deve ser modificada para atender a esses requisitos.</span><span class="sxs-lookup"><span data-stu-id="52532-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="52532-177">Agora, sempre que você receber um objeto chamando o `GetInstance` método, deverá verificar se o objeto implementa `IObjectControl.` se ele faz isso, você deve chamar o `Activate` método adequadamente.</span><span class="sxs-lookup"><span data-stu-id="52532-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="52532-178">Ao retornar um objeto para o pool, uma verificação é necessária para a `CanBePooled` propriedade antes de adicionar o objeto de volta ao pool.</span><span class="sxs-lookup"><span data-stu-id="52532-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
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
  
 <span data-ttu-id="52532-179">Como o desenvolvedor do serviço pode decidir se um objeto pode ser agrupado, a contagem de objetos no pool em um determinado momento pode ficar abaixo do tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="52532-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="52532-180">Portanto, você deve verificar se a contagem de objetos esteve abaixo do nível mínimo e executar a inicialização necessária no procedimento de limpeza.</span><span class="sxs-lookup"><span data-stu-id="52532-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
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
  
 <span data-ttu-id="52532-181">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="52532-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="52532-182">Pressione Enter em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="52532-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52532-183">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="52532-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="52532-184">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52532-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="52532-185">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52532-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="52532-186">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52532-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52532-187">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="52532-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52532-188">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="52532-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="52532-189">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="52532-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52532-190">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="52532-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
