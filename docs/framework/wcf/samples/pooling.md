---
title: Agrupamento
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 6554ec9c5eaefaf8c9e39d2a8d92982716cc18c5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809814"
---
# <a name="pooling"></a><span data-ttu-id="5c792-102">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="5c792-102">Pooling</span></span>
<span data-ttu-id="5c792-103">Este exemplo demonstra como estender o Windows Communication Foundation (WCF) para dar suporte a pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="5c792-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="5c792-104">O exemplo demonstra como criar um atributo que é sintaticamente e semanticamente semelhante do `ObjectPoolingAttribute` funcionalidade de serviços corporativos de atributo.</span><span class="sxs-lookup"><span data-stu-id="5c792-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="5c792-105">Pool de objetos pode fornecer um aumento significativo no desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c792-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="5c792-106">No entanto, ele pode ter o efeito oposto, se ele não está sendo usado corretamente.</span><span class="sxs-lookup"><span data-stu-id="5c792-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="5c792-107">Pool de objetos ajuda a reduzir a sobrecarga de recriar os objetos usados com frequência que requerem inicialização ampla.</span><span class="sxs-lookup"><span data-stu-id="5c792-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="5c792-108">No entanto, se uma chamada para um método em um objeto de pool leva uma quantidade considerável de tempo para concluir, pool de objetos enfileira solicitações adicionais assim que o tamanho máximo do pool for atingido.</span><span class="sxs-lookup"><span data-stu-id="5c792-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="5c792-109">Portanto, pode falhar atender solicitações de criação de um objeto lançando uma exceção de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5c792-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c792-110">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5c792-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5c792-111">A primeira etapa na criação de uma extensão do WCF é decidir o ponto de extensibilidade para usar.</span><span class="sxs-lookup"><span data-stu-id="5c792-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="5c792-112">No WCF o termo *dispatcher* refere-se a um componente de tempo de execução responsável pela conversão de mensagens de entrada em invocações do método no serviço do usuário e para converter valores de retorno de método em uma mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="5c792-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="5c792-113">Um serviço WCF cria um dispatcher para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5c792-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="5c792-114">Um cliente WCF deve usar um distribuidor se o contrato associado com esse cliente é um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="5c792-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="5c792-115">Os distribuidores de canal e o ponto de extremidade oferecem canal- e extensibilidade de todo o contrato ao expor várias propriedades que controlam o comportamento do dispatcher.</span><span class="sxs-lookup"><span data-stu-id="5c792-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="5c792-116">O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> propriedade também permite que você inspecione, modificar ou personalizar o processo de distribuição.</span><span class="sxs-lookup"><span data-stu-id="5c792-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="5c792-117">Este exemplo enfoca o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="5c792-118">O IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="5c792-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="5c792-119">No WCF, o dispatcher cria instâncias de classe de serviço usando um <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, que implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span><span class="sxs-lookup"><span data-stu-id="5c792-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="5c792-120">Essa interface possui três métodos:</span><span class="sxs-lookup"><span data-stu-id="5c792-120">This interface has three methods:</span></span>  
  
-   <span data-ttu-id="5c792-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Quando uma mensagem chega as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método para criar uma instância da classe de serviço para processar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="5c792-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="5c792-122">A frequência de chamadas a este método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5c792-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="5c792-123">Por exemplo, se o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> está definida como <xref:System.ServiceModel.InstanceContextMode.PerCall> uma nova instância da classe de serviço é criada para processar cada mensagem que chega, isso <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> é chamado sempre que uma mensagem chega.</span><span class="sxs-lookup"><span data-stu-id="5c792-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="5c792-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Isso é idêntico ao método anterior, exceto que isso é invocado quando não há nenhum argumento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5c792-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
-   <span data-ttu-id="5c792-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Quando decorrido o tempo de vida de uma instância serviço, as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> método.</span><span class="sxs-lookup"><span data-stu-id="5c792-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="5c792-126">Assim como para o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método, a frequência de chamadas a este método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5c792-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="5c792-127">O Pool de objetos</span><span class="sxs-lookup"><span data-stu-id="5c792-127">The Object Pool</span></span>  
 <span data-ttu-id="5c792-128">Um personalizado <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação fornece o objeto necessário pooling semântica para um serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="5c792-129">Portanto, este exemplo tem um `ObjectPoolingInstanceProvider` tipo que fornece uma implementação personalizada de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> para o pool.</span><span class="sxs-lookup"><span data-stu-id="5c792-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="5c792-130">Quando o `Dispatcher` chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória.</span><span class="sxs-lookup"><span data-stu-id="5c792-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="5c792-131">Se houver um disponível, ele será retornado.</span><span class="sxs-lookup"><span data-stu-id="5c792-131">If one is available, it is returned.</span></span> <span data-ttu-id="5c792-132">Caso contrário, um novo objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5c792-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="5c792-133">A implementação para `GetInstance` é mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c792-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="5c792-134">Personalizado `ReleaseInstance` implementação adiciona a instância liberada para o pool e diminui o `ActiveObjectsCount` valor.</span><span class="sxs-lookup"><span data-stu-id="5c792-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="5c792-135">O `Dispatcher` pode chamar esses métodos de diversos threads e sincronizado, portanto, o acesso a membros de nível de classe no `ObjectPoolingInstanceProvider` classe é necessária.</span><span class="sxs-lookup"><span data-stu-id="5c792-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```  
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
  
 <span data-ttu-id="5c792-136">O `ReleaseInstance` método fornece um recurso de "Limpar inicialização".</span><span class="sxs-lookup"><span data-stu-id="5c792-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="5c792-137">Normalmente o pool mantém um número mínimo de objetos para o tempo de vida do pool.</span><span class="sxs-lookup"><span data-stu-id="5c792-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="5c792-138">No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="5c792-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="5c792-139">Finalmente, quando o pool se torna menos ativo, esses objetos excedentes podem se tornar uma sobrecarga extra.</span><span class="sxs-lookup"><span data-stu-id="5c792-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="5c792-140">Portanto, quando o `activeObjectsCount` atingir zero, um timer de ociosidade é iniciado, gatilhos e executa um ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="5c792-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="5c792-141">Adicionando o comportamento</span><span class="sxs-lookup"><span data-stu-id="5c792-141">Adding the Behavior</span></span>  
 <span data-ttu-id="5c792-142">Extensões de camada do Dispatcher são conectadas usando os seguintes comportamentos:</span><span class="sxs-lookup"><span data-stu-id="5c792-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="5c792-143">Comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-143">Service Behaviors.</span></span> <span data-ttu-id="5c792-144">Eles permitem a personalização do tempo de execução de todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-144">These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="5c792-145">Comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5c792-145">Endpoint Behaviors.</span></span> <span data-ttu-id="5c792-146">Isso permite a personalização de pontos de extremidade de serviço, especificamente um canal e o Dispatcher do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5c792-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
-   <span data-ttu-id="5c792-147">Comportamentos de contrato.</span><span class="sxs-lookup"><span data-stu-id="5c792-147">Contract Behaviors.</span></span> <span data-ttu-id="5c792-148">Eles permitem a personalização de ambos <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes no cliente e o serviço, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5c792-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="5c792-149">Com a finalidade de um objeto de extensão do pool um comportamento de serviço deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="5c792-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="5c792-150">Comportamentos de serviço são criados com a implementação de <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span><span class="sxs-lookup"><span data-stu-id="5c792-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="5c792-151">Há várias maneiras de tornar o modelo de serviço com reconhecimento de comportamentos personalizados:</span><span class="sxs-lookup"><span data-stu-id="5c792-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="5c792-152">Usando um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5c792-152">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="5c792-153">Imperativa adicionado à coleção de comportamentos da descrição de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="5c792-154">Extensão do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5c792-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="5c792-155">Este exemplo usa um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5c792-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="5c792-156">Quando o <xref:System.ServiceModel.ServiceHost> é criado ele examina os atributos usados na definição de tipo de serviço e adiciona os comportamentos disponíveis para a coleção de comportamentos da descrição de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="5c792-157">A interface <xref:System.ServiceModel.Description.IServiceBehavior> tem três métodos em-- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c792-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="5c792-158">O <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> método é usado para garantir que o comportamento pode ser aplicado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="5c792-159">Neste exemplo, a implementação garante que o serviço não está configurado com <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="5c792-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="5c792-160">O <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> método é usado para configurar as ligações de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="5c792-161">Não é necessário neste cenário.</span><span class="sxs-lookup"><span data-stu-id="5c792-161">It is not required in this scenario.</span></span> <span data-ttu-id="5c792-162">O <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> é usado para configurar os distribuidores do serviço.</span><span class="sxs-lookup"><span data-stu-id="5c792-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="5c792-163">Este método é chamado pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="5c792-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="5c792-164">Os seguintes parâmetros são passados para este método:</span><span class="sxs-lookup"><span data-stu-id="5c792-164">The following parameters are passed into this method:</span></span>  
  
-   <span data-ttu-id="5c792-165">`Description`: Este argumento fornece a descrição do serviço para o serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="5c792-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="5c792-166">Isso pode ser usado para inspecionar dados descrição sobre pontos de extremidade do serviço e outros dados, associações e contratos.</span><span class="sxs-lookup"><span data-stu-id="5c792-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
-   <span data-ttu-id="5c792-167">`ServiceHostBase`: Este argumento fornece o <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializado.</span><span class="sxs-lookup"><span data-stu-id="5c792-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="5c792-168">Em personalizado <xref:System.ServiceModel.Description.IServiceBehavior> uma nova instância da implementação de `ObjectPoolingInstanceProvider` é criada e atribuída ao <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada <xref:System.ServiceModel.Dispatcher.DispatchRuntime> em ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="5c792-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```  
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
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
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
  
 <span data-ttu-id="5c792-169">Além de um <xref:System.ServiceModel.Description.IServiceBehavior> implementação o <xref:System.EnterpriseServices.ObjectPoolingAttribute> classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo.</span><span class="sxs-lookup"><span data-stu-id="5c792-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="5c792-170">Esses membros incluem <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, e <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, para coincidir com o conjunto de recursos fornecido pelo .NET Enterprise Services ao pool de objetos.</span><span class="sxs-lookup"><span data-stu-id="5c792-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="5c792-171">O comportamento de pooling de objeto pode ser adicionado a um serviço WCF, anotando a implementação do serviço com o recém-criado personalizado `ObjectPooling` atributo.</span><span class="sxs-lookup"><span data-stu-id="5c792-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="5c792-172">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="5c792-172">Running the Sample</span></span>  
 <span data-ttu-id="5c792-173">O exemplo demonstra os benefícios de desempenho que podem ser obtidos usando o pool de objetos em determinados cenários.</span><span class="sxs-lookup"><span data-stu-id="5c792-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="5c792-174">O aplicativo de serviço implementa dois serviços – `WorkService` e `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="5c792-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="5c792-175">Os serviços compartilham a mesma implementação – eles requerem inicialização cara tanto expõem um `DoWork()` método que é relativamente barato.</span><span class="sxs-lookup"><span data-stu-id="5c792-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="5c792-176">A única diferença é que o `ObjectPooledWorkService` tem o pool de objetos configurados:</span><span class="sxs-lookup"><span data-stu-id="5c792-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```  
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
  
 <span data-ttu-id="5c792-177">Quando você executa o cliente, o tempo que chama o `WorkService` 5 vezes.</span><span class="sxs-lookup"><span data-stu-id="5c792-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="5c792-178">Tempo, em seguida, chamar o `ObjectPooledWorkService` 5 vezes.</span><span class="sxs-lookup"><span data-stu-id="5c792-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="5c792-179">A diferença de tempo, em seguida, é exibida:</span><span class="sxs-lookup"><span data-stu-id="5c792-179">The difference in time is then displayed:</span></span>  
  
```  
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
>  <span data-ttu-id="5c792-180">Na primeira vez em que o cliente é executar ambos os serviços parecem levar aproximadamente a mesma quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="5c792-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="5c792-181">Se você executar novamente o exemplo, você pode ver que o `ObjectPooledWorkService` retorna muito mais rápida porque já existe uma instância desse objeto no pool.</span><span class="sxs-lookup"><span data-stu-id="5c792-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c792-182">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5c792-182">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5c792-183">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c792-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5c792-184">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c792-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5c792-185">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c792-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c792-186">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="5c792-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c792-187">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5c792-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c792-188">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5c792-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5c792-189">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5c792-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c792-190">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5c792-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a><span data-ttu-id="5c792-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c792-191">See Also</span></span>
