---
title: "Contexto de instância durável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 540f6b6fe7795eb958afd84695865fd2e4271175
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="durable-instance-context"></a><span data-ttu-id="92de0-102">Contexto de instância durável</span><span class="sxs-lookup"><span data-stu-id="92de0-102">Durable Instance Context</span></span>
<span data-ttu-id="92de0-103">Este exemplo demonstra como personalizar o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tempo de execução para permitir que os contextos de instância durável.</span><span class="sxs-lookup"><span data-stu-id="92de0-103">This sample demonstrates how to customize the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime to enable durable instance contexts.</span></span> <span data-ttu-id="92de0-104">Ele usa o SQL Server 2005 como seu armazenamento de backup (SQL Server 2005 Express neste caso).</span><span class="sxs-lookup"><span data-stu-id="92de0-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="92de0-105">No entanto, ele também fornece uma maneira de acessar os mecanismos de armazenamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="92de0-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92de0-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="92de0-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="92de0-107">Este exemplo envolve estendendo a camada do canal e a camada de modelo de serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92de0-107">This sample involves extending both the channel layer and the service model layer of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="92de0-108">Portanto, é necessário entender os conceitos subjacentes antes de continuar com os detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="92de0-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="92de0-109">Contextos de instância durável com muita frequência, podem ser encontrados em cenários do mundo real.</span><span class="sxs-lookup"><span data-stu-id="92de0-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="92de0-110">Um aplicativo de carrinho de compras, por exemplo, tem a capacidade de pausar a metade de compras por meio e continuá-lo em outro dia.</span><span class="sxs-lookup"><span data-stu-id="92de0-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="92de0-111">Para que quando visitar o carrinho de compras no dia seguinte, nosso contexto original é restaurado.</span><span class="sxs-lookup"><span data-stu-id="92de0-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="92de0-112">É importante observar que o aplicativo de carrinho de compras (no servidor) não mantém a instância de carrinho de compras enquanto estamos estiver desconectados.</span><span class="sxs-lookup"><span data-stu-id="92de0-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="92de0-113">Em vez disso, ele mantém seu estado em uma mídia de armazenamento durável e usa-o ao construir uma nova instância para o contexto restaurado.</span><span class="sxs-lookup"><span data-stu-id="92de0-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="92de0-114">Portanto, a instância de serviço que pode atender para o mesmo contexto não é o mesmo que a instância anterior (ou seja, ele não tem o mesmo endereço de memória).</span><span class="sxs-lookup"><span data-stu-id="92de0-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="92de0-115">Contexto de instância durável é possibilitado por um protocolo pequeno que uma ID de contexto entre o cliente e o serviço de troca.</span><span class="sxs-lookup"><span data-stu-id="92de0-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="92de0-116">Essa ID de contexto é criado no cliente e transmitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="92de0-117">Quando a instância do serviço é criada, o tempo de execução do serviço tenta carregar o estado persistente que corresponde a essa ID de contexto de um armazenamento persistente (por padrão é um banco de dados do SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="92de0-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="92de0-118">Se nenhum estado está disponível a nova instância tem seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="92de0-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="92de0-119">A implementação de serviço usa um atributo personalizado para marcar as operações que alteram o estado da implementação do serviço para que o tempo de execução pode salvar a instância de serviço depois de executá-los.</span><span class="sxs-lookup"><span data-stu-id="92de0-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="92de0-120">A descrição anterior, duas etapas podem ser distinguidas facilmente para atingir a meta:</span><span class="sxs-lookup"><span data-stu-id="92de0-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1.  <span data-ttu-id="92de0-121">Alterar a mensagem que entra no fio para executar o ID de contexto.</span><span class="sxs-lookup"><span data-stu-id="92de0-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2.  <span data-ttu-id="92de0-122">Altere o comportamento de local de serviço para implementar a lógica personalizada de instância.</span><span class="sxs-lookup"><span data-stu-id="92de0-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="92de0-123">Como o primeiro na lista afeta as mensagens na conexão, ele deve ser implementado como um canal personalizado e ser vinculado a camada do canal.</span><span class="sxs-lookup"><span data-stu-id="92de0-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="92de0-124">O último só afeta o comportamento de serviço local e, portanto, pode ser implementado, estendendo a vários pontos de extensibilidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="92de0-125">Nas próximas seções, cada uma das seguintes extensões são discutidos.</span><span class="sxs-lookup"><span data-stu-id="92de0-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="92de0-126">Canal de InstanceContext duráveis</span><span class="sxs-lookup"><span data-stu-id="92de0-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="92de0-127">A primeira coisa a observar é uma extensão de camada do canal.</span><span class="sxs-lookup"><span data-stu-id="92de0-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="92de0-128">É a primeira etapa na composição de um canal personalizado decidir a estrutura do canal de comunicação.</span><span class="sxs-lookup"><span data-stu-id="92de0-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="92de0-129">Como um novo protocolo de transmissão está sendo introduzido o canal deve funcionar com praticamente qualquer outro canal na pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="92de0-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="92de0-130">Portanto, ele deve dar suporte a todos os padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="92de0-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="92de0-131">No entanto, a funcionalidade básica do canal é o mesmo, independentemente de sua estrutura de comunicação.</span><span class="sxs-lookup"><span data-stu-id="92de0-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="92de0-132">Mais especificamente, do cliente ele deve gravar a identificação de contexto para as mensagens e do serviço deve ler esta ID de contexto das mensagens e passá-lo para os níveis superiores.</span><span class="sxs-lookup"><span data-stu-id="92de0-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="92de0-133">Por isso, um `DurableInstanceContextChannelBase` classe é criada que atua como a classe base abstrata para todas as implementações de canal de contexto de instância durável.</span><span class="sxs-lookup"><span data-stu-id="92de0-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="92de0-134">Essa classe contém as funções de gerenciamento de máquina de estado comum e dois membros protegidos para aplicar e ler as informações de contexto para e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="92de0-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-135">Esses dois métodos fazem uso de `IContextManager` implementações para gravar e ler a ID do contexto de ou para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="92de0-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="92de0-136">(`IContextManager` é uma interface personalizada usada para definir o contrato para todos os gerenciadores de contexto.) O canal pode incluir a ID do contexto em um cabeçalho SOAP personalizado ou em um cabeçalho de cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="92de0-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="92de0-137">Cada implementação do Gerenciador de contexto herda o `ContextManagerBase` classe que contém a funcionalidade comum para todos os gerenciadores de contexto.</span><span class="sxs-lookup"><span data-stu-id="92de0-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="92de0-138">O `GetContextId` método nessa classe é usado para se originar a ID do contexto do cliente.</span><span class="sxs-lookup"><span data-stu-id="92de0-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="92de0-139">Quando um contexto de que ID é originada pela primeira vez, esse método salva em um arquivo de texto cujo nome é criado pelo endereço do ponto de extremidade remoto (os caracteres de nome de arquivo inválido nos URIs típicos são substituídos por caracteres @).</span><span class="sxs-lookup"><span data-stu-id="92de0-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="92de0-140">Mais tarde quando a ID de contexto é necessária para o mesmo ponto de extremidade remoto, ele verifica se existe um arquivo apropriado.</span><span class="sxs-lookup"><span data-stu-id="92de0-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="92de0-141">Em caso afirmativo, ele lê a ID do contexto e retorna.</span><span class="sxs-lookup"><span data-stu-id="92de0-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="92de0-142">Caso contrário, ele retorna a ID do contexto recém-gerado e salva-o em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="92de0-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="92de0-143">Com a configuração padrão, esses arquivos são colocados em um diretório chamado ContextStore, que reside no diretório temp do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="92de0-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="92de0-144">No entanto, esse local é configurável usando o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="92de0-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="92de0-145">O mecanismo usado para a ID do contexto de transporte é configurável.</span><span class="sxs-lookup"><span data-stu-id="92de0-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="92de0-146">Ele pode ser gravado para o cabeçalho de cookie HTTP ou um cabeçalho SOAP personalizado.</span><span class="sxs-lookup"><span data-stu-id="92de0-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="92de0-147">A abordagem de cabeçalho SOAP personalizada torna possível usar esse protocolo com protocolos não HTTP (por exemplo, TCP ou Pipes nomeados).</span><span class="sxs-lookup"><span data-stu-id="92de0-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="92de0-148">Há duas classes, ou seja, `MessageHeaderContextManager` e `HttpCookieContextManager`, que implementam essas duas opções.</span><span class="sxs-lookup"><span data-stu-id="92de0-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="92de0-149">Os dois gravam a identificação de contexto para a mensagem adequadamente.</span><span class="sxs-lookup"><span data-stu-id="92de0-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="92de0-150">Por exemplo, o `MessageHeaderContextManager` classe grava um cabeçalho SOAP no `WriteContext` método.</span><span class="sxs-lookup"><span data-stu-id="92de0-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-151">Tanto o `ApplyContext` e `ReadContextId` métodos o `DurableInstanceContextChannelBase` classe chamar o `IContextManager.ReadContext` e `IContextManager.WriteContext`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="92de0-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="92de0-152">No entanto, esses gerenciadores de contexto não são diretamente criados pelo `DurableInstanceContextChannelBase` classe.</span><span class="sxs-lookup"><span data-stu-id="92de0-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="92de0-153">Em vez disso, ele usa o `ContextManagerFactory` classe para realizar esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="92de0-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="92de0-154">O `ApplyContext` método é invocado por canais de envio.</span><span class="sxs-lookup"><span data-stu-id="92de0-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="92de0-155">Ele insere a ID do contexto para as mensagens de saída.</span><span class="sxs-lookup"><span data-stu-id="92de0-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="92de0-156">O `ReadContextId` método é invocado por canais de recebimento.</span><span class="sxs-lookup"><span data-stu-id="92de0-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="92de0-157">Esse método garante que a ID do contexto está disponível nas mensagens de entrada e adiciona-o para o `Properties` coleção do `Message` classe.</span><span class="sxs-lookup"><span data-stu-id="92de0-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="92de0-158">Ela também gera uma `CommunicationException` em caso de falha ao ler a ID do contexto e, portanto, faz com que o canal a ser anulada.</span><span class="sxs-lookup"><span data-stu-id="92de0-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="92de0-159">Antes de continuar, é importante entender o uso do `Properties` coleção no `Message` classe.</span><span class="sxs-lookup"><span data-stu-id="92de0-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="92de0-160">Normalmente, isso `Properties` coleção é usada quando passando dados para baixo para os níveis superiores da camada de canal.</span><span class="sxs-lookup"><span data-stu-id="92de0-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="92de0-161">Dessa forma os dados desejados podem ser fornecidos para os níveis superiores de maneira consistente, independentemente dos detalhes de protocolo.</span><span class="sxs-lookup"><span data-stu-id="92de0-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="92de0-162">Em outras palavras, a camada do canal de mensagens pode enviar e receber a ID do contexto como um cabeçalho SOAP ou um cabeçalho de cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="92de0-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="92de0-163">Mas não é necessário para os níveis superiores conhecer esses detalhes, como a camada de canal torna essas informações disponíveis no `Properties` coleção.</span><span class="sxs-lookup"><span data-stu-id="92de0-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="92de0-164">Agora com o `DurableInstanceContextChannelBase` os dez as interfaces necessárias (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, classe in-loco IDuplexChannel, IDuplexSessionChannel) deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="92de0-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="92de0-165">Eles são semelhantes a cada padrão de troca de mensagens disponíveis (datagrama, simplex, duplex e suas variantes de sessão).</span><span class="sxs-lookup"><span data-stu-id="92de0-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="92de0-166">Cada uma dessas implementações herdar a classe base descrito anteriormente e chama `ApplyContext` e `ReadContexId` adequadamente.</span><span class="sxs-lookup"><span data-stu-id="92de0-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="92de0-167">Por exemplo, `DurableInstanceContextOutputChannel` - que implementa a interface IOutputChannel - chama o `ApplyContext` método de cada método que envia as mensagens.</span><span class="sxs-lookup"><span data-stu-id="92de0-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="92de0-168">Por outro lado, `DurableInstanceContextInputChannel` -que implementa o `IInputChannel` interface - chama o `ReadContextId` método em cada método que recebe as mensagens.</span><span class="sxs-lookup"><span data-stu-id="92de0-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="92de0-169">Além disso, essas implementações de canal delegam as invocações de método para o canal abaixo na pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="92de0-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="92de0-170">No entanto, variantes de sessão têm uma lógica básica para certificar-se de que a ID de contexto é enviada e é lido apenas para a primeira mensagem que faz com que a sessão a ser criado.</span><span class="sxs-lookup"><span data-stu-id="92de0-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="92de0-171">Essas implementações de canal são adicionadas ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução de canal, o `DurableInstanceContextBindingElement` classe e `DurableInstanceContextBindingElementSection` classe adequadamente.</span><span class="sxs-lookup"><span data-stu-id="92de0-171">These channel implementations are then added to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="92de0-172">Consulte o [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) documentação de exemplo para obter mais detalhes sobre seções de elemento de associação e elementos de associação de canal.</span><span class="sxs-lookup"><span data-stu-id="92de0-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="92de0-173">Extensões de modelo de camada de serviço</span><span class="sxs-lookup"><span data-stu-id="92de0-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="92de0-174">Agora que a ID do contexto tem percorrida por meio da camada de canal, o comportamento de serviço pode ser implementado para personalizar a instanciação.</span><span class="sxs-lookup"><span data-stu-id="92de0-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="92de0-175">Neste exemplo, um Gerenciador de armazenamento é usado para carregar e salvar o estado de ou para o armazenamento persistente.</span><span class="sxs-lookup"><span data-stu-id="92de0-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="92de0-176">Conforme explicado anteriormente, este exemplo fornece um Gerenciador de armazenamento que usa o SQL Server 2005 como seu armazenamento de backup.</span><span class="sxs-lookup"><span data-stu-id="92de0-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="92de0-177">No entanto, também é possível adicionar os mecanismos de armazenamento personalizado para essa extensão.</span><span class="sxs-lookup"><span data-stu-id="92de0-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="92de0-178">Para fazer isso em uma interface pública for declarado, que deve ser implementado por todos os gerenciadores de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="92de0-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="92de0-179">O `SqlServerStorageManager` classe contém o padrão `IStorageManager` implementação.</span><span class="sxs-lookup"><span data-stu-id="92de0-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="92de0-180">No seu `SaveInstance` método do objeto especificado é serializado usando XmlSerializer e é salvo no banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92de0-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-181">No `GetInstance` método os dados serializados são lidos para uma ID de contexto fornecido e o objeto construído a partir dele é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="92de0-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-182">Usuários desses gerenciadores de não deveria ser instanciá-las diretamente de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="92de0-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="92de0-183">Eles usam o `StorageManagerFactory` classe que abstrai dos detalhes de criação do Gerenciador de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="92de0-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="92de0-184">Essa classe tem um membro estático, `GetStorageManager`, que cria uma instância de um tipo de Gerenciador de armazenamento específico.</span><span class="sxs-lookup"><span data-stu-id="92de0-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="92de0-185">Se o parâmetro de tipo é `null`, esse método cria uma instância padrão do `SqlServerStorageManager` classe e o retorna.</span><span class="sxs-lookup"><span data-stu-id="92de0-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="92de0-186">Ele também valida o tipo fornecido para certificar-se de que ele implementa o `IStorageManager` interface.</span><span class="sxs-lookup"><span data-stu-id="92de0-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-187">A infraestrutura necessária para ler e gravar instâncias do armazenamento persistente é implementada.</span><span class="sxs-lookup"><span data-stu-id="92de0-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="92de0-188">Agora, as etapas necessárias para alterar o comportamento de serviço devem ser executados.</span><span class="sxs-lookup"><span data-stu-id="92de0-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="92de0-189">Como a primeira etapa desse processo, precisamos salvar a identificação de contexto fornecido por meio da camada do canal para o InstanceContext atual.</span><span class="sxs-lookup"><span data-stu-id="92de0-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="92de0-190">InstanceContext é um componente de tempo de execução que atua como o link entre a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatcher e a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-190">InstanceContext is a runtime component that acts as the link between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatcher and the service instance.</span></span> <span data-ttu-id="92de0-191">Ele pode ser usado para fornecer estado adicionais e o comportamento para a instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="92de0-192">Isso é essencial porque na comunicação da sessão, a ID do contexto é enviada somente com a primeira mensagem.</span><span class="sxs-lookup"><span data-stu-id="92de0-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="92de0-193">permite estender seu componente de tempo de execução InstanceContext adicionando um novo estado e o comportamento usando o padrão de objeto extensível.</span><span class="sxs-lookup"><span data-stu-id="92de0-193"> allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="92de0-194">O padrão de objeto extensível é usado em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado para um objeto.</span><span class="sxs-lookup"><span data-stu-id="92de0-194">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="92de0-195">Existem três interfaces no padrão de objeto extensível - IExtensibleObject\<T >, IExtension\<T > e IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="92de0-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="92de0-196">O IExtensibleObject\<T > interface é implementada por objetos que permitem a extensões que personalizar sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="92de0-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="92de0-197">O IExtension\<T > interface é implementada por objetos que são extensões de classes do tipo T.</span><span class="sxs-lookup"><span data-stu-id="92de0-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="92de0-198">O IExtensionCollection\<T > interface é uma coleção de IExtensions que permite recuperar IExtensions por seu tipo.</span><span class="sxs-lookup"><span data-stu-id="92de0-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="92de0-199">Portanto, uma classe InstanceContextExtension deve ser criada que implementa a interface IExtension e define o estado exigido para salvar o ID de contexto.</span><span class="sxs-lookup"><span data-stu-id="92de0-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="92de0-200">Essa classe também fornece o estado para manter o armazenamento manager que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="92de0-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="92de0-201">Depois do novo estado salvo, não deve ser possível modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="92de0-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="92de0-202">Portanto, o estado é fornecido e salvo na instância no momento está sendo construído e, em seguida, somente acessível usando propriedades somente leitura.</span><span class="sxs-lookup"><span data-stu-id="92de0-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-203">A classe InstanceContextInitializer implementa a interface IInstanceContextInitializer e adiciona a extensão de contexto de instância para a coleção de extensões da InstanceContext sendo construída.</span><span class="sxs-lookup"><span data-stu-id="92de0-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-204">Conforme descrito anteriormente a ID de contexto é lido a partir de `Properties` coleção do `Message` classe e transmitido ao construtor da classe de extensão.</span><span class="sxs-lookup"><span data-stu-id="92de0-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="92de0-205">Isso demonstra como as informações podem ser trocadas entre as camadas de maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="92de0-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="92de0-206">A próxima etapa importante está substituindo o processo de criação de instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-206">The next important step is overriding the service instance creation process.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="92de0-207">permite a implementação de comportamentos personalizados instanciação e capturando-los até o tempo de execução usando a interface IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="92de0-207"> allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="92de0-208">O novo `InstanceProvider` classe é implementada para fazer esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="92de0-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="92de0-209">No construtor no tipo de serviço esperado do provedor de instância é aceita.</span><span class="sxs-lookup"><span data-stu-id="92de0-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="92de0-210">Posteriormente, isso é usado para criar novas instâncias.</span><span class="sxs-lookup"><span data-stu-id="92de0-210">Later this is used to create new instances.</span></span> <span data-ttu-id="92de0-211">No `GetInstance` implementação de uma instância de um Gerenciador de armazenamento é criada procurando uma instância persistente.</span><span class="sxs-lookup"><span data-stu-id="92de0-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="92de0-212">Se ele retorna `null` , em seguida, uma nova instância do tipo de serviço é instanciada e retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="92de0-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 <span data-ttu-id="92de0-213">A próxima etapa importante é instalar o `InstanceContextExtension`, `InstanceContextInitializer` e `InstanceProvider` classes para o tempo de execução do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="92de0-214">Um atributo personalizado pode ser usado para marcar as classes de implementação de serviço para o comportamento da instalação.</span><span class="sxs-lookup"><span data-stu-id="92de0-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="92de0-215">O `DurableInstanceContextAttribute` contém a implementação para esse atributo e implementa o `IServiceBehavior` interface para estender o tempo de execução de todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="92de0-216">Essa classe tem uma propriedade que aceita o tipo do Gerenciador de armazenamento a ser usado.</span><span class="sxs-lookup"><span data-stu-id="92de0-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="92de0-217">Dessa forma, a implementação permite aos usuários especificar seus próprios `IStorageManager` implementação como parâmetro desse atributo.</span><span class="sxs-lookup"><span data-stu-id="92de0-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="92de0-218">No `ApplyDispatchBehavior` implementação o `InstanceContextMode` do atual `ServiceBehavior` atributo está sendo verificado.</span><span class="sxs-lookup"><span data-stu-id="92de0-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="92de0-219">Se essa propriedade é definida como Singleton, permitindo que a instância durável não é possível e um `InvalidOperationException` gerada para notificar o host.</span><span class="sxs-lookup"><span data-stu-id="92de0-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 <span data-ttu-id="92de0-220">Depois das instâncias do Gerenciador de armazenamento, o inicializador de contexto de instância e o provedor de instância são criadas e instaladas no `DispatchRuntime` criado para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="92de0-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-221">Em resumo até agora, este exemplo produziu um canal que habilitado o protocolo personalizado para o exchange de ID de contexto personalizado e ele também substitui o padrão de comportamento para carregar as instâncias do armazenamento persistente de instâncias.</span><span class="sxs-lookup"><span data-stu-id="92de0-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="92de0-222">O restante é uma maneira de salvar a instância de serviço para o armazenamento persistente.</span><span class="sxs-lookup"><span data-stu-id="92de0-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="92de0-223">Como discutido anteriormente, já existe a funcionalidade necessária para salvar o estado em um `IStorageManager` implementação.</span><span class="sxs-lookup"><span data-stu-id="92de0-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="92de0-224">Estamos agora deve se integrar com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="92de0-224">We now must integrate this with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="92de0-225">Outro atributo é necessário que é aplicável para os métodos na classe de implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="92de0-226">Esse atributo deve ser aplicado a métodos que alteram o estado da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="92de0-227">O `SaveStateAttribute` classe implementa essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="92de0-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="92de0-228">Ele também implementa `IOperationBehavior` classe para modificar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução para cada operação.</span><span class="sxs-lookup"><span data-stu-id="92de0-228">It also implements `IOperationBehavior` class to modify the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime for each operation.</span></span> <span data-ttu-id="92de0-229">Quando um método é marcado com esse atributo, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução chama o `ApplyBehavior` método apropriada `DispatchOperation` está sendo construído.</span><span class="sxs-lookup"><span data-stu-id="92de0-229">When a method is marked with this attribute, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="92de0-230">Nessa implementação de método há uma única linha de código:</span><span class="sxs-lookup"><span data-stu-id="92de0-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="92de0-231">Essa instrução cria uma instância de `OperationInvoker` tipo e o atribui para a `Invoker` propriedade do `DispatchOperation` sendo construído.</span><span class="sxs-lookup"><span data-stu-id="92de0-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="92de0-232">O `OperationInvoker` classe é um wrapper para o chamador de operação padrão criado para o `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="92de0-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="92de0-233">Essa classe implementa o `IOperationInvoker` interface.</span><span class="sxs-lookup"><span data-stu-id="92de0-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="92de0-234">No `Invoke` implementação do método de invocação de método real é delegada para o chamador da operação interna.</span><span class="sxs-lookup"><span data-stu-id="92de0-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="92de0-235">No entanto, antes de retornar os resultados do Gerenciador de armazenamento no `InstanceContext` é usado para salvar a instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a><span data-ttu-id="92de0-236">Usando a extensão</span><span class="sxs-lookup"><span data-stu-id="92de0-236">Using the Extension</span></span>  
 <span data-ttu-id="92de0-237">As extensões de camada do modelo de canal camada e de serviço são feitas e agora podem ser usados em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="92de0-237">Both the channel layer and service model layer extensions are done and they can now be used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span> <span data-ttu-id="92de0-238">Serviços precisam adicionar o canal a pilha de canais usando uma associação personalizada e, em seguida, marcar as classes de implementação de serviço com os atributos apropriados.</span><span class="sxs-lookup"><span data-stu-id="92de0-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
```  
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
  
 <span data-ttu-id="92de0-239">Aplicativos cliente devem adicionar o DurableInstanceContextChannel na pilha de canais usando uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="92de0-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="92de0-240">Para configurar o canal declarativamente no arquivo de configuração, a seção do elemento de associação deve ser adicionado à coleção de extensões do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="92de0-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="92de0-241">Agora o elemento de associação pode ser usado com uma associação personalizada, assim como outros elementos de associação padrão:</span><span class="sxs-lookup"><span data-stu-id="92de0-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
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
  
## <a name="conclusion"></a><span data-ttu-id="92de0-242">Conclusão</span><span class="sxs-lookup"><span data-stu-id="92de0-242">Conclusion</span></span>  
 <span data-ttu-id="92de0-243">Esse exemplo mostrou como criar um canal de protocolo personalizado e como personalizar o comportamento de serviço para habilitá-lo.</span><span class="sxs-lookup"><span data-stu-id="92de0-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="92de0-244">A extensão pode ser aprimorada ainda mais, permitindo que os usuários especificar o `IStorageManager` implementação usando uma seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="92de0-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="92de0-245">Isso torna possível modificar o repositório de backup sem recompilar o código de serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="92de0-246">Além disso, você pode tentar implementar uma classe (por exemplo, `StateBag`), que encapsula o estado da instância.</span><span class="sxs-lookup"><span data-stu-id="92de0-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="92de0-247">Essa classe é responsável por manter o estado sempre que ele é alterado.</span><span class="sxs-lookup"><span data-stu-id="92de0-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="92de0-248">Dessa forma, você pode evitar o uso de `SaveState` de atributos e executar o trabalho persistente com mais precisão (por exemplo, você pode manter o estado quando o estado é alterado, na verdade, em vez de salvá-lo sempre que quando um método com o `SaveState` atributo é chamado).</span><span class="sxs-lookup"><span data-stu-id="92de0-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="92de0-249">Quando você executar o exemplo, a seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="92de0-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="92de0-250">O cliente adiciona dois itens ao seu carrinho de compras e, em seguida, obtém a lista de itens em seu carrinho de compras do serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="92de0-251">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="92de0-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="92de0-252">Recriar o serviço substitui o arquivo de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="92de0-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="92de0-253">Para observar preservado em várias execuções do exemplo de estado, lembre-se de não recompilar o exemplo entre as execuções.</span><span class="sxs-lookup"><span data-stu-id="92de0-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="92de0-254">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="92de0-254">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="92de0-255">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92de0-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="92de0-256">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92de0-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="92de0-257">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92de0-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92de0-258">Você deve estar executando o SQL Server 2005 ou SQL Express 2005 para executar esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="92de0-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="92de0-259">Se você estiver executando o SQL Server 2005, você deve modificar a configuração de cadeia de caracteres de conexão do serviço.</span><span class="sxs-lookup"><span data-stu-id="92de0-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="92de0-260">Quando em execução entre computadores, o SQL Server é necessário somente na máquina do servidor.</span><span class="sxs-lookup"><span data-stu-id="92de0-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92de0-261">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="92de0-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="92de0-262">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="92de0-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92de0-263">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="92de0-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92de0-264">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="92de0-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a><span data-ttu-id="92de0-265">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92de0-265">See Also</span></span>
