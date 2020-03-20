---
title: Inicialização de instancialização
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183602"
---
# <a name="instancing-initialization"></a><span data-ttu-id="f39fb-102">Inicialização de instancialização</span><span class="sxs-lookup"><span data-stu-id="f39fb-102">Instancing Initialization</span></span>
<span data-ttu-id="f39fb-103">Esta amostra estende a amostra de `IObjectControl` [Pooling definindo](../../../../docs/framework/wcf/samples/pooling.md) uma interface, que personaliza a inicialização de um objeto ativando-o e desativando-o.</span><span class="sxs-lookup"><span data-stu-id="f39fb-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="f39fb-104">O cliente invoca métodos que retornam o objeto para o pool e que não retornam o objeto para o pool.</span><span class="sxs-lookup"><span data-stu-id="f39fb-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f39fb-105">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f39fb-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="f39fb-106">Pontos de Extensibilidade</span><span class="sxs-lookup"><span data-stu-id="f39fb-106">Extensibility Points</span></span>  
 <span data-ttu-id="f39fb-107">O primeiro passo para criar uma extensão da Windows Communication Foundation (WCF) é decidir o ponto de extensibilidade a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="f39fb-108">No WCF, o termo *EndpointDispatcher* refere-se a um componente de tempo de execução responsável por converter mensagens recebidas em invocações de método no serviço do usuário e converter valores de retorno desse método para uma mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="f39fb-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="f39fb-109">Um serviço WCF cria um EndpointDispatcher para cada ponto final.</span><span class="sxs-lookup"><span data-stu-id="f39fb-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="f39fb-110">O EndpointDispatcher oferece extensibilidade de escopo de ponto final (para <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> todas as mensagens recebidas ou enviadas pelo serviço) usando a classe.</span><span class="sxs-lookup"><span data-stu-id="f39fb-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="f39fb-111">Esta classe permite personalizar várias propriedades que controlam o comportamento do EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="f39fb-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="f39fb-112">Esta amostra se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> concentra na propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="f39fb-113">Iinstanceprovider</span><span class="sxs-lookup"><span data-stu-id="f39fb-113">IInstanceProvider</span></span>  
 <span data-ttu-id="f39fb-114">No WCF, o EndpointDispatcher cria instâncias de uma classe <xref:System.ServiceModel.Dispatcher.IInstanceProvider> de serviço usando um provedor de instâncias que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="f39fb-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="f39fb-115">Esta interface tem apenas dois métodos:</span><span class="sxs-lookup"><span data-stu-id="f39fb-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="f39fb-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Quando uma mensagem chega, <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> o Despachante chama o método para criar uma instância da classe de serviço para processar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f39fb-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="f39fb-117">A frequência das chamadas para este <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> método é determinada pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="f39fb-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="f39fb-118">Por exemplo, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> se a <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>propriedade estiver definida como , uma nova instância de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> classe de serviço é criada para processar cada mensagem que chega, por isso é chamado sempre que uma mensagem chega.</span><span class="sxs-lookup"><span data-stu-id="f39fb-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="f39fb-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Quando a instância de serviço termina o processamento da <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> mensagem, o EndpointDispatcher chama o método.</span><span class="sxs-lookup"><span data-stu-id="f39fb-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="f39fb-120">Como no <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, a frequência das chamadas para <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> este método é determinada pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="f39fb-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="f39fb-121">O Pool de Objetos</span><span class="sxs-lookup"><span data-stu-id="f39fb-121">The Object Pool</span></span>  
 <span data-ttu-id="f39fb-122">A `ObjectPoolInstanceProvider` classe contém a implementação para o pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="f39fb-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="f39fb-123">Esta classe implementa a <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface para interagir com a camada do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="f39fb-124">Quando o EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> chama o método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória.</span><span class="sxs-lookup"><span data-stu-id="f39fb-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="f39fb-125">Se um estiver disponível, é devolvido.</span><span class="sxs-lookup"><span data-stu-id="f39fb-125">If one is available, it is returned.</span></span> <span data-ttu-id="f39fb-126">Caso contrário, `ObjectPoolInstanceProvider` verifica `ActiveObjectsCount` se a propriedade (número de objetos devolvidos do pool) atingiu o tamanho máximo da piscina.</span><span class="sxs-lookup"><span data-stu-id="f39fb-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="f39fb-127">Caso não, uma nova instância é criada e `ActiveObjectsCount` devolvida ao chamador e, posteriormente, incrementada.</span><span class="sxs-lookup"><span data-stu-id="f39fb-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="f39fb-128">Caso contrário, uma solicitação de criação de objeto saem na fila por um período de tempo configurado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="f39fb-129">A implementação `GetObjectFromThePool` é mostrada no seguinte código de amostra.</span><span class="sxs-lookup"><span data-stu-id="f39fb-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="f39fb-130">A `ReleaseInstance` implementação personalizada adiciona a instância liberada de `ActiveObjectsCount` volta ao pool e decreta o valor.</span><span class="sxs-lookup"><span data-stu-id="f39fb-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="f39fb-131">O EndpointDispatcher pode chamar esses métodos de diferentes segmentos e, portanto, o acesso sincronizado aos membros do nível de classe na `ObjectPoolInstanceProvider` classe é necessário.</span><span class="sxs-lookup"><span data-stu-id="f39fb-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="f39fb-132">O `ReleaseInstance` método fornece um recurso *de inicialização* de limpeza.</span><span class="sxs-lookup"><span data-stu-id="f39fb-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="f39fb-133">Normalmente, a piscina mantém um número mínimo de objetos durante a vida útil da piscina.</span><span class="sxs-lookup"><span data-stu-id="f39fb-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="f39fb-134">No entanto, pode haver períodos de uso excessivo que requerem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="f39fb-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="f39fb-135">Eventualmente, quando a piscina se torna menos ativa, esses objetos excedentes podem se tornar uma sobrecarga extra.</span><span class="sxs-lookup"><span data-stu-id="f39fb-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="f39fb-136">Portanto, quando `activeObjectsCount` o atinge zero um temporizador ocioso é iniciado que aciona e executa um ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="f39fb-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="f39fb-137">As extensões de camada serviceModel são ligadas usando os seguintes comportamentos:</span><span class="sxs-lookup"><span data-stu-id="f39fb-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="f39fb-138">Comportamentos de serviço: Estes permitem a personalização de todo o tempo de execução do serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="f39fb-139">Comportamentos de ponto final: Estes permitem a personalização de um ponto final de serviço específico, incluindo o EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="f39fb-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="f39fb-140">Comportamentos contratuais: Estes permitem a <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> personalização de qualquer ou classes sobre o cliente ou o serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f39fb-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="f39fb-141">Comportamentos de operação: Estes permitem <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> personalização de qualquer ou classes sobre o cliente ou o serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f39fb-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="f39fb-142">Para fins de uma extensão de agrupamento de objetos, um comportamento de ponto final ou um comportamento de serviço podem ser criados.</span><span class="sxs-lookup"><span data-stu-id="f39fb-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="f39fb-143">Neste exemplo, usamos um comportamento de serviço, que aplica a capacidade de agrupamento de objetos em todos os pontos finais do serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="f39fb-144">Os comportamentos de serviço são <xref:System.ServiceModel.Description.IServiceBehavior> criados implementando a interface.</span><span class="sxs-lookup"><span data-stu-id="f39fb-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="f39fb-145">Existem várias maneiras de conscientizar o ServiceModel sobre os comportamentos personalizados:</span><span class="sxs-lookup"><span data-stu-id="f39fb-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="f39fb-146">Usando um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="f39fb-147">Adicioná-lo imperativamente à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="f39fb-148">Estendendo o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f39fb-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="f39fb-149">Esta amostra usa um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="f39fb-150">Quando <xref:System.ServiceModel.ServiceHost> o é construído, examina os atributos utilizados na definição do tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="f39fb-151">A <xref:System.ServiceModel.Description.IServiceBehavior> interface tem três <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>métodos: e .</span><span class="sxs-lookup"><span data-stu-id="f39fb-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="f39fb-152">Esses métodos são chamados pelo <xref:System.ServiceModel.ServiceHost> WCF quando o está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="f39fb-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>é chamado primeiro; permite que o serviço seja inspecionado por inconsistências.</span><span class="sxs-lookup"><span data-stu-id="f39fb-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="f39fb-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>é chamado de próximo; este método só é necessário em cenários muito avançados.</span><span class="sxs-lookup"><span data-stu-id="f39fb-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="f39fb-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>é chamado de último e é responsável pela configuração do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f39fb-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="f39fb-156">Os seguintes parâmetros são passados em: <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f39fb-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="f39fb-157">`Description`: Este parâmetro fornece a descrição do serviço para todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="f39fb-158">Isso pode ser usado para inspecionar dados de descrição sobre os pontos finais do serviço, contratos, vinculações e outros dados associados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="f39fb-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="f39fb-159">`ServiceHostBase`: Este parâmetro <xref:System.ServiceModel.ServiceHostBase> fornece o que está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="f39fb-160">Na <xref:System.ServiceModel.Description.IServiceBehavior> implementação personalizada, uma `ObjectPoolInstanceProvider` nova instância é instanciada e atribuída à <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada uma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> das que está anexada ao <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="f39fb-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="f39fb-161">Além de <xref:System.ServiceModel.Description.IServiceBehavior> uma `ObjectPoolingAttribute` implementação, a classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo.</span><span class="sxs-lookup"><span data-stu-id="f39fb-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="f39fb-162">Esses membros `MaxSize` `MinSize`incluem `Enabled` `CreationTimeout`, e , para corresponder ao conjunto de recursos de pooling de objetos fornecido pelo .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="f39fb-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="f39fb-163">O comportamento de pooling de objetos agora pode ser adicionado a um serviço `ObjectPooling` WCF anotando a implementação do serviço com o atributo personalizado recém-criado.</span><span class="sxs-lookup"><span data-stu-id="f39fb-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="f39fb-164">Ativação e desativação de ganchos</span><span class="sxs-lookup"><span data-stu-id="f39fb-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="f39fb-165">O objetivo principal do agrupamento de objetos é otimizar objetos de curta duração com criação e inicialização relativamente caras.</span><span class="sxs-lookup"><span data-stu-id="f39fb-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="f39fb-166">Portanto, ele pode dar um aumento dramático de desempenho para uma aplicação se usado corretamente.</span><span class="sxs-lookup"><span data-stu-id="f39fb-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="f39fb-167">Como o objeto é devolvido da piscina, o construtor é chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f39fb-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="f39fb-168">No entanto, alguns aplicativos exigem algum nível de controle para que possam inicializar e limpar os recursos usados durante um único contexto.</span><span class="sxs-lookup"><span data-stu-id="f39fb-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="f39fb-169">Por exemplo, um objeto que está sendo usado para um conjunto de cálculos pode redefinir seus campos privados antes de processar o próximo cálculo.</span><span class="sxs-lookup"><span data-stu-id="f39fb-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="f39fb-170">Os Serviços Corporativos permitiram esse tipo de inicialização `Activate` `Deactivate` específica do <xref:System.EnterpriseServices.ServicedComponent> contexto, permitindo que o desenvolvedor de objetos se sobreponha e os métodos da classe base.</span><span class="sxs-lookup"><span data-stu-id="f39fb-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="f39fb-171">O pool de `Activate` objetos chama o método pouco antes de devolver o objeto da piscina.</span><span class="sxs-lookup"><span data-stu-id="f39fb-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="f39fb-172">`Deactivate`é chamado quando o objeto retorna para a piscina.</span><span class="sxs-lookup"><span data-stu-id="f39fb-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="f39fb-173">A <xref:System.EnterpriseServices.ServicedComponent> classe base `boolean` também `CanBePooled`tem uma propriedade chamada , que pode ser usada para notificar o pool se o objeto pode ser agrupado ainda mais.</span><span class="sxs-lookup"><span data-stu-id="f39fb-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="f39fb-174">Para imitar essa funcionalidade, a amostra declara`IObjectControl`uma interface pública ( ) que tem os membros acima mencionados.</span><span class="sxs-lookup"><span data-stu-id="f39fb-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="f39fb-175">Essa interface é então implementada por classes de serviço destinadas a fornecer inicialização específica do contexto.</span><span class="sxs-lookup"><span data-stu-id="f39fb-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="f39fb-176">A <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação deve ser modificada para atender a esses requisitos.</span><span class="sxs-lookup"><span data-stu-id="f39fb-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="f39fb-177">Agora, cada vez que você `GetInstance` recebe um objeto chamando o `IObjectControl.` método, você deve `Activate` verificar se o objeto implementa Se ele faz, você deve chamar o método apropriadamente.</span><span class="sxs-lookup"><span data-stu-id="f39fb-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="f39fb-178">Ao devolver um objeto à piscina, é `CanBePooled` necessária uma verificação para a propriedade antes de adicionar o objeto de volta à piscina.</span><span class="sxs-lookup"><span data-stu-id="f39fb-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="f39fb-179">Como o desenvolvedor do serviço pode decidir se um objeto pode ser agrupado, a contagem de objetos no pool em um determinado momento pode ficar abaixo do tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="f39fb-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="f39fb-180">Portanto, você deve verificar se a contagem de objetos foi abaixo do nível mínimo e realizar a inicialização necessária no procedimento de limpeza.</span><span class="sxs-lookup"><span data-stu-id="f39fb-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="f39fb-181">Quando você executa a amostra, as solicitações e respostas da operação são exibidas nas janelas do serviço e do console cliente.</span><span class="sxs-lookup"><span data-stu-id="f39fb-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f39fb-182">Pressione Enter em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="f39fb-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f39fb-183">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f39fb-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f39fb-184">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f39fb-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f39fb-185">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f39fb-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f39fb-186">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f39fb-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f39fb-187">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f39fb-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f39fb-188">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f39fb-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f39fb-189">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="f39fb-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f39fb-190">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f39fb-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
