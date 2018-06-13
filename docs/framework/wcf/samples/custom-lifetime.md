---
title: tempo de vida personalizado
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: e41c970739b8036730fa601433ce7157e01d7e19
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809297"
---
# <a name="custom-lifetime"></a><span data-ttu-id="25ac0-102">tempo de vida personalizado</span><span class="sxs-lookup"><span data-stu-id="25ac0-102">Custom Lifetime</span></span>
<span data-ttu-id="25ac0-103">Este exemplo demonstra como escrever uma extensão do Windows Communication Foundation (WCF) para fornecer serviços de tempo de vida personalizado para instâncias de serviço compartilhados do WCF.</span><span class="sxs-lookup"><span data-stu-id="25ac0-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25ac0-104">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="25ac0-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="25ac0-105">Compartilhado de instanciação</span><span class="sxs-lookup"><span data-stu-id="25ac0-105">Shared Instancing</span></span>  
 <span data-ttu-id="25ac0-106">O WCF oferece vários modos de instância para suas instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="25ac0-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="25ac0-107">O modo compartilhado instanciação abordado neste tópico fornece uma maneira de compartilhar uma instância de serviço entre vários canais.</span><span class="sxs-lookup"><span data-stu-id="25ac0-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="25ac0-108">Os clientes podem resolver o endereço de ponto de extremidade da instância local ou entre em contato com um método de fábrica no serviço para obter o endereço de ponto de extremidade de uma instância em execução.</span><span class="sxs-lookup"><span data-stu-id="25ac0-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="25ac0-109">Depois que ele tem o endereço de ponto de extremidade, ele pode criar um novo canal e iniciar a comunicação.</span><span class="sxs-lookup"><span data-stu-id="25ac0-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="25ac0-110">O trecho de código a seguir mostra como um aplicativo cliente cria um novo canal para uma instância de serviço existente.</span><span class="sxs-lookup"><span data-stu-id="25ac0-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="25ac0-111">Ao contrário de outros modos de instância, o modo de instanciamento compartilhado tem forma singular de liberação as instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="25ac0-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="25ac0-112">Quando todos os canais são fechados para uma instância, o tempo de execução do serviço WCF inicia um cronômetro.</span><span class="sxs-lookup"><span data-stu-id="25ac0-112">When all the channels are closed for an instance, the service WCF runtime starts a timer.</span></span> <span data-ttu-id="25ac0-113">Se ninguém fizer uma conexão antes do tempo limite expirar, WCF libera a instância e as declarações de recursos.</span><span class="sxs-lookup"><span data-stu-id="25ac0-113">If nobody makes a connection before the timeout expires, WCF releases the instance and claims the resources.</span></span> <span data-ttu-id="25ac0-114">Como parte do procedimento subdivisão WCF chama o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método de todos os <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementações antes de liberar a instância.</span><span class="sxs-lookup"><span data-stu-id="25ac0-114">As a part of the teardown procedure WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="25ac0-115">Se todos eles retornarem `true` a instância é liberada.</span><span class="sxs-lookup"><span data-stu-id="25ac0-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="25ac0-116">Caso contrário, o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação é responsável por notificar o `Dispatcher` do estado ocioso, usando um método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="25ac0-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="25ac0-117">Por padrão, o valor de tempo limite de ociosidade de <xref:System.ServiceModel.InstanceContext> é um minuto.</span><span class="sxs-lookup"><span data-stu-id="25ac0-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="25ac0-118">No entanto, este exemplo demonstra como você pode estender esse usando uma extensão personalizada.</span><span class="sxs-lookup"><span data-stu-id="25ac0-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="25ac0-119">Estendendo o InstanceContext</span><span class="sxs-lookup"><span data-stu-id="25ac0-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="25ac0-120">No WCF, <xref:System.ServiceModel.InstanceContext> é o vínculo entre a instância de serviço e o `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-120">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="25ac0-121">WCF permite estender esse componente de tempo de execução, adicionando o novo estado ou comportamento usando o padrão de objeto extensível.</span><span class="sxs-lookup"><span data-stu-id="25ac0-121">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="25ac0-122">O padrão de objeto extensível é usado no WCF para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado para um objeto.</span><span class="sxs-lookup"><span data-stu-id="25ac0-122">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="25ac0-123">Existem três interfaces no padrão de objeto extensível: `IExtensibleObject<T>`, `IExtension<T>`, e `IExtensionCollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="25ac0-124">O `IExtensibleObject<T>` interface é implementada por objetos para permitir extensões que personalizar sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="25ac0-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="25ac0-125">O `IExtension<T>` interface é implementada por objetos que podem ser extensões de classes do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="25ac0-126">E, finalmente, o `IExtensionCollection<T>` interface é uma coleção de `IExtensions` que permite recuperar `IExtensions` por seu tipo.</span><span class="sxs-lookup"><span data-stu-id="25ac0-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="25ac0-127">Portanto, para estender o <xref:System.ServiceModel.InstanceContext> você deve implementar o `IExtension` interface.</span><span class="sxs-lookup"><span data-stu-id="25ac0-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="25ac0-128">Neste projeto de exemplo de `CustomLeaseExtension` classe contém essa implementação.</span><span class="sxs-lookup"><span data-stu-id="25ac0-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="25ac0-129">O `IExtension` interface tem dois métodos `Attach` e `Detach`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="25ac0-130">Como seus nomes sugerem, esses dois métodos são chamados quando o tempo de execução se conecta e desconecta a extensão a uma instância do <xref:System.ServiceModel.InstanceContext> classe.</span><span class="sxs-lookup"><span data-stu-id="25ac0-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="25ac0-131">Neste exemplo, o `Attach` método é usado para controlar o <xref:System.ServiceModel.InstanceContext> objeto ao qual pertence a instância atual da extensão.</span><span class="sxs-lookup"><span data-stu-id="25ac0-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="25ac0-132">Além disso, adicione a implementação necessária para a extensão para fornecer o suporte de tempo de vida estendida.</span><span class="sxs-lookup"><span data-stu-id="25ac0-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="25ac0-133">Portanto, o `ICustomLease` interface é declarada com os métodos desejados e é implementada no `CustomLeaseExtension` classe.</span><span class="sxs-lookup"><span data-stu-id="25ac0-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="25ac0-134">Quando o WCF chama o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação esta chamada é roteada para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-134">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="25ac0-135">Em seguida, o `CustomLeaseExtension` verifica seu estado particular para ver se o <xref:System.ServiceModel.InstanceContext> está ocioso.</span><span class="sxs-lookup"><span data-stu-id="25ac0-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="25ac0-136">Se ele estiver ocioso ele retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="25ac0-137">Caso contrário, ele inicia um temporizador para um determinado período de tempo de vida estendido.</span><span class="sxs-lookup"><span data-stu-id="25ac0-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 <span data-ttu-id="25ac0-138">Do timer `Elapsed` a função de retorno de chamada no Dispatcher de evento é chamada para iniciar outro ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="25ac0-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="25ac0-139">Não é possível renovar o timer de execução quando uma nova mensagem chega para a instância que está sendo movida para o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="25ac0-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="25ac0-140">O exemplo implementa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> para interceptar as chamadas para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> rota e o método para o `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="25ac0-141">O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação está contida no `CustomLifetimeLease` classe.</span><span class="sxs-lookup"><span data-stu-id="25ac0-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="25ac0-142">O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método é invocado quando o WCF está prestes a liberar a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="25ac0-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="25ac0-143">No entanto, há apenas uma instância de um determinado `ISharedSessionInstance` implementação no ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> coleção.</span><span class="sxs-lookup"><span data-stu-id="25ac0-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="25ac0-144">Isso significa que não há maneira de saber o <xref:System.ServiceModel.InstanceContext> que está sendo fechado no momento WCF verifica o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="25ac0-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="25ac0-145">Portanto, este exemplo usa o thread para serializar as solicitações de bloqueio de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="25ac0-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="25ac0-146">Usando o bloqueio de thread não é uma abordagem recomendada porque a serialização pode afetar seriamente o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25ac0-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="25ac0-147">Uma variável de membro privado é usada no `CustomLeaseExtension` classe para rastrear o `IsIdle` valor.</span><span class="sxs-lookup"><span data-stu-id="25ac0-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="25ac0-148">Cada vez que o valor de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> é recuperado do `IsIdle` membro privado é retornado e redefinir a `false`.</span><span class="sxs-lookup"><span data-stu-id="25ac0-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="25ac0-149">É essencial para definir esse valor como `false` para garantir que as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="25ac0-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="25ac0-150">Se o `ISharedSessionLifetime.IsIdle` propriedade retorna `false` o Dispatcher registra uma função de retorno de chamada usando o `NotifyIdle` método.</span><span class="sxs-lookup"><span data-stu-id="25ac0-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="25ac0-151">Este método recebe uma referência para o <xref:System.ServiceModel.InstanceContext> sendo lançada.</span><span class="sxs-lookup"><span data-stu-id="25ac0-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="25ac0-152">Portanto o código de exemplo pode consultar o `ICustomLease` tipo de extensão e verifique o `ICustomLease.IsIdle` propriedade no estado estendido.</span><span class="sxs-lookup"><span data-stu-id="25ac0-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 <span data-ttu-id="25ac0-153">Antes do `ICustomLease.IsIdle` propriedade estiver marcada, a propriedade de retorno de chamada precisa ser definida como isso é essencial para `CustomLeaseExtension` para notificar o Dispatcher quando ele estiver ocioso.</span><span class="sxs-lookup"><span data-stu-id="25ac0-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="25ac0-154">Se `ICustomLease.IsIdle` retorna `true`, o `isIdle` membro privado simplesmente é definido `CustomLifetimeLease` para `true` e chama o método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="25ac0-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="25ac0-155">Como o código mantém um bloqueio, outros threads não é possível alterar o valor desse membro privado.</span><span class="sxs-lookup"><span data-stu-id="25ac0-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="25ac0-156">E na próxima vez em que o distribuidor verifica o `ISharedSessionLifetime.IsIdle`, ele retorna `true` e permite que o Dispatcher liberar a instância.</span><span class="sxs-lookup"><span data-stu-id="25ac0-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="25ac0-157">Agora que a base para a extensão personalizada é concluída, ele deve ser vinculada ao modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="25ac0-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="25ac0-158">Para ligar o `CustomLeaseExtension` implementação para o <xref:System.ServiceModel.InstanceContext>, o WCF fornece o <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> para executar a inicialização de <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="25ac0-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="25ac0-159">No exemplo, o `CustomLeaseInitializer` classe implementa essa interface e adiciona uma instância de `CustomLeaseExtension` para o <xref:System.ServiceModel.InstanceContext.Extensions%2A> coleção de inicialização o único método.</span><span class="sxs-lookup"><span data-stu-id="25ac0-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="25ac0-160">Este método é chamado pelo Dispatcher ao inicializar o <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="25ac0-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="25ac0-161">Por fim o `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` e <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> são implementações é gancho até o modelo de serviço usando o <xref:System.ServiceModel.Description.IServiceBehavior> implementação.</span><span class="sxs-lookup"><span data-stu-id="25ac0-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="25ac0-162">Essa implementação é colocada no `CustomLeaseTimeAttribute` classe e ele também deriva o `Attribute` classe para expor esse comportamento como um atributo base.</span><span class="sxs-lookup"><span data-stu-id="25ac0-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="25ac0-163">No `IServiceBehavior.ApplyBehavior` método, instâncias de <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> e `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementações são adicionadas para o `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` e <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> coleções do <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectivamente.</span><span class="sxs-lookup"><span data-stu-id="25ac0-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="25ac0-164">Esse comportamento pode ser adicionado a uma classe de serviço de exemplo, anotando-o com o `CustomLeaseTime` atributo.</span><span class="sxs-lookup"><span data-stu-id="25ac0-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="25ac0-165">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="25ac0-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="25ac0-166">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="25ac0-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="25ac0-167">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="25ac0-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="25ac0-168">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25ac0-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="25ac0-169">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25ac0-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="25ac0-170">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25ac0-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="25ac0-171">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="25ac0-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="25ac0-172">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="25ac0-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="25ac0-173">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="25ac0-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25ac0-174">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="25ac0-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="25ac0-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25ac0-175">See Also</span></span>
