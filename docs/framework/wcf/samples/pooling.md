---
title: Agrupamento
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183398"
---
# <a name="pooling"></a><span data-ttu-id="ce3c3-102">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="ce3c3-102">Pooling</span></span>
<span data-ttu-id="ce3c3-103">Esta amostra demonstra como estender o Windows Communication Foundation (WCF) para suportar o pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="ce3c3-104">A amostra demonstra como criar um atributo que seja sintática `ObjectPoolingAttribute` e semanticamente semelhante à funcionalidade de atributo dos Serviços Corporativos.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="ce3c3-105">O pool de objetos pode fornecer um impulso dramático ao desempenho de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="ce3c3-106">No entanto, pode ter o efeito oposto se não for usado corretamente.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="ce3c3-107">O agrupamento de objetos ajuda a reduzir a sobrecarga de recriar objetos usados com freqüência que requerem uma inicialização extensiva.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="ce3c3-108">No entanto, se uma chamada para um método em um objeto agrupado levar um tempo considerável para ser concluída, o pool de objetos faz filas adicionais assim que o tamanho máximo da piscina for atingido.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="ce3c3-109">Assim, ele pode não atender a algumas solicitações de criação de objetos, lançando uma exceção de tempo.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce3c3-110">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce3c3-111">O primeiro passo para criar uma extensão do WCF é decidir o ponto de extensibilidade a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="ce3c3-112">No WCF, o *despachante* de termo refere-se a um componente de tempo de execução responsável pela conversão de mensagens recebidas em invocações de método no serviço do usuário e por converter valores de retorno desse método para uma mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="ce3c3-113">Um serviço WCF cria um despachante para cada ponto final.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="ce3c3-114">Um cliente WCF deve usar um despachante se o contrato associado a esse cliente for um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="ce3c3-115">Os despachantes de canais e pontos finais oferecem extensibilidade de canal e contrato, expondo várias propriedades que controlam o comportamento do despachante.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="ce3c3-116">A <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> propriedade também permite que você inspecione, modifique ou personalize o processo de expedição.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="ce3c3-117">Esta amostra se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> concentra na propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="ce3c3-118">O provedor de iinstance</span><span class="sxs-lookup"><span data-stu-id="ce3c3-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="ce3c3-119">No WCF, o despachante cria <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>instâncias da <xref:System.ServiceModel.Dispatcher.IInstanceProvider> classe de serviço usando a , que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="ce3c3-120">Esta interface tem três métodos:</span><span class="sxs-lookup"><span data-stu-id="ce3c3-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="ce3c3-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Quando uma mensagem chega, o Despachante chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método para criar uma instância da classe de serviço para processar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="ce3c3-122">A frequência das chamadas para este <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> método é determinada pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="ce3c3-123">Por exemplo, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> se a <xref:System.ServiceModel.InstanceContextMode.PerCall> propriedade for definida como uma nova instância de classe <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> de serviço é criada para processar cada mensagem que chega, assim é chamada sempre que uma mensagem chega.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="ce3c3-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Este é idêntico ao método anterior, exceto que este é invocado quando não há argumento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="ce3c3-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Quando a vida útil de uma instância de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> serviço é decorrido, o Despachante chama o método.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="ce3c3-126">Assim como <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> para o método, a frequência das chamadas <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> para este método é determinada pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="ce3c3-127">O Pool de Objetos</span><span class="sxs-lookup"><span data-stu-id="ce3c3-127">The Object Pool</span></span>  
 <span data-ttu-id="ce3c3-128">Uma <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação personalizada fornece a semântica de pool de objetos necessária para um serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="ce3c3-129">Portanto, esta amostra `ObjectPoolingInstanceProvider` tem um tipo <xref:System.ServiceModel.Dispatcher.IInstanceProvider> que fornece implementação personalizada para pooling.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="ce3c3-130">Quando `Dispatcher` o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método chama, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="ce3c3-131">Se um estiver disponível, é devolvido.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-131">If one is available, it is returned.</span></span> <span data-ttu-id="ce3c3-132">Caso contrário, um novo objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="ce3c3-133">A implementação `GetInstance` é mostrada no seguinte código de amostra.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ce3c3-134">A `ReleaseInstance` implementação personalizada adiciona a instância liberada de `ActiveObjectsCount` volta ao pool e decreta o valor.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="ce3c3-135">É `Dispatcher` necessário chamar esses métodos de diferentes segmentos e, portanto, `ObjectPoolingInstanceProvider` é necessário acesso sincronizado aos membros do nível de classe na classe.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="ce3c3-136">O `ReleaseInstance` método fornece um recurso de "limpeza inicialização".</span><span class="sxs-lookup"><span data-stu-id="ce3c3-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="ce3c3-137">Normalmente, a piscina mantém um número mínimo de objetos durante a vida útil da piscina.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="ce3c3-138">No entanto, pode haver períodos de uso excessivo que requerem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="ce3c3-139">Eventualmente, quando a piscina se torna menos ativa, esses objetos excedentes podem se tornar uma sobrecarga extra.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="ce3c3-140">Portanto, quando `activeObjectsCount` o tempo chega a zero, é iniciado um temporizador ocioso que aciona e realiza um ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="ce3c3-141">Adicionando o Comportamento</span><span class="sxs-lookup"><span data-stu-id="ce3c3-141">Adding the Behavior</span></span>  
 <span data-ttu-id="ce3c3-142">As extensões da camada do despachante são ligadas usando os seguintes comportamentos:</span><span class="sxs-lookup"><span data-stu-id="ce3c3-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="ce3c3-143">Comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-143">Service Behaviors.</span></span> <span data-ttu-id="ce3c3-144">Isso permite a personalização de todo o tempo de execução do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="ce3c3-145">Comportamentos de ponto final.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-145">Endpoint Behaviors.</span></span> <span data-ttu-id="ce3c3-146">Estes permitem a personalização de pontos finais de serviço, especificamente um Despachante de Canais e Endpoint.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="ce3c3-147">Comportamentos contratuais.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-147">Contract Behaviors.</span></span> <span data-ttu-id="ce3c3-148">Estes permitem a personalização de ambos <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes sobre o cliente e o serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="ce3c3-149">Para efeitos de uma extensão de agrupamento de objetos, um comportamento de serviço deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="ce3c3-150">Os comportamentos de serviço são <xref:System.ServiceModel.Description.IServiceBehavior> criados implementando a interface.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="ce3c3-151">Existem várias maneiras de conscientizar o modelo de serviço sobre os comportamentos personalizados:</span><span class="sxs-lookup"><span data-stu-id="ce3c3-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="ce3c3-152">Usando um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="ce3c3-153">Adicioná-lo imperativamente à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="ce3c3-154">Estendendo o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="ce3c3-155">Esta amostra usa um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="ce3c3-156">Quando <xref:System.ServiceModel.ServiceHost> o é construído, examina os atributos utilizados na definição do tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="ce3c3-157">A <xref:System.ServiceModel.Description.IServiceBehavior> interface tem três métodos <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>nele <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>e.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="ce3c3-158">O <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> método é usado para garantir que o comportamento possa ser aplicado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="ce3c3-159">Nesta amostra, a implementação garante que o <xref:System.ServiceModel.InstanceContextMode.Single>serviço não esteja configurado com .</span><span class="sxs-lookup"><span data-stu-id="ce3c3-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="ce3c3-160">O <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> método é usado para configurar as vinculações do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="ce3c3-161">Não é necessário neste cenário.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-161">It is not required in this scenario.</span></span> <span data-ttu-id="ce3c3-162">O <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> é usado para configurar os despachantes do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="ce3c3-163">Este método é chamado pelo <xref:System.ServiceModel.ServiceHost> WCF quando o está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="ce3c3-164">Os seguintes parâmetros são passados para este método:</span><span class="sxs-lookup"><span data-stu-id="ce3c3-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="ce3c3-165">`Description`: Este argumento fornece a descrição do serviço para todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="ce3c3-166">Isso pode ser usado para inspecionar dados de descrição sobre os pontos finais do serviço, contratos, vinculações e outros dados.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="ce3c3-167">`ServiceHostBase`: Este argumento <xref:System.ServiceModel.ServiceHostBase> fornece o que está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="ce3c3-168">Na implementação <xref:System.ServiceModel.Description.IServiceBehavior> personalizada, `ObjectPoolingInstanceProvider` uma nova instância é instanciada e atribuída à <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada uma <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="ce3c3-169">Além de <xref:System.ServiceModel.Description.IServiceBehavior> uma <xref:System.EnterpriseServices.ObjectPoolingAttribute> implementação, a classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="ce3c3-170">Esses membros <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>incluem <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, e , para corresponder ao conjunto de recursos de pooling de objetos fornecido pelo .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="ce3c3-171">O comportamento de pooling de objetos agora pode ser adicionado a um serviço `ObjectPooling` WCF anotando a implementação do serviço com o atributo personalizado recém-criado.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="ce3c3-172">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="ce3c3-172">Running the Sample</span></span>  
 <span data-ttu-id="ce3c3-173">A amostra demonstra os benefícios de desempenho que podem ser obtidos usando o agrupamento de objetos em determinados cenários.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="ce3c3-174">O aplicativo de serviço implementa dois serviços -- `WorkService` e `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="ce3c3-175">Ambos os serviços compartilham a mesma implementação -- `DoWork()` ambos exigem inicialização cara e, em seguida, expõem um método que é relativamente barato.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="ce3c3-176">A única diferença `ObjectPooledWorkService` é que o pool de objetos está configurado:</span><span class="sxs-lookup"><span data-stu-id="ce3c3-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="ce3c3-177">Quando você executa o cliente, ele vezes liga ndo as `WorkService` 5 vezes.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="ce3c3-178">Em seguida, `ObjectPooledWorkService` vezes liga ndo as 5 vezes.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="ce3c3-179">A diferença de tempo é então exibida:</span><span class="sxs-lookup"><span data-stu-id="ce3c3-179">The difference in time is then displayed:</span></span>  
  
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
> <span data-ttu-id="ce3c3-180">A primeira vez que o cliente é executado ambos os serviços parecem levar cerca da mesma quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="ce3c3-181">Se você reexecutar a amostra, você `ObjectPooledWorkService` pode ver que o retorno muito mais rápido porque uma instância desse objeto já existe na piscina.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce3c3-182">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ce3c3-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ce3c3-183">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c3-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ce3c3-184">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c3-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ce3c3-185">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c3-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce3c3-186">Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce3c3-187">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce3c3-188">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ce3c3-189">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="ce3c3-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce3c3-190">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
