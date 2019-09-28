---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: af624305e4ab4678938b7f63c4e4056404de0bc9
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393130"
---
# <a name="httpcookiesession"></a><span data-ttu-id="3ee35-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="3ee35-102">HttpCookieSession</span></span>
<span data-ttu-id="3ee35-103">Este exemplo demonstra como criar um canal de protocolo personalizado para usar cookies HTTP para gerenciamento de sessão.</span><span class="sxs-lookup"><span data-stu-id="3ee35-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="3ee35-104">Esse canal permite a comunicação entre os serviços de Windows Communication Foundation (WCF) e os clientes ASMX ou entre clientes WCF e serviços ASMX.</span><span class="sxs-lookup"><span data-stu-id="3ee35-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="3ee35-105">Quando um cliente chama um método Web em um serviço Web ASMX baseado em sessão, o mecanismo ASP.NET faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3ee35-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="3ee35-106">Gera uma ID exclusiva (ID de sessão).</span><span class="sxs-lookup"><span data-stu-id="3ee35-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="3ee35-107">Gera o objeto de sessão e o associa com a ID exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3ee35-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="3ee35-108">Adiciona a ID exclusiva a um cabeçalho de resposta HTTP Set-cookie e a envia ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3ee35-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="3ee35-109">Identifica o cliente em chamadas subsequentes com base na ID de sessão que ele envia a ele.</span><span class="sxs-lookup"><span data-stu-id="3ee35-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="3ee35-110">O cliente inclui essa ID de sessão em suas solicitações subsequentes para o servidor.</span><span class="sxs-lookup"><span data-stu-id="3ee35-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="3ee35-111">O servidor usa a ID de sessão do cliente para carregar o objeto de sessão apropriado para o contexto HTTP atual.</span><span class="sxs-lookup"><span data-stu-id="3ee35-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ee35-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3ee35-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3ee35-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3ee35-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3ee35-114">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="3ee35-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ee35-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3ee35-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="3ee35-116">Padrão de troca de mensagens do canal HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="3ee35-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="3ee35-117">Este exemplo habilita sessões para cenários semelhantes a ASMX.</span><span class="sxs-lookup"><span data-stu-id="3ee35-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="3ee35-118">Na parte inferior da pilha do canal, temos o transporte HTTP que dá suporte <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>e.</span><span class="sxs-lookup"><span data-stu-id="3ee35-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="3ee35-119">É o trabalho do canal para fornecer sessões para os níveis mais altos da pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="3ee35-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="3ee35-120">O exemplo implementa dois canais (<xref:System.ServiceModel.Channels.IRequestSessionChannel> e <xref:System.ServiceModel.Channels.IReplySessionChannel>) que dão suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="3ee35-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="3ee35-121">Canal de serviço</span><span class="sxs-lookup"><span data-stu-id="3ee35-121">Service Channel</span></span>  
 <span data-ttu-id="3ee35-122">O exemplo fornece um canal de serviço na `HttpCookieReplySessionChannelListener` classe.</span><span class="sxs-lookup"><span data-stu-id="3ee35-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="3ee35-123">Essa classe implementa a <xref:System.ServiceModel.Channels.IChannelListener> interface e converte o <xref:System.ServiceModel.Channels.IReplyChannel> canal de baixo na pilha de canais para um <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3ee35-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="3ee35-124">Esse processo pode ser dividido nas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="3ee35-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="3ee35-125">Quando o ouvinte de canal é aberto, ele aceita um canal interno de seu ouvinte interno.</span><span class="sxs-lookup"><span data-stu-id="3ee35-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="3ee35-126">Como o ouvinte interno é um ouvinte de datagrama e o tempo de vida de um canal aceito é dissociado do tempo de vida do ouvinte, podemos fechar o ouvinte interno e manter apenas o canal interno</span><span class="sxs-lookup"><span data-stu-id="3ee35-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="3ee35-127">Quando o processo aberto é concluído, configuramos um loop de mensagem para receber mensagens do canal interno.</span><span class="sxs-lookup"><span data-stu-id="3ee35-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="3ee35-128">Quando uma mensagem chega, o canal de serviço examina o identificador de sessão e os demultiplexs para o canal de sessão apropriado.</span><span class="sxs-lookup"><span data-stu-id="3ee35-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="3ee35-129">O ouvinte de canal mantém um dicionário que mapeia os identificadores de sessão para as instâncias de canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="3ee35-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="3ee35-130">A `HttpCookieReplySessionChannel` classe implementa <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3ee35-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="3ee35-131">Níveis mais altos da pilha de canal chamam <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> o método para ler solicitações para esta sessão.</span><span class="sxs-lookup"><span data-stu-id="3ee35-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="3ee35-132">Cada canal de sessão tem uma fila de mensagens privada que é populada pelo canal de serviço.</span><span class="sxs-lookup"><span data-stu-id="3ee35-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="3ee35-133">No caso em que alguém chama o <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> método e não há mensagens na fila de mensagens, o canal aguarda um período de tempo especificado antes de desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="3ee35-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="3ee35-134">Isso limpa os canais de sessão criados para clientes não WCF.</span><span class="sxs-lookup"><span data-stu-id="3ee35-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="3ee35-135">Usamos o `channelMapping` para acompanhar o `ReplySessionChannels`e não fechamos nosso subjacente `innerChannel` até que todos os canais aceitos tenham sido fechados.</span><span class="sxs-lookup"><span data-stu-id="3ee35-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="3ee35-136">Dessa forma `HttpCookieReplySessionChannel` , pode existir além do tempo `HttpCookieReplySessionChannelListener`de vida de.</span><span class="sxs-lookup"><span data-stu-id="3ee35-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="3ee35-137">Também não precisamos nos preocupar com o ouvinte que está recebendo o lixo para baixo, pois os canais aceitos mantêm uma referência ao ouvinte por meio do retorno de `OnClosed` chamada.</span><span class="sxs-lookup"><span data-stu-id="3ee35-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="3ee35-138">Canal de cliente</span><span class="sxs-lookup"><span data-stu-id="3ee35-138">Client channel</span></span>  
 <span data-ttu-id="3ee35-139">O canal do cliente correspondente está na `HttpCookieSessionChannelFactory` classe.</span><span class="sxs-lookup"><span data-stu-id="3ee35-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="3ee35-140">Durante a criação do canal, a fábrica de canais encapsula o canal de solicitação `HttpCookieRequestSessionChannel`interno com um.</span><span class="sxs-lookup"><span data-stu-id="3ee35-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="3ee35-141">A `HttpCookieRequestSessionChannel` classe encaminha as chamadas para o canal de solicitação subjacente.</span><span class="sxs-lookup"><span data-stu-id="3ee35-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="3ee35-142">Quando o cliente fecha o proxy, `HttpCookieRequestSessionChannel` o envia uma mensagem para o serviço que indica que o canal está sendo fechado.</span><span class="sxs-lookup"><span data-stu-id="3ee35-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="3ee35-143">Assim, a pilha de canais de serviço pode desligar normalmente o canal de sessão que está em uso.</span><span class="sxs-lookup"><span data-stu-id="3ee35-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="3ee35-144">Elemento Binding e Binding</span><span class="sxs-lookup"><span data-stu-id="3ee35-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="3ee35-145">Depois de criar os canais de serviço e cliente, a próxima etapa é integrá-los ao tempo de execução do WCF.</span><span class="sxs-lookup"><span data-stu-id="3ee35-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="3ee35-146">Os canais são expostos ao WCF por meio de associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="3ee35-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="3ee35-147">Uma associação consiste em um ou vários elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="3ee35-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="3ee35-148">O WCF oferece várias associações definidas pelo sistema; por exemplo, BasicHttpBinding ou WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="3ee35-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="3ee35-149">A `HttpCookieSessionBindingElement` classe contém a implementação para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="3ee35-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="3ee35-150">Ele substitui o ouvinte do canal e os métodos de criação de fábrica de canal para fazer as instanciações necessárias do canal ou do ouvinte de canal.</span><span class="sxs-lookup"><span data-stu-id="3ee35-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="3ee35-151">O exemplo usa declarações de política para a descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="3ee35-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="3ee35-152">Isso permite que o exemplo publique seus requisitos de canal para outros clientes que podem consumir o serviço.</span><span class="sxs-lookup"><span data-stu-id="3ee35-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="3ee35-153">Por exemplo, esse elemento de associação publica declarações de política para permitir que clientes potenciais saibam que ele dá suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="3ee35-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="3ee35-154">Como o exemplo habilita a `ExchangeTerminateMessage` Propriedade na configuração do elemento de associação, ele adiciona as declarações necessárias para mostrar que o serviço dá suporte a uma ação de troca de mensagens extra para encerrar a conversa da sessão.</span><span class="sxs-lookup"><span data-stu-id="3ee35-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="3ee35-155">Os clientes podem usar essa ação.</span><span class="sxs-lookup"><span data-stu-id="3ee35-155">Clients can then use this action.</span></span> <span data-ttu-id="3ee35-156">O código WSDL a seguir mostra as declarações de política criadas a `HttpCookieSessionBindingElement`partir do.</span><span class="sxs-lookup"><span data-stu-id="3ee35-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="3ee35-157">A `HttpCookieSessionBinding` classe é uma associação fornecida pelo sistema que usa o elemento de associação descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ee35-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="3ee35-158">Adicionando o canal ao sistema de configuração</span><span class="sxs-lookup"><span data-stu-id="3ee35-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="3ee35-159">O exemplo fornece duas classes que expõem o canal de exemplo por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="3ee35-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="3ee35-160">O primeiro é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> para o `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3ee35-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="3ee35-161">A maior parte da implementação é delegada para o `HttpCookieSessionBindingConfigurationElement`, que deriva de. <xref:System.ServiceModel.Configuration.StandardBindingElement></span><span class="sxs-lookup"><span data-stu-id="3ee35-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="3ee35-162">O `HttpCookieSessionBindingConfigurationElement` tem propriedades que correspondem às propriedades em `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3ee35-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="3ee35-163">Seção de extensão do elemento de associação</span><span class="sxs-lookup"><span data-stu-id="3ee35-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="3ee35-164">A seção `HttpCookieSessionBindingElementSection` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `HttpCookieSessionBindingElement` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="3ee35-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="3ee35-165">Com algumas substituições do nome da seção de configuração, o tipo do elemento de associação e como criar o elemento de associação são definidos.</span><span class="sxs-lookup"><span data-stu-id="3ee35-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="3ee35-166">Em seguida, podemos registrar a seção de extensão em um arquivo de configuração da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3ee35-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="3ee35-167">Código de teste</span><span class="sxs-lookup"><span data-stu-id="3ee35-167">Test Code</span></span>  
 <span data-ttu-id="3ee35-168">O código de teste para usar esse transporte de exemplo está disponível nos diretórios de cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="3ee35-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="3ee35-169">Ele consiste em dois testes: um teste usa uma associação com `allowCookies` definido como `true` no cliente.</span><span class="sxs-lookup"><span data-stu-id="3ee35-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="3ee35-170">O segundo teste habilita o desligamento explícito (usando a troca de mensagens de encerramento) na associação.</span><span class="sxs-lookup"><span data-stu-id="3ee35-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="3ee35-171">Ao executar o exemplo, você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3ee35-171">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3ee35-172">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3ee35-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3ee35-173">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="3ee35-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="3ee35-174">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ee35-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="3ee35-175">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ee35-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3ee35-176">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ee35-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
