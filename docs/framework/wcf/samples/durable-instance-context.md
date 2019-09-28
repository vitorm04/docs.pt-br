---
title: Contexto de instância durável
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 4c2e39aa257d4b4b9b3bd28e0cd469f09cae0766
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351625"
---
# <a name="durable-instance-context"></a><span data-ttu-id="777e1-102">Contexto de instância durável</span><span class="sxs-lookup"><span data-stu-id="777e1-102">Durable Instance Context</span></span>

<span data-ttu-id="777e1-103">Este exemplo demonstra como personalizar o tempo de execução de Windows Communication Foundation (WCF) para habilitar contextos de instância durável.</span><span class="sxs-lookup"><span data-stu-id="777e1-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="777e1-104">Ele usa SQL Server 2005 como armazenamento de backup (SQL Server 2005 Express nesse caso).</span><span class="sxs-lookup"><span data-stu-id="777e1-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="777e1-105">No entanto, ele também fornece uma maneira de acessar mecanismos de armazenamento personalizados.</span><span class="sxs-lookup"><span data-stu-id="777e1-105">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="777e1-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="777e1-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="777e1-107">Este exemplo envolve a extensão da camada de canal e da camada do modelo de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="777e1-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="777e1-108">Portanto, é necessário entender os conceitos subjacentes antes de entrar nos detalhes da implementação.</span><span class="sxs-lookup"><span data-stu-id="777e1-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="777e1-109">Contextos de instância durável podem ser encontrados nos cenários do mundo real com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="777e1-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="777e1-110">Um aplicativo de carrinho de compras, por exemplo, tem a capacidade de pausar a compra na metade e continuar em outro dia.</span><span class="sxs-lookup"><span data-stu-id="777e1-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="777e1-111">Então, quando visitamos o carrinho de compras no dia seguinte, nosso contexto original é restaurado.</span><span class="sxs-lookup"><span data-stu-id="777e1-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="777e1-112">É importante observar que o aplicativo de carrinho de compras (no servidor) não mantém a instância do carrinho de compras enquanto estamos desconectados.</span><span class="sxs-lookup"><span data-stu-id="777e1-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="777e1-113">Em vez disso, ele persiste seu estado em uma mídia de armazenamento durável e a usa ao construir uma nova instância para o contexto restaurado.</span><span class="sxs-lookup"><span data-stu-id="777e1-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="777e1-114">Portanto, a instância de serviço que pode ser atendida para o mesmo contexto não é igual à instância anterior (ou seja, não tem o mesmo endereço de memória).</span><span class="sxs-lookup"><span data-stu-id="777e1-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="777e1-115">O contexto de instância durável torna-se possível por um protocolo pequeno que troca uma ID de contexto entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="777e1-116">Essa ID de contexto é criada no cliente e transmitida para o serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="777e1-117">Quando a instância do serviço é criada, o tempo de execução do serviço tenta carregar o estado persistente que corresponde a essa ID de contexto de um armazenamento persistente (por padrão, é um banco de dados SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="777e1-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="777e1-118">Se nenhum estado estiver disponível, a nova instância terá seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="777e1-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="777e1-119">A implementação do serviço usa um atributo personalizado para marcar operações que alteram o estado da implementação do serviço para que o tempo de execução possa salvar a instância do serviço depois de chamá-las.</span><span class="sxs-lookup"><span data-stu-id="777e1-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="777e1-120">Pela descrição anterior, duas etapas podem ser facilmente diferenciadas para atingir o objetivo:</span><span class="sxs-lookup"><span data-stu-id="777e1-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="777e1-121">Altere a mensagem que passa pela conexão para transportar a ID de contexto.</span><span class="sxs-lookup"><span data-stu-id="777e1-121">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="777e1-122">Altere o comportamento local do serviço para implementar a lógica de instanciação personalizada.</span><span class="sxs-lookup"><span data-stu-id="777e1-122">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="777e1-123">Como o primeiro na lista afeta as mensagens na transmissão, ela deve ser implementada como um canal personalizado e ser conectada à camada de canal.</span><span class="sxs-lookup"><span data-stu-id="777e1-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="777e1-124">O último afeta apenas o comportamento local do serviço e, portanto, pode ser implementado estendendo vários pontos de extensibilidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="777e1-125">Nas próximas seções, cada uma dessas extensões é discutida.</span><span class="sxs-lookup"><span data-stu-id="777e1-125">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="777e1-126">Canal de InstanceContext durável</span><span class="sxs-lookup"><span data-stu-id="777e1-126">Durable InstanceContext Channel</span></span>

<span data-ttu-id="777e1-127">A primeira coisa a ser examinada é uma extensão de camada de canal.</span><span class="sxs-lookup"><span data-stu-id="777e1-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="777e1-128">A primeira etapa na gravação de um canal personalizado é decidir a estrutura de comunicação do canal.</span><span class="sxs-lookup"><span data-stu-id="777e1-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="777e1-129">Como um novo protocolo de conexão está sendo introduzido, o canal deve funcionar com quase qualquer outro canal na pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="777e1-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="777e1-130">Portanto, ele deve dar suporte a todos os padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="777e1-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="777e1-131">No entanto, a funcionalidade principal do canal é a mesma, independentemente de sua estrutura de comunicação.</span><span class="sxs-lookup"><span data-stu-id="777e1-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="777e1-132">Mais especificamente, do cliente, ele deve gravar a ID de contexto para as mensagens e do serviço ele deve ler essa ID de contexto das mensagens e passá-la para os níveis superiores.</span><span class="sxs-lookup"><span data-stu-id="777e1-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="777e1-133">Por isso, é criada `DurableInstanceContextChannelBase` uma classe que atua como a classe base abstrata para todas as implementações de canal de contexto de instância durável.</span><span class="sxs-lookup"><span data-stu-id="777e1-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="777e1-134">Essa classe contém as funções de gerenciamento de máquina de Estado comum e dois membros protegidos para aplicar e ler as informações de contexto de e para mensagens.</span><span class="sxs-lookup"><span data-stu-id="777e1-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

<span data-ttu-id="777e1-135">Esses dois métodos fazem uso de `IContextManager` implementações para gravar e ler a ID de contexto de ou para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="777e1-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="777e1-136">(`IContextManager` é uma interface personalizada usada para definir o contrato para todos os gerenciadores de contexto.) O canal pode incluir a ID de contexto em um cabeçalho SOAP personalizado ou em um cabeçalho de cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="777e1-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="777e1-137">Cada implementação do Gerenciador de contexto herda `ContextManagerBase` da classe que contém a funcionalidade comum para todos os gerenciadores de contexto.</span><span class="sxs-lookup"><span data-stu-id="777e1-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="777e1-138">O `GetContextId` método nessa classe é usado para originar a ID de contexto do cliente.</span><span class="sxs-lookup"><span data-stu-id="777e1-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="777e1-139">Quando uma ID de contexto é originada pela primeira vez, esse método a salva em um arquivo de texto cujo nome é construído pelo endereço do ponto de extremidade remoto (os caracteres de nome de arquivo inválidos nos URIs típicos são substituídos por @ caracteres).</span><span class="sxs-lookup"><span data-stu-id="777e1-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="777e1-140">Posteriormente, quando a ID de contexto for necessária para o mesmo ponto de extremidade remoto, ela verificará se um arquivo apropriado existe.</span><span class="sxs-lookup"><span data-stu-id="777e1-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="777e1-141">Se tiver, ele lerá a ID de contexto e retornará.</span><span class="sxs-lookup"><span data-stu-id="777e1-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="777e1-142">Caso contrário, ele retorna uma ID de contexto gerada recentemente e salva-o em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="777e1-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="777e1-143">Com a configuração padrão, esses arquivos são colocados em um diretório chamado ContextStore, que reside no diretório Temp do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="777e1-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="777e1-144">No entanto, esse local é configurável usando o elemento Binding.</span><span class="sxs-lookup"><span data-stu-id="777e1-144">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="777e1-145">O mecanismo usado para transportar a ID de contexto é configurável.</span><span class="sxs-lookup"><span data-stu-id="777e1-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="777e1-146">Ele pode ser gravado no cabeçalho do cookie HTTP ou em um cabeçalho SOAP personalizado.</span><span class="sxs-lookup"><span data-stu-id="777e1-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="777e1-147">A abordagem de cabeçalho SOAP personalizada possibilita o uso desse protocolo com protocolos não HTTP (por exemplo, TCP ou pipes nomeados).</span><span class="sxs-lookup"><span data-stu-id="777e1-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="777e1-148">Há duas classes, `MessageHeaderContextManager` ou `HttpCookieContextManager`seja, que implementam essas duas opções.</span><span class="sxs-lookup"><span data-stu-id="777e1-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="777e1-149">Ambos gravam a ID de contexto na mensagem adequadamente.</span><span class="sxs-lookup"><span data-stu-id="777e1-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="777e1-150">Por exemplo, a `MessageHeaderContextManager` classe a grava em um cabeçalho SOAP `WriteContext` no método.</span><span class="sxs-lookup"><span data-stu-id="777e1-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

<span data-ttu-id="777e1-151">`ReadContextId` `IContextManager.ReadContext` Os métodos `ApplyContext` e na `IContextManager.WriteContext`classe invocam o e, respectivamente. `DurableInstanceContextChannelBase`</span><span class="sxs-lookup"><span data-stu-id="777e1-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="777e1-152">No entanto, esses gerenciadores de `DurableInstanceContextChannelBase` contexto não são criados diretamente pela classe.</span><span class="sxs-lookup"><span data-stu-id="777e1-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="777e1-153">Em vez disso, `ContextManagerFactory` ele usa a classe para fazer esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="777e1-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="777e1-154">O `ApplyContext` método é invocado pelos canais de envio.</span><span class="sxs-lookup"><span data-stu-id="777e1-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="777e1-155">Ele injeta a ID de contexto para as mensagens de saída.</span><span class="sxs-lookup"><span data-stu-id="777e1-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="777e1-156">O `ReadContextId` método é invocado pelos canais de recebimento.</span><span class="sxs-lookup"><span data-stu-id="777e1-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="777e1-157">Esse método garante que a ID de contexto esteja disponível nas mensagens de entrada e a adicione à `Properties` coleção `Message` da classe.</span><span class="sxs-lookup"><span data-stu-id="777e1-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="777e1-158">Ele também gera um `CommunicationException` no caso de uma falha ao ler a ID do contexto e, portanto, faz com que o canal seja anulado.</span><span class="sxs-lookup"><span data-stu-id="777e1-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="777e1-159">Antes de continuar, é importante entender o uso da `Properties` coleção `Message` na classe.</span><span class="sxs-lookup"><span data-stu-id="777e1-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="777e1-160">Normalmente, essa `Properties` coleção é usada ao passar dados de baixo para os níveis superiores da camada de canal.</span><span class="sxs-lookup"><span data-stu-id="777e1-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="777e1-161">Dessa forma, os dados desejados podem ser fornecidos para os níveis superiores de forma consistente, independentemente dos detalhes do protocolo.</span><span class="sxs-lookup"><span data-stu-id="777e1-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="777e1-162">Em outras palavras, a camada de canal pode enviar e receber a ID de contexto como um cabeçalho SOAP ou um cabeçalho de cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="777e1-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="777e1-163">Mas não é necessário que os níveis superiores saibam sobre esses detalhes porque a camada de canal torna essas informações disponíveis na `Properties` coleção.</span><span class="sxs-lookup"><span data-stu-id="777e1-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="777e1-164">Agora, com `DurableInstanceContextChannelBase` a classe em vigor, todas as dez interfaces necessárias (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="777e1-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="777e1-165">Eles se assemelham a todos os padrões de troca de mensagens disponíveis (datagrama, simplex, duplex e suas variantes de sessão).</span><span class="sxs-lookup"><span data-stu-id="777e1-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="777e1-166">Cada uma dessas implementações herda a classe base descrita anteriormente e `ApplyContext` chama `ReadContextId` e adequadamente.</span><span class="sxs-lookup"><span data-stu-id="777e1-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="777e1-167">Por exemplo, `DurableInstanceContextOutputChannel` -que implementa a interface IOutputChannel – chama o `ApplyContext` método de cada método que envia as mensagens.</span><span class="sxs-lookup"><span data-stu-id="777e1-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="777e1-168">Por outro lado, `DurableInstanceContextInputChannel` -que implementa a `IInputChannel` interface – chama o `ReadContextId` método em cada método que recebe as mensagens.</span><span class="sxs-lookup"><span data-stu-id="777e1-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="777e1-169">Além disso, essas implementações de canal delegam as invocações de método ao canal abaixo delas na pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="777e1-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="777e1-170">No entanto, as variantes de sessão têm uma lógica básica para garantir que a ID de contexto seja enviada e seja lida somente para a primeira mensagem que faz com que a sessão seja criada.</span><span class="sxs-lookup"><span data-stu-id="777e1-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="777e1-171">Essas implementações de `DurableInstanceContextBindingElement` canal são então adicionadas ao tempo de execução do canal `DurableInstanceContextBindingElementSection` do WCF pela classe e classe adequadamente.</span><span class="sxs-lookup"><span data-stu-id="777e1-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="777e1-172">Consulte a documentação de exemplo do canal [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) para obter mais detalhes sobre elementos de associação e seções de elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="777e1-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="777e1-173">Extensões de camada de modelo de serviço</span><span class="sxs-lookup"><span data-stu-id="777e1-173">Service Model Layer Extensions</span></span>

<span data-ttu-id="777e1-174">Agora que a ID de contexto percorreu pela camada de canal, o comportamento do serviço pode ser implementado para personalizar a instanciação.</span><span class="sxs-lookup"><span data-stu-id="777e1-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="777e1-175">Neste exemplo, um Gerenciador de armazenamento é usado para carregar e salvar o estado de ou para o repositório persistente.</span><span class="sxs-lookup"><span data-stu-id="777e1-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="777e1-176">Conforme explicado anteriormente, este exemplo fornece um Gerenciador de armazenamento que usa SQL Server 2005 como seu armazenamento de backup.</span><span class="sxs-lookup"><span data-stu-id="777e1-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="777e1-177">No entanto, também é possível adicionar mecanismos de armazenamento personalizados a essa extensão.</span><span class="sxs-lookup"><span data-stu-id="777e1-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="777e1-178">Para fazer isso, uma interface pública é declarada, que deve ser implementada por todos os gerenciadores de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="777e1-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="777e1-179">A `SqlServerStorageManager` classe contém a implementação `IStorageManager` padrão.</span><span class="sxs-lookup"><span data-stu-id="777e1-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="777e1-180">Em seu `SaveInstance` método, o objeto fornecido é serializado usando o XmlSerializer e é salvo no banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="777e1-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

<span data-ttu-id="777e1-181">`GetInstance` No método, os dados serializados são lidos para uma determinada ID de contexto e o objeto construído a partir dele é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="777e1-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

<span data-ttu-id="777e1-182">Os usuários desses gerenciadores de armazenamento não devem instanciá-los diretamente.</span><span class="sxs-lookup"><span data-stu-id="777e1-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="777e1-183">Eles usam a `StorageManagerFactory` classe, que é abstraida dos detalhes de criação do Gerenciador de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="777e1-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="777e1-184">Essa classe tem um membro estático, `GetStorageManager`, que cria uma instância de um determinado tipo de Gerenciador de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="777e1-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="777e1-185">Se o parâmetro de tipo `null`for, esse método criará uma instância da `SqlServerStorageManager` classe padrão e a retornará.</span><span class="sxs-lookup"><span data-stu-id="777e1-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="777e1-186">Ele também valida o tipo fornecido para certificar-se de que ele implementa `IStorageManager` a interface.</span><span class="sxs-lookup"><span data-stu-id="777e1-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

<span data-ttu-id="777e1-187">A infraestrutura necessária para ler e gravar instâncias do armazenamento persistente é implementada.</span><span class="sxs-lookup"><span data-stu-id="777e1-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="777e1-188">Agora, as etapas necessárias para alterar o comportamento do serviço devem ser realizadas.</span><span class="sxs-lookup"><span data-stu-id="777e1-188">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="777e1-189">Como a primeira etapa desse processo, precisamos salvar a ID de contexto, que veio pela camada de canal para o InstanceContext atual.</span><span class="sxs-lookup"><span data-stu-id="777e1-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="777e1-190">InstanceContext é um componente de tempo de execução que atua como o link entre o Dispatcher do WCF e a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="777e1-191">Ele pode ser usado para fornecer estado adicional e comportamento à instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="777e1-192">Isso é essencial porque, na comunicação de sessão, a ID de contexto é enviada somente com a primeira mensagem.</span><span class="sxs-lookup"><span data-stu-id="777e1-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="777e1-193">O WCF permite estender seu componente de tempo de execução de InstanceContext adicionando um novo estado e comportamento usando seu padrão de objeto extensível.</span><span class="sxs-lookup"><span data-stu-id="777e1-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="777e1-194">O padrão de objeto extensível é usado no WCF para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado a um objeto.</span><span class="sxs-lookup"><span data-stu-id="777e1-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="777e1-195">Há três interfaces no padrão de objeto extensível-IExtensibleObject\<T >, IExtension\<t > e IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="777e1-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="777e1-196">A interface\<IExtensibleObject T > é implementada por objetos que permitem extensões que personalizam sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="777e1-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="777e1-197">A interface\<IExtension T > é implementada por objetos que são extensões de classes do tipo T.</span><span class="sxs-lookup"><span data-stu-id="777e1-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="777e1-198">A interface\<IExtensionCollection T > é uma coleção de IExtensions que permite recuperar IExtensions por seu tipo.</span><span class="sxs-lookup"><span data-stu-id="777e1-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="777e1-199">Portanto, uma classe InstanceContextExtension deve ser criada para implementar a interface IExtension e definir o estado necessário para salvar a ID de contexto.</span><span class="sxs-lookup"><span data-stu-id="777e1-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="777e1-200">Essa classe também fornece o estado para manter o Gerenciador de armazenamento em uso.</span><span class="sxs-lookup"><span data-stu-id="777e1-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="777e1-201">Depois que o novo estado for salvo, não será possível modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="777e1-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="777e1-202">Portanto, o estado é fornecido e salvo na instância no momento em que está sendo construído e só pode ser acessado usando propriedades somente leitura.</span><span class="sxs-lookup"><span data-stu-id="777e1-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

<span data-ttu-id="777e1-203">A classe InstanceContextInitializer implementa a interface IInstanceContextInitializer e adiciona a extensão de contexto de instância à coleção Extensions do InstanceContext que está sendo construído.</span><span class="sxs-lookup"><span data-stu-id="777e1-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

<span data-ttu-id="777e1-204">Conforme descrito anteriormente, a ID de contexto é lida `Properties` da coleção `Message` da classe e passada para o construtor da classe de extensão.</span><span class="sxs-lookup"><span data-stu-id="777e1-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="777e1-205">Isso demonstra como as informações podem ser trocadas entre as camadas de maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="777e1-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="777e1-206">A próxima etapa importante é substituir o processo de criação da instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="777e1-207">O WCF permite implementar comportamentos de instanciação personalizados e conectá-los ao tempo de execução usando a interface IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="777e1-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="777e1-208">A nova `InstanceProvider` classe é implementada para fazer esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="777e1-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="777e1-209">No construtor, o tipo de serviço esperado do provedor de instância é aceito.</span><span class="sxs-lookup"><span data-stu-id="777e1-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="777e1-210">Posteriormente, isso é usado para criar novas instâncias.</span><span class="sxs-lookup"><span data-stu-id="777e1-210">Later this is used to create new instances.</span></span> <span data-ttu-id="777e1-211">`GetInstance` Na implementação, uma instância de um Gerenciador de armazenamento é criada procurando por uma instância persistente.</span><span class="sxs-lookup"><span data-stu-id="777e1-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="777e1-212">Se ele retornar `null` , uma nova instância do tipo de serviço será instanciada e retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="777e1-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="777e1-213">A próxima etapa importante é instalar o `InstanceContextExtension` `InstanceContextInitializer` e `InstanceProvider` as classes no tempo de execução do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="777e1-214">Um atributo personalizado pode ser usado para marcar as classes de implementação de serviço para instalar o comportamento.</span><span class="sxs-lookup"><span data-stu-id="777e1-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="777e1-215">O `DurableInstanceContextAttribute` contém a implementação para esse atributo e implementa a `IServiceBehavior` interface para estender o tempo de execução do serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="777e1-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="777e1-216">Essa classe tem uma propriedade que aceita o tipo do Gerenciador de armazenamento a ser usado.</span><span class="sxs-lookup"><span data-stu-id="777e1-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="777e1-217">Dessa forma, a implementação permite que os usuários especifiquem sua `IStorageManager` própria implementação como parâmetro deste atributo.</span><span class="sxs-lookup"><span data-stu-id="777e1-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="777e1-218">Na implementação, o `InstanceContextMode` do atributo atual `ServiceBehavior` está sendo verificado. `ApplyDispatchBehavior`</span><span class="sxs-lookup"><span data-stu-id="777e1-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="777e1-219">Se essa propriedade for definida como singleton, a habilitação da instanciação durável não será `InvalidOperationException` possível e uma será gerada para notificar o host.</span><span class="sxs-lookup"><span data-stu-id="777e1-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="777e1-220">Depois disso, as instâncias do Gerenciador de armazenamento, o inicializador de contexto de instância e o provedor de instância são `DispatchRuntime` criados e instalados no ponto de extremidade criado para cada.</span><span class="sxs-lookup"><span data-stu-id="777e1-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

<span data-ttu-id="777e1-221">No Resumo até agora, este exemplo produziu um canal que habilitou o protocolo de conexão personalizada para a troca de ID de contexto personalizado e também substitui o comportamento de instanciação padrão para carregar as instâncias do armazenamento persistente.</span><span class="sxs-lookup"><span data-stu-id="777e1-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="777e1-222">O que resta é uma maneira de salvar a instância do serviço no armazenamento persistente.</span><span class="sxs-lookup"><span data-stu-id="777e1-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="777e1-223">Conforme discutido anteriormente, já existe a funcionalidade necessária para salvar o estado em uma `IStorageManager` implementação.</span><span class="sxs-lookup"><span data-stu-id="777e1-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="777e1-224">Agora, devemos integrar isso ao tempo de execução do WCF.</span><span class="sxs-lookup"><span data-stu-id="777e1-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="777e1-225">É necessário outro atributo que seja aplicável aos métodos na classe de implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="777e1-226">Esse atributo deve ser aplicado aos métodos que alteram o estado da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="777e1-227">A `SaveStateAttribute` classe implementa essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="777e1-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="777e1-228">Ele também implementa `IOperationBehavior` a classe para modificar o tempo de execução do WCF para cada operação.</span><span class="sxs-lookup"><span data-stu-id="777e1-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="777e1-229">Quando um método é marcado com esse atributo, o tempo de execução do WCF `ApplyBehavior` invoca o método enquanto `DispatchOperation` o apropriado está sendo construído.</span><span class="sxs-lookup"><span data-stu-id="777e1-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="777e1-230">Nessa implementação de método há uma linha de código única:</span><span class="sxs-lookup"><span data-stu-id="777e1-230">In this method implementation there is single line of code:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="777e1-231">Essa instrução cria uma instância do `OperationInvoker` tipo e a atribui `Invoker` à propriedade de `DispatchOperation` que está sendo construída.</span><span class="sxs-lookup"><span data-stu-id="777e1-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="777e1-232">A `OperationInvoker` classe é um wrapper para o chamador de operação padrão criado para o `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="777e1-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="777e1-233">Essa classe implementa a `IOperationInvoker` interface.</span><span class="sxs-lookup"><span data-stu-id="777e1-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="777e1-234">`Invoke` Na implementação do método, a invocação do método real é delegada para o chamador da operação interna.</span><span class="sxs-lookup"><span data-stu-id="777e1-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="777e1-235">No entanto, antes de retornar os resultados, o `InstanceContext` Gerenciador de armazenamento no é usado para salvar a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="777e1-236">Usando a extensão</span><span class="sxs-lookup"><span data-stu-id="777e1-236">Using the Extension</span></span>

<span data-ttu-id="777e1-237">A camada de canal e as extensões de camada de modelo de serviço são feitas e agora podem ser usadas em aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="777e1-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="777e1-238">Os serviços precisam adicionar o canal à pilha de canais usando uma associação personalizada e, em seguida, marcar as classes de implementação de serviço com os atributos apropriados.</span><span class="sxs-lookup"><span data-stu-id="777e1-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

<span data-ttu-id="777e1-239">Os aplicativos cliente devem adicionar o DurableInstanceContextChannel à pilha de canais usando uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="777e1-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="777e1-240">Para configurar o canal de forma declarativa no arquivo de configuração, a seção elemento de associação deve ser adicionada à coleção de extensões do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="777e1-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
```

<span data-ttu-id="777e1-241">Agora, o elemento Binding pode ser usado com uma associação personalizada, assim como outros elementos de ligação padrão:</span><span class="sxs-lookup"><span data-stu-id="777e1-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a><span data-ttu-id="777e1-242">Conclusão</span><span class="sxs-lookup"><span data-stu-id="777e1-242">Conclusion</span></span>

<span data-ttu-id="777e1-243">Este exemplo mostrou como criar um canal de protocolo personalizado e como personalizar o comportamento do serviço para habilitá-lo.</span><span class="sxs-lookup"><span data-stu-id="777e1-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="777e1-244">A extensão pode ser melhorada, permitindo que os usuários `IStorageManager` especifiquem a implementação usando uma seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="777e1-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="777e1-245">Isso torna possível modificar o armazenamento de backup sem recompilar o código do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="777e1-246">Além disso, você pode tentar implementar uma classe (por exemplo `StateBag`,), que encapsula o estado da instância.</span><span class="sxs-lookup"><span data-stu-id="777e1-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="777e1-247">Essa classe é responsável por persistir o estado sempre que ele for alterado.</span><span class="sxs-lookup"><span data-stu-id="777e1-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="777e1-248">Dessa forma, você pode evitar o `SaveState` uso do atributo e executar o trabalho persistente com mais precisão (por exemplo, você pode persistir o estado quando o estado é realmente alterado, em vez de salvá-lo toda vez `SaveState` que um método com o atributo for chamado).</span><span class="sxs-lookup"><span data-stu-id="777e1-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="777e1-249">Quando você executa o exemplo, a saída a seguir é exibida.</span><span class="sxs-lookup"><span data-stu-id="777e1-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="777e1-250">O cliente adiciona dois itens ao seu carrinho de compras e obtém a lista de itens em seu carrinho de compras do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="777e1-251">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="777e1-251">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="777e1-252">A recriação do serviço substitui o arquivo de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="777e1-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="777e1-253">Para observar o estado preservado entre várias execuções do exemplo, não se esqueça de recompilar o exemplo entre as execuções.</span><span class="sxs-lookup"><span data-stu-id="777e1-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="777e1-254">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="777e1-254">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="777e1-255">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="777e1-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="777e1-256">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="777e1-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="777e1-257">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="777e1-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="777e1-258">Você deve estar executando o SQL Server 2005 ou o SQL Express 2005 para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="777e1-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="777e1-259">Se estiver executando o SQL Server 2005, você deverá modificar a configuração da cadeia de conexão do serviço.</span><span class="sxs-lookup"><span data-stu-id="777e1-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="777e1-260">Ao executar a máquina cruzada, SQL Server só é necessária no computador do servidor.</span><span class="sxs-lookup"><span data-stu-id="777e1-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="777e1-261">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="777e1-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="777e1-262">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="777e1-262">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="777e1-263">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="777e1-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="777e1-264">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="777e1-264">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
