---
title: Tempo de vida personalizado
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715474"
---
# <a name="custom-lifetime"></a><span data-ttu-id="0b9ba-102">Tempo de vida personalizado</span><span class="sxs-lookup"><span data-stu-id="0b9ba-102">Custom lifetime</span></span>

<span data-ttu-id="0b9ba-103">Este exemplo demonstra como gravar uma extensão de Windows Communication Foundation (WCF) para fornecer serviços de tempo de vida personalizados para instâncias de serviço WCF compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="0b9ba-104">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste artigo.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="0b9ba-105">Instanciação compartilhada</span><span class="sxs-lookup"><span data-stu-id="0b9ba-105">Shared instancing</span></span>

<span data-ttu-id="0b9ba-106">O WCF oferece vários modos de instanciação para suas instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="0b9ba-107">O modo de instanciação compartilhado abordado neste artigo fornece uma maneira de compartilhar uma instância de serviço entre vários canais.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="0b9ba-108">Os clientes podem contatar um método de fábrica no serviço e criar um novo canal para iniciar a comunicação.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="0b9ba-109">O trecho de código a seguir mostra como um aplicativo cliente cria um novo canal para uma instância de serviço existente:</span><span class="sxs-lookup"><span data-stu-id="0b9ba-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="0b9ba-110">Ao contrário de outros modos de instanciação, o modo de instanciação compartilhado tem uma maneira exclusiva de liberar as instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="0b9ba-111">Por padrão, quando todos os canais são fechados para um <xref:System.ServiceModel.InstanceContext>, o tempo de execução do serviço WCF verifica se o <xref:System.ServiceModel.InstanceContextMode> de serviço está configurado para <xref:System.ServiceModel.InstanceContextMode.PerCall> ou <xref:System.ServiceModel.InstanceContextMode.PerSession>e, em caso afirmativo, libera a instância e declara os recursos.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="0b9ba-112">Se um <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> personalizado estiver sendo usado, o WCF invocará o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> da implementação do provedor antes de liberar a instância.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="0b9ba-113">Se <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> retornar `true` a instância será liberada, caso contrário, a implementação de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> será responsável por notificar a `Dispatcher` do estado ocioso usando um método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="0b9ba-114">Isso é feito chamando o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> do provedor.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="0b9ba-115">Este exemplo demonstra como você pode atrasar a liberação do <xref:System.ServiceModel.InstanceContext> com um tempo limite de ociosidade de 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="0b9ba-116">Estendendo o InstanceContext</span><span class="sxs-lookup"><span data-stu-id="0b9ba-116">Extending the InstanceContext</span></span>

<span data-ttu-id="0b9ba-117">No WCF, <xref:System.ServiceModel.InstanceContext> é o vínculo entre a instância do serviço e o `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="0b9ba-118">O WCF permite que você estenda esse componente de tempo de execução adicionando um novo estado ou comportamento usando seu padrão de objeto extensível.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="0b9ba-119">O padrão de objeto extensível é usado no WCF para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado a um objeto.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="0b9ba-120">Há três interfaces no padrão de objeto extensível: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>e <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="0b9ba-121">A interface <xref:System.ServiceModel.IExtensibleObject%601> é implementada por objetos para permitir extensões que personalizam sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="0b9ba-122">A interface <xref:System.ServiceModel.IExtension%601> é implementada por objetos que podem ser extensões de classes do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="0b9ba-123">E, finalmente, a interface <xref:System.ServiceModel.IExtensionCollection%601> é uma coleção de implementações de <xref:System.ServiceModel.IExtension%601> que permite recuperar uma implementação de <xref:System.ServiceModel.IExtension%601> por seu tipo.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="0b9ba-124">Portanto, para estender o <xref:System.ServiceModel.InstanceContext>, você deve implementar a interface <xref:System.ServiceModel.IExtension%601>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="0b9ba-125">Neste projeto de exemplo, a classe `CustomLeaseExtension` contém essa implementação.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="0b9ba-126">A interface <xref:System.ServiceModel.IExtension%601> tem dois métodos <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="0b9ba-127">Como seus nomes sugerem, esses dois métodos são chamados quando o tempo de execução anexa e desanexa a extensão a uma instância da classe <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="0b9ba-128">Neste exemplo, o método `Attach` é usado para controlar o objeto <xref:System.ServiceModel.InstanceContext> que pertence à instância atual da extensão.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="0b9ba-129">Além disso, você deve adicionar a implementação necessária à extensão para fornecer o suporte estendido ao tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="0b9ba-130">Portanto, a interface `ICustomLease` é declarada com os métodos desejados e é implementada na classe `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="0b9ba-131">Quando o WCF chama o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> na implementação de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, essa chamada é roteada para o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="0b9ba-132">Em seguida, o `CustomLeaseExtension` verifica seu estado particular para ver se o <xref:System.ServiceModel.InstanceContext> está ocioso.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="0b9ba-133">Se estiver ocioso, ele retornará `true`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="0b9ba-134">Caso contrário, ele iniciará um temporizador para uma quantidade especificada de tempo de vida estendido.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
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

<span data-ttu-id="0b9ba-135">No evento `Elapsed` do temporizador, a função de retorno de chamada no Dispatcher é chamada para iniciar outro ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="0b9ba-136">Não há como renovar o temporizador em execução quando uma nova mensagem chega à instância que está sendo movida para o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="0b9ba-137">O exemplo implementa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> para interceptar as chamadas para o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> e roteá-las para o `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="0b9ba-138">A implementação de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> está contida na classe `CustomLifetimeLease`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="0b9ba-139">O método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> é invocado quando o WCF está prestes a liberar a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="0b9ba-140">No entanto, há apenas uma instância de uma implementação de `ISharedSessionInstance` específica na coleção de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> do serviceInstance.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="0b9ba-141">Isso significa que não há como saber se o <xref:System.ServiceModel.InstanceContext> está fechado no momento em que o WCF verifica o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="0b9ba-142">Portanto, este exemplo usa o bloqueio de thread para serializar solicitações para o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b9ba-143">Usar o bloqueio de thread não é uma abordagem recomendada porque a serialização pode afetar seriamente o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="0b9ba-144">Um campo de membro privado é usado na classe `CustomLifetimeLease` para acompanhar o estado ocioso e é retornado pelo método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="0b9ba-145">Cada vez que o método de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> é chamado, o campo `isIdle` é retornado e redefinido como `false`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="0b9ba-146">É essencial definir esse valor como `false` para garantir que o Dispatcher chame o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="0b9ba-147">Se o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> retornar `false`, o Dispatcher registrará uma função de retorno de chamada usando o método <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="0b9ba-148">Esse método recebe uma referência para o <xref:System.ServiceModel.InstanceContext> que está sendo liberado.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="0b9ba-149">Portanto, o código de exemplo pode consultar a extensão de tipo de `ICustomLease` e verificar a propriedade `ICustomLease.IsIdle` no estado estendido.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
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

<span data-ttu-id="0b9ba-150">Antes que a propriedade `ICustomLease.IsIdle` seja marcada, a propriedade de retorno de chamada precisa ser definida, pois isso é essencial para `CustomLeaseExtension` notificar o Dispatcher quando ele se tornar ocioso.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="0b9ba-151">Se `ICustomLease.IsIdle` retornar `true`, o membro privado `isIdle` será simplesmente definido em `CustomLifetimeLease` para `true` e chamará o método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="0b9ba-152">Como o código mantém um bloqueio, outros threads não podem alterar o valor desse membro privado.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="0b9ba-153">E, na próxima vez que o Dispatcher chamar o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, ele retornará `true` e permitirá que o Dispatcher libere a instância.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="0b9ba-154">Agora que a base para a extensão personalizada foi concluída, ela precisa ser conectada ao modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="0b9ba-155">Para conectar a implementação de `CustomLeaseExtension` ao <xref:System.ServiceModel.InstanceContext>, o WCF fornece a interface de <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> para executar a inicialização de <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="0b9ba-156">No exemplo, a classe `CustomLeaseInitializer` implementa essa interface e adiciona uma instância de `CustomLeaseExtension` à coleção de <xref:System.ServiceModel.InstanceContext.Extensions%2A> da única inicialização do método.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="0b9ba-157">Esse método é chamado pelo Dispatcher ao inicializar o <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="0b9ba-158">Por fim, a implementação de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> é conectada ao modelo de serviço usando a implementação <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="0b9ba-159">Essa implementação é colocada na classe `CustomLeaseTimeAttribute` e também deriva da classe base <xref:System.Attribute> para expor esse comportamento como um atributo.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="0b9ba-160">Esse comportamento pode ser adicionado a uma classe de serviço de exemplo, anotando-o com o atributo `CustomLeaseTime`.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="0b9ba-161">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0b9ba-162">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b9ba-163">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0b9ba-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0b9ba-164">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b9ba-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0b9ba-165">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b9ba-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="0b9ba-166">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b9ba-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b9ba-167">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b9ba-168">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0b9ba-169">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b9ba-170">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0b9ba-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
