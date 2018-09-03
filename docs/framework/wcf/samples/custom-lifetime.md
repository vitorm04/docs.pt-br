---
title: Tempo de vida personalizado
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1946608c69401fb08f6eb458a8adabea24563963
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467740"
---
# <a name="custom-lifetime"></a><span data-ttu-id="b8209-102">Tempo de vida personalizado</span><span class="sxs-lookup"><span data-stu-id="b8209-102">Custom lifetime</span></span>

<span data-ttu-id="b8209-103">Este exemplo demonstra como escrever uma extensão do Windows Communication Foundation (WCF) para fornecer serviços de tempo de vida personalizado para instâncias de serviço compartilhados do WCF.</span><span class="sxs-lookup"><span data-stu-id="b8209-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="b8209-104">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste artigo.</span><span class="sxs-lookup"><span data-stu-id="b8209-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="b8209-105">Compartilhado de instanciação</span><span class="sxs-lookup"><span data-stu-id="b8209-105">Shared instancing</span></span>

<span data-ttu-id="b8209-106">O WCF oferece vários modos de instanciação para suas instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="b8209-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="b8209-107">O modo de instanciação compartilhado abordado neste artigo fornece uma maneira de compartilhar uma instância de serviço entre os vários canais.</span><span class="sxs-lookup"><span data-stu-id="b8209-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="b8209-108">Os clientes possam entre em contato com um método de fábrica no serviço e criar um novo canal para iniciar a comunicação.</span><span class="sxs-lookup"><span data-stu-id="b8209-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="b8209-109">O trecho de código a seguir mostra como um aplicativo cliente cria um novo canal para uma instância de serviço existente:</span><span class="sxs-lookup"><span data-stu-id="b8209-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

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

<span data-ttu-id="b8209-110">Ao contrário de outros modos de instanciação, o modo de instanciação compartilhado tem uma maneira exclusiva de liberar as instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="b8209-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="b8209-111">Por padrão, quando todos os canais são fechados para um <xref:System.ServiceModel.InstanceContext>, o tempo de execução do serviço WCF verifica se o serviço <xref:System.ServiceModel.InstanceContextMode> é configurado para <xref:System.ServiceModel.InstanceContextMode.PerCall> ou <xref:System.ServiceModel.InstanceContextMode.PerSession>e se então libera a instância e os recursos de declarações.</span><span class="sxs-lookup"><span data-stu-id="b8209-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="b8209-112">Se um personalizado <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> está sendo usado, o WCF chama o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método da implementação do provedor antes de liberar a instância.</span><span class="sxs-lookup"><span data-stu-id="b8209-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="b8209-113">Se <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> retorna `true` a instância é liberada, caso contrário, o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação é responsável por notificar a `Dispatcher` do estado ocioso, usando um método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b8209-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="b8209-114">Isso é feito chamando o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método do provedor.</span><span class="sxs-lookup"><span data-stu-id="b8209-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="b8209-115">Este exemplo demonstra como você pode atrasar a liberar o <xref:System.ServiceModel.InstanceContext> com um tempo limite de ociosidade de 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="b8209-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="b8209-116">Estendendo o InstanceContext</span><span class="sxs-lookup"><span data-stu-id="b8209-116">Extending the InstanceContext</span></span>

<span data-ttu-id="b8209-117">No WCF, <xref:System.ServiceModel.InstanceContext> é o vínculo entre a instância de serviço e o `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="b8209-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="b8209-118">O WCF permite que você estenda este componente de tempo de execução, adicionando o novo estado ou comportamento por meio de seu padrão de objeto extensível.</span><span class="sxs-lookup"><span data-stu-id="b8209-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="b8209-119">O padrão de objeto extensível é usado no WCF para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado para um objeto.</span><span class="sxs-lookup"><span data-stu-id="b8209-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="b8209-120">Existem três interfaces no padrão de objeto extensível: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, e <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="b8209-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="b8209-121">O <xref:System.ServiceModel.IExtensibleObject%601> interface é implementada por objetos para permitir que as extensões que personalizar sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="b8209-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="b8209-122">O <xref:System.ServiceModel.IExtension%601> interface é implementada por objetos que podem ser extensões de classes do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="b8209-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="b8209-123">E, finalmente, o <xref:System.ServiceModel.IExtensionCollection%601> interface é uma coleção de <xref:System.ServiceModel.IExtension%601> implementações que permite a recuperação de uma implementação de <xref:System.ServiceModel.IExtension%601> por tipo.</span><span class="sxs-lookup"><span data-stu-id="b8209-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="b8209-124">Portanto, para estender a <xref:System.ServiceModel.InstanceContext>, você deve implementar o <xref:System.ServiceModel.IExtension%601> interface.</span><span class="sxs-lookup"><span data-stu-id="b8209-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="b8209-125">Neste projeto de exemplo, o `CustomLeaseExtension` classe contém essa implementação.</span><span class="sxs-lookup"><span data-stu-id="b8209-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="b8209-126">O <xref:System.ServiceModel.IExtension%601> interface tem dois métodos <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8209-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="b8209-127">Como seus nomes já dizem, esses dois métodos são chamados quando o tempo de execução anexa e Desanexa a extensão a uma instância da <xref:System.ServiceModel.InstanceContext> classe.</span><span class="sxs-lookup"><span data-stu-id="b8209-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="b8209-128">Neste exemplo, o `Attach` método é usado para controlar o <xref:System.ServiceModel.InstanceContext> objeto ao qual pertence a instância atual da extensão.</span><span class="sxs-lookup"><span data-stu-id="b8209-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="b8209-129">Além disso, você deve adicionar a implementação necessária para a extensão para fornecer o suporte estendido do tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="b8209-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="b8209-130">Portanto, o `ICustomLease` interface é declarado com os métodos desejados e é implementado de `CustomLeaseExtension` classe.</span><span class="sxs-lookup"><span data-stu-id="b8209-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

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

<span data-ttu-id="b8209-131">Quando o WCF chama o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método na <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação, essa chamada for roteada para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método da `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="b8209-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="b8209-132">Em seguida, o `CustomLeaseExtension` verifica o estado particular para ver se o <xref:System.ServiceModel.InstanceContext> está ocioso.</span><span class="sxs-lookup"><span data-stu-id="b8209-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="b8209-133">Se estiver ocioso, ele retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="b8209-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="b8209-134">Caso contrário, ele inicia um cronômetro para um determinado período de tempo de vida estendido.</span><span class="sxs-lookup"><span data-stu-id="b8209-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

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

<span data-ttu-id="b8209-135">Do timer `Elapsed` evento, a função de retorno de chamada no Dispatcher é chamada para iniciar outro ciclo de limpeza.</span><span class="sxs-lookup"><span data-stu-id="b8209-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

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

<span data-ttu-id="b8209-136">Não é possível renovar o temporizador em execução quando uma nova mensagem chega para a instância que está sendo movida para o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="b8209-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="b8209-137">A amostra implementa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> interceptar as chamadas para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método e a rota para o `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="b8209-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="b8209-138">O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação está contida no `CustomLifetimeLease` classe.</span><span class="sxs-lookup"><span data-stu-id="b8209-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="b8209-139">O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método é invocado quando o WCF está prestes a liberar a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="b8209-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="b8209-140">No entanto, há apenas uma instância de um determinado `ISharedSessionInstance` implementação no ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> coleção.</span><span class="sxs-lookup"><span data-stu-id="b8209-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="b8209-141">Isso significa que não há nenhuma maneira de saber se o <xref:System.ServiceModel.InstanceContext> é fechada no momento em que o WCF verifica o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b8209-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="b8209-142">Portanto, este exemplo usa o thread de bloqueio para serializar as solicitações para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b8209-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8209-143">Usando o bloqueio de thread não é uma abordagem recomendada porque a serialização pode afetar gravemente o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8209-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="b8209-144">Um campo de membro privado é usado na `CustomLifetimeLease` de classe para controlar o estado ocioso e é retornado pelo <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b8209-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="b8209-145">Cada vez que o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método é chamado, o `isIdle` campo é retornado e redefinido como `false`.</span><span class="sxs-lookup"><span data-stu-id="b8209-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="b8209-146">É essencial para definir esse valor como `false` para garantir que as chamadas de Dispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b8209-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

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

<span data-ttu-id="b8209-147">Se o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> retorn `false`, o Dispatcher registra uma função de retorno de chamada usando o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b8209-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="b8209-148">Esse método recebe uma referência para o <xref:System.ServiceModel.InstanceContext> sendo lançada.</span><span class="sxs-lookup"><span data-stu-id="b8209-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="b8209-149">Portanto, o código de exemplo pode consultar a `ICustomLease` digite a extensão e marque o `ICustomLease.IsIdle` propriedade no estado estendido.</span><span class="sxs-lookup"><span data-stu-id="b8209-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

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

<span data-ttu-id="b8209-150">Antes do `ICustomLease.IsIdle` propriedade estiver marcada, a propriedade de retorno de chamada precisa ser definido como isso é essencial para `CustomLeaseExtension` para notificar o Dispatcher quando ele se torna ocioso.</span><span class="sxs-lookup"><span data-stu-id="b8209-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="b8209-151">Se `ICustomLease.IsIdle` retorna `true`, o `isIdle` membro privado é simplesmente definido `CustomLifetimeLease` para `true` e chama o método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b8209-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="b8209-152">Como o código mantém um bloqueio, outros threads não é possível alterar o valor desse membro privado.</span><span class="sxs-lookup"><span data-stu-id="b8209-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="b8209-153">E na próxima vez em que o Dispatcher chama a <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, ele retorna `true` e permite que o Dispatcher liberar a instância.</span><span class="sxs-lookup"><span data-stu-id="b8209-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="b8209-154">Agora que as bases para a extensão personalizada for concluída, ele deve ser vinculada ao modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="b8209-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="b8209-155">Para ligar os `CustomLeaseExtension` implementação para o <xref:System.ServiceModel.InstanceContext>, o WCF fornece o <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface para executar a inicialização de <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="b8209-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="b8209-156">No exemplo, o `CustomLeaseInitializer` classe implementa essa interface e adiciona uma instância do `CustomLeaseExtension` para o <xref:System.ServiceModel.InstanceContext.Extensions%2A> coleção da inicialização único método.</span><span class="sxs-lookup"><span data-stu-id="b8209-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="b8209-157">Esse método é chamado pelo Dispatcher ao inicializar o <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="b8209-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="b8209-158">Por fim o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação é ligada ao modelo de serviço usando o <xref:System.ServiceModel.Description.IServiceBehavior> implementação.</span><span class="sxs-lookup"><span data-stu-id="b8209-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="b8209-159">Essa implementação é colocada na `CustomLeaseTimeAttribute` classe e ele também deriva o `Attribute` classe para expor esse comportamento como um atributo base.</span><span class="sxs-lookup"><span data-stu-id="b8209-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span>

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

<span data-ttu-id="b8209-160">Esse comportamento pode ser adicionado a uma classe de serviço de exemplo, anotando-o com o `CustomLeaseTime` atributo.</span><span class="sxs-lookup"><span data-stu-id="b8209-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="b8209-161">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="b8209-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b8209-162">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="b8209-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8209-163">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b8209-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b8209-164">Certifique-se de que você executou o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8209-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b8209-165">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8209-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="b8209-166">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8209-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8209-167">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b8209-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8209-168">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b8209-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b8209-169">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b8209-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8209-170">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b8209-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
