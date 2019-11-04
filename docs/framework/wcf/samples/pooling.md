---
title: Agrupamento
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 717dafb6ba9467590201511cbc0ac17690c931ae
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424277"
---
# <a name="pooling"></a><span data-ttu-id="3515a-102">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="3515a-102">Pooling</span></span>
<span data-ttu-id="3515a-103">Este exemplo demonstra como estender Windows Communication Foundation (WCF) para dar suporte ao pooling de objetos.</span><span class="sxs-lookup"><span data-stu-id="3515a-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="3515a-104">O exemplo demonstra como criar um atributo que seja sintaticamente e semanticamente semelhante à funcionalidade de atributo `ObjectPoolingAttribute` dos serviços corporativos.</span><span class="sxs-lookup"><span data-stu-id="3515a-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="3515a-105">O pooling de objetos pode fornecer um aumento considerável para o desempenho de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3515a-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="3515a-106">No entanto, ele pode ter o efeito oposto se não for usado corretamente.</span><span class="sxs-lookup"><span data-stu-id="3515a-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="3515a-107">O pooling de objetos ajuda a reduzir a sobrecarga de recriação de objetos usados com frequência que exigem inicialização extensiva.</span><span class="sxs-lookup"><span data-stu-id="3515a-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="3515a-108">No entanto, se uma chamada para um método em um objeto em pool levar um tempo considerável para ser concluída, o pooling de objetos enfileirará solicitações adicionais assim que o tamanho máximo do pool for atingido.</span><span class="sxs-lookup"><span data-stu-id="3515a-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="3515a-109">Portanto, ele pode falhar ao fornecer algumas solicitações de criação de objeto lançando uma exceção de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3515a-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3515a-110">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3515a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3515a-111">A primeira etapa na criação de uma extensão WCF é decidir o ponto de extensibilidade a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3515a-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="3515a-112">No WCF, o termo *Dispatcher* refere-se a um componente de tempo de execução responsável pela conversão de mensagens de entrada em invocações de método no serviço do usuário e pela conversão de valores de retorno desse método em uma mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="3515a-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="3515a-113">Um serviço WCF cria um Dispatcher para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3515a-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="3515a-114">Um cliente WCF deve usar um Dispatcher se o contrato associado a esse cliente for um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="3515a-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="3515a-115">Os despachantes de canal e ponto de extremidade oferecem extensibilidade de canal e de todo o contrato expondo várias propriedades que controlam o comportamento do Dispatcher.</span><span class="sxs-lookup"><span data-stu-id="3515a-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="3515a-116">A propriedade <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> também permite que você inspecione, modifique ou personalize o processo de expedição.</span><span class="sxs-lookup"><span data-stu-id="3515a-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="3515a-117">Este exemplo se concentra na propriedade <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> que aponta para o objeto que fornece as instâncias da classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="3515a-118">O IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="3515a-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="3515a-119">No WCF, o Dispatcher cria instâncias da classe de serviço usando um <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, que implementa a interface <xref:System.ServiceModel.Dispatcher.IInstanceProvider>.</span><span class="sxs-lookup"><span data-stu-id="3515a-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="3515a-120">Essa interface tem três métodos:</span><span class="sxs-lookup"><span data-stu-id="3515a-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="3515a-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: quando uma mensagem chega ao dispatcher chama o método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> para criar uma instância da classe de serviço para processar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="3515a-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="3515a-122">A frequência das chamadas para esse método é determinada pela propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3515a-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="3515a-123">Por exemplo, se a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> for definida como <xref:System.ServiceModel.InstanceContextMode.PerCall> uma nova instância da classe de serviço será criada para processar cada mensagem que chega, de modo que <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> será chamado sempre que uma mensagem chegar.</span><span class="sxs-lookup"><span data-stu-id="3515a-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="3515a-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: isso é idêntico ao método anterior, exceto que isso é invocado quando não há nenhum argumento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3515a-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="3515a-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: quando o tempo de vida de uma instância de serviço tiver decorrido, o Dispatcher chamará o método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="3515a-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="3515a-126">Assim como no método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, a frequência das chamadas para esse método é determinada pela propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3515a-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="3515a-127">O pool de objetos</span><span class="sxs-lookup"><span data-stu-id="3515a-127">The Object Pool</span></span>  
 <span data-ttu-id="3515a-128">Uma implementação de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> personalizada fornece a semântica de pool de objetos necessária para um serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="3515a-129">Portanto, esse exemplo tem um tipo de `ObjectPoolingInstanceProvider` que fornece implementação personalizada de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> para pooling.</span><span class="sxs-lookup"><span data-stu-id="3515a-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="3515a-130">Quando o `Dispatcher` chama o método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool na memória.</span><span class="sxs-lookup"><span data-stu-id="3515a-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="3515a-131">Se houver um disponível, ele será retornado.</span><span class="sxs-lookup"><span data-stu-id="3515a-131">If one is available, it is returned.</span></span> <span data-ttu-id="3515a-132">Caso contrário, um novo objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="3515a-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="3515a-133">A implementação para `GetInstance` é mostrada no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3515a-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;            
}  
```  
  
 <span data-ttu-id="3515a-134">A implementação de `ReleaseInstance` personalizada adiciona a instância liberada de volta ao pool e decrementa o valor de `ActiveObjectsCount`.</span><span class="sxs-lookup"><span data-stu-id="3515a-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="3515a-135">O `Dispatcher` pode chamar esses métodos de threads diferentes e, portanto, o acesso sincronizado aos membros de nível de classe na classe `ObjectPoolingInstanceProvider` é necessário.</span><span class="sxs-lookup"><span data-stu-id="3515a-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests   
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();                       
    }  
}  
```  
  
 <span data-ttu-id="3515a-136">O método `ReleaseInstance` fornece um recurso de "inicialização de limpeza".</span><span class="sxs-lookup"><span data-stu-id="3515a-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="3515a-137">Normalmente, o pool mantém um número mínimo de objetos durante o tempo de vida do pool.</span><span class="sxs-lookup"><span data-stu-id="3515a-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="3515a-138">No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para alcançar o limite máximo especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="3515a-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="3515a-139">Eventualmente, quando o pool se torna menos ativo, esses objetos excedentes podem se tornar uma sobrecarga extra.</span><span class="sxs-lookup"><span data-stu-id="3515a-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="3515a-140">Portanto, quando o `activeObjectsCount` chega a zero, um temporizador ocioso é iniciado que dispara e executa um ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="3515a-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="3515a-141">Adicionando o comportamento</span><span class="sxs-lookup"><span data-stu-id="3515a-141">Adding the Behavior</span></span>  
 <span data-ttu-id="3515a-142">As extensões de camada de Dispatcher são conectadas usando os seguintes comportamentos:</span><span class="sxs-lookup"><span data-stu-id="3515a-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="3515a-143">Comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-143">Service Behaviors.</span></span> <span data-ttu-id="3515a-144">Elas permitem a personalização de todo o tempo de execução do serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="3515a-145">Comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3515a-145">Endpoint Behaviors.</span></span> <span data-ttu-id="3515a-146">Eles permitem a personalização de pontos de extremidade de serviço, especificamente um Dispatcher de canal e de ponto final.</span><span class="sxs-lookup"><span data-stu-id="3515a-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="3515a-147">Comportamentos de contrato.</span><span class="sxs-lookup"><span data-stu-id="3515a-147">Contract Behaviors.</span></span> <span data-ttu-id="3515a-148">Eles permitem a personalização das classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> no cliente e no serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3515a-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="3515a-149">Para a finalidade de uma extensão de pool de objetos, um comportamento de serviço deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="3515a-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="3515a-150">Os comportamentos de serviço são criados com a implementação da interface <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3515a-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="3515a-151">Há várias maneiras de fazer com que o modelo de serviço reconheça os comportamentos personalizados:</span><span class="sxs-lookup"><span data-stu-id="3515a-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="3515a-152">Usando um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="3515a-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="3515a-153">Adicionando imperativamente à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="3515a-154">Estendendo o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3515a-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="3515a-155">Este exemplo usa um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="3515a-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="3515a-156">Quando o <xref:System.ServiceModel.ServiceHost> é construído, ele examina os atributos usados na definição de tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="3515a-157">A interface <xref:System.ServiceModel.Description.IServiceBehavior> tem três métodos, <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="3515a-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="3515a-158">O método <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> é usado para garantir que o comportamento possa ser aplicado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="3515a-159">Neste exemplo, a implementação garante que o serviço não esteja configurado com <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="3515a-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="3515a-160">O método <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> é usado para configurar as associações do serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="3515a-161">Isso não é necessário neste cenário.</span><span class="sxs-lookup"><span data-stu-id="3515a-161">It is not required in this scenario.</span></span> <span data-ttu-id="3515a-162">O <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> é usado para configurar os expedidores do serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="3515a-163">Esse método é chamado pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="3515a-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="3515a-164">Os parâmetros a seguir são passados para este método:</span><span class="sxs-lookup"><span data-stu-id="3515a-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="3515a-165">`Description`: esse argumento fornece a descrição do serviço para todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="3515a-166">Isso pode ser usado para inspecionar dados de descrição sobre os pontos de extremidade, contratos, associações e outros dados do serviço.</span><span class="sxs-lookup"><span data-stu-id="3515a-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="3515a-167">`ServiceHostBase`: esse argumento fornece a <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializada no momento.</span><span class="sxs-lookup"><span data-stu-id="3515a-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="3515a-168">Na implementação de <xref:System.ServiceModel.Description.IServiceBehavior> personalizada, uma nova instância do `ObjectPoolingInstanceProvider` é instanciada e atribuída à propriedade <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> em cada <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="3515a-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,   
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior   
    // (this.throttlingBehavior==null), it should have initialized   
    // a single ServiceThrottle on all ChannelDispatchers.    
    // As we loop through the ChannelDispatchers, we verify that   
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in   
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all   
            // endpoints. If there were others, we could not enforce   
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&   
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new   
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =   
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items   
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >   
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="3515a-169">Além de uma implementação de <xref:System.ServiceModel.Description.IServiceBehavior>, a classe <xref:System.EnterpriseServices.ObjectPoolingAttribute> tem vários membros para personalizar o pool de objetos usando os argumentos de atributo.</span><span class="sxs-lookup"><span data-stu-id="3515a-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="3515a-170">Esses membros incluem <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>e <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>para corresponder ao conjunto de recursos do pool de objetos fornecido pelo .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="3515a-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="3515a-171">O comportamento do pool de objetos agora pode ser adicionado a um serviço WCF anotando a implementação do serviço com o atributo de `ObjectPooling` personalizado recém-criado.</span><span class="sxs-lookup"><span data-stu-id="3515a-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="3515a-172">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="3515a-172">Running the Sample</span></span>  
 <span data-ttu-id="3515a-173">O exemplo demonstra os benefícios de desempenho que podem ser obtidos usando o pool de objetos em determinados cenários.</span><span class="sxs-lookup"><span data-stu-id="3515a-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="3515a-174">O aplicativo de serviço implementa dois serviços – `WorkService` e `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="3515a-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="3515a-175">Ambos os serviços compartilham a mesma implementação – eles exigem uma inicialização cara e expõem um método de `DoWork()` relativamente barato.</span><span class="sxs-lookup"><span data-stu-id="3515a-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="3515a-176">A única diferença é que o `ObjectPooledWorkService` tem o pool de objetos configurado:</span><span class="sxs-lookup"><span data-stu-id="3515a-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }          
}  
```  
  
 <span data-ttu-id="3515a-177">Quando você executa o cliente, ele se esgota ao chamar o `WorkService` 5 vezes.</span><span class="sxs-lookup"><span data-stu-id="3515a-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="3515a-178">Em seguida, as vezes chamam o `ObjectPooledWorkService` 5 vezes.</span><span class="sxs-lookup"><span data-stu-id="3515a-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="3515a-179">A diferença no tempo é exibida:</span><span class="sxs-lookup"><span data-stu-id="3515a-179">The difference in time is then displayed:</span></span>  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="3515a-180">Na primeira vez em que o cliente é executado, ambos os serviços parecem levar aproximadamente na mesma quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="3515a-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="3515a-181">Se você executar novamente o exemplo, poderá ver que o `ObjectPooledWorkService` retorna muito mais rápido porque já existe uma instância desse objeto no pool.</span><span class="sxs-lookup"><span data-stu-id="3515a-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3515a-182">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3515a-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3515a-183">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3515a-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3515a-184">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3515a-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3515a-185">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3515a-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3515a-186">Se você usar svcutil. exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="3515a-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3515a-187">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3515a-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3515a-188">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3515a-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3515a-189">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="3515a-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3515a-190">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3515a-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
