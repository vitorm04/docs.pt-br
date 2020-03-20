---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183622"
---
# <a name="httpcookiesession"></a><span data-ttu-id="e0e05-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="e0e05-102">HttpCookieSession</span></span>
<span data-ttu-id="e0e05-103">Esta amostra demonstra como construir um canal de protocolo personalizado para usar cookies HTTP para gerenciamento de sessões.</span><span class="sxs-lookup"><span data-stu-id="e0e05-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="e0e05-104">Este canal permite a comunicação entre os serviços da Windows Communication Foundation (WCF) e os clientes ASMX ou entre clientes WCF e serviços ASMX.</span><span class="sxs-lookup"><span data-stu-id="e0e05-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="e0e05-105">Quando um cliente chama um método Web em um serviço WEB ASMX baseado em sessão, o mecanismo ASP.NET faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0e05-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="e0e05-106">Gera um ID único (ID de sessão).</span><span class="sxs-lookup"><span data-stu-id="e0e05-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="e0e05-107">Gera o objeto de sessão e o associa ao ID único.</span><span class="sxs-lookup"><span data-stu-id="e0e05-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="e0e05-108">Adiciona o ID exclusivo a um cabeçalho de resposta HTTP do Set-Cookie e envia-o ao cliente.</span><span class="sxs-lookup"><span data-stu-id="e0e05-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="e0e05-109">Identifica o cliente em chamadas subseqüentes com base no ID de sessão que ele envia para ele.</span><span class="sxs-lookup"><span data-stu-id="e0e05-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="e0e05-110">O cliente inclui este ID de sessão em suas solicitações subseqüentes ao servidor.</span><span class="sxs-lookup"><span data-stu-id="e0e05-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="e0e05-111">O servidor usa o ID de sessão do cliente para carregar o objeto de sessão apropriado para o contexto HTTP atual.</span><span class="sxs-lookup"><span data-stu-id="e0e05-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e0e05-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e0e05-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e0e05-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e0e05-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e0e05-114">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="e0e05-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e0e05-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e0e05-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="e0e05-116">Padrão de troca de mensagens do canal httpcookiesession</span><span class="sxs-lookup"><span data-stu-id="e0e05-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="e0e05-117">Esta amostra permite sessões para cenários semelhantes ao ASMX.</span><span class="sxs-lookup"><span data-stu-id="e0e05-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="e0e05-118">Na parte inferior da nossa pilha de canais, <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IReplyChannel>temos o transporte HTTP que suporta e .</span><span class="sxs-lookup"><span data-stu-id="e0e05-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="e0e05-119">É trabalho do canal fornecer sessões para os níveis mais altos da pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="e0e05-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="e0e05-120">A amostra implementa dois<xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>canais, (e ) que suportam sessões.</span><span class="sxs-lookup"><span data-stu-id="e0e05-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="e0e05-121">Canal de Serviços</span><span class="sxs-lookup"><span data-stu-id="e0e05-121">Service Channel</span></span>  
 <span data-ttu-id="e0e05-122">A amostra fornece um `HttpCookieReplySessionChannelListener` canal de serviço na classe.</span><span class="sxs-lookup"><span data-stu-id="e0e05-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="e0e05-123">Esta classe implementa a <xref:System.ServiceModel.Channels.IChannelListener> interface <xref:System.ServiceModel.Channels.IReplyChannel> e converte o canal <xref:System.ServiceModel.Channels.IReplySessionChannel>de inferior na pilha de canais para um .</span><span class="sxs-lookup"><span data-stu-id="e0e05-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="e0e05-124">Este processo pode ser dividido nas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="e0e05-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="e0e05-125">Quando o ouvinte do canal é aberto, ele aceita um canal interno de seu ouvinte interno.</span><span class="sxs-lookup"><span data-stu-id="e0e05-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="e0e05-126">Como o ouvinte interno é um ouvinte de datagrama e a vida de um canal aceito é dissociada da vida do ouvinte, podemos fechar o ouvinte interno e apenas segurar o canal interno</span><span class="sxs-lookup"><span data-stu-id="e0e05-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="e0e05-127">Quando o processo aberto é concluído, configuramos um loop de mensagem para receber mensagens do canal interno.</span><span class="sxs-lookup"><span data-stu-id="e0e05-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="e0e05-128">Quando uma mensagem chega, o canal de serviço examina o identificador de sessão e os desmultiplexes para o canal de sessão apropriado.</span><span class="sxs-lookup"><span data-stu-id="e0e05-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="e0e05-129">O ouvinte do canal mantém um dicionário que mapeia os identificadores de sessão para as instâncias do canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="e0e05-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="e0e05-130">A `HttpCookieReplySessionChannel` classe <xref:System.ServiceModel.Channels.IReplySessionChannel>implementa.</span><span class="sxs-lookup"><span data-stu-id="e0e05-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="e0e05-131">Níveis mais altos da <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> pilha de canais chamam o método para ler solicitações para esta sessão.</span><span class="sxs-lookup"><span data-stu-id="e0e05-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="e0e05-132">Cada canal de sessão tem uma fila de mensagens privada que é preenchida pelo canal de serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e05-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="e0e05-133">No caso em que <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> alguém chama o método e não há mensagens na fila de mensagens, o canal espera por um determinado período de tempo antes de se desligar.</span><span class="sxs-lookup"><span data-stu-id="e0e05-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="e0e05-134">Isso limpa os canais de sessão criados para clientes não-WCF.</span><span class="sxs-lookup"><span data-stu-id="e0e05-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="e0e05-135">Usamos o `channelMapping` para `ReplySessionChannels`rastrear o , e não `innerChannel` fechamos nosso si mesmo até que todos os canais aceitos tenham sido fechados.</span><span class="sxs-lookup"><span data-stu-id="e0e05-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="e0e05-136">Desta `HttpCookieReplySessionChannel` forma pode existir `HttpCookieReplySessionChannelListener`além da vida de .</span><span class="sxs-lookup"><span data-stu-id="e0e05-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="e0e05-137">Também não temos que nos preocupar com o ouvinte recebendo lixo coletado em baixo `OnClosed` de nós porque os canais aceitos mantêm uma referência ao seu ouvinte através do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e0e05-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="e0e05-138">Canal do cliente</span><span class="sxs-lookup"><span data-stu-id="e0e05-138">Client channel</span></span>  
 <span data-ttu-id="e0e05-139">O canal do cliente `HttpCookieSessionChannelFactory` correspondente está na classe.</span><span class="sxs-lookup"><span data-stu-id="e0e05-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="e0e05-140">Durante a criação do canal, a fábrica `HttpCookieRequestSessionChannel`do canal envolve o canal de solicitação interna com um .</span><span class="sxs-lookup"><span data-stu-id="e0e05-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="e0e05-141">A `HttpCookieRequestSessionChannel` classe encaminha as chamadas para o canal de solicitação subjacente.</span><span class="sxs-lookup"><span data-stu-id="e0e05-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="e0e05-142">Quando o cliente fecha `HttpCookieRequestSessionChannel` o proxy, envia uma mensagem para o serviço que indica que o canal está sendo fechado.</span><span class="sxs-lookup"><span data-stu-id="e0e05-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="e0e05-143">Assim, a pilha de canais de serviço pode desligar graciosamente o canal de sessão que está em uso.</span><span class="sxs-lookup"><span data-stu-id="e0e05-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="e0e05-144">Elemento de vinculação e vinculação</span><span class="sxs-lookup"><span data-stu-id="e0e05-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="e0e05-145">Depois de criar os canais de atendimento e cliente, o próximo passo é integrá-los ao tempo de execução do WCF.</span><span class="sxs-lookup"><span data-stu-id="e0e05-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="e0e05-146">Os canais são expostos ao WCF através de amarras e elementos de ligação.</span><span class="sxs-lookup"><span data-stu-id="e0e05-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="e0e05-147">Uma ligação consiste em um ou muitos elementos de ligação.</span><span class="sxs-lookup"><span data-stu-id="e0e05-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="e0e05-148">O WCF oferece várias vinculações definidas pelo sistema; por exemplo, BasicHttpBinding ou WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="e0e05-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="e0e05-149">A `HttpCookieSessionBindingElement` classe contém a implementação para o elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="e0e05-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="e0e05-150">Ele substitui os métodos de criação do ouvinte do canal e da fábrica do canal para fazer as instanciações necessárias do ouvinte do canal ou da fábrica do canal.</span><span class="sxs-lookup"><span data-stu-id="e0e05-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="e0e05-151">A amostra usa afirmações de políticas para a descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e05-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="e0e05-152">Isso permite que a amostra publique suas necessidades de canal para outros clientes que possam consumir o serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e05-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="e0e05-153">Por exemplo, esse elemento vinculante publica afirmações de políticas para que os clientes em potencial saibam que ele suporta sessões.</span><span class="sxs-lookup"><span data-stu-id="e0e05-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="e0e05-154">Como a amostra `ExchangeTerminateMessage` habilita a propriedade na configuração do elemento de vinculação, ela adiciona as afirmações necessárias para mostrar que o serviço suporta uma ação extra de troca de mensagens para encerrar a conversa da sessão.</span><span class="sxs-lookup"><span data-stu-id="e0e05-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="e0e05-155">Os clientes podem então usar essa ação.</span><span class="sxs-lookup"><span data-stu-id="e0e05-155">Clients can then use this action.</span></span> <span data-ttu-id="e0e05-156">O código WSDL a seguir mostra as `HttpCookieSessionBindingElement`afirmações de políticas criadas a partir do .</span><span class="sxs-lookup"><span data-stu-id="e0e05-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
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
  
 <span data-ttu-id="e0e05-157">A `HttpCookieSessionBinding` classe é uma vinculação fornecida pelo sistema que usa o elemento de vinculação descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e0e05-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="e0e05-158">Adicionando o Canal ao Sistema de Configuração</span><span class="sxs-lookup"><span data-stu-id="e0e05-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="e0e05-159">A amostra fornece duas classes que expõem o canal amostral através da configuração.</span><span class="sxs-lookup"><span data-stu-id="e0e05-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="e0e05-160">O primeiro <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> é `HttpCookieSessionBindingElement`um para o .</span><span class="sxs-lookup"><span data-stu-id="e0e05-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="e0e05-161">A maior parte da implementação `HttpCookieSessionBindingConfigurationElement`é delegada <xref:System.ServiceModel.Configuration.StandardBindingElement>ao , que deriva de .</span><span class="sxs-lookup"><span data-stu-id="e0e05-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="e0e05-162">O `HttpCookieSessionBindingConfigurationElement` tem propriedades que correspondem às propriedades em `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="e0e05-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="e0e05-163">Seção de extensão do elemento de vinculação</span><span class="sxs-lookup"><span data-stu-id="e0e05-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="e0e05-164">A `HttpCookieSessionBindingElementSection` seção <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> é `HttpCookieSessionBindingElement` uma que se expõe ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="e0e05-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="e0e05-165">Com algumas substituições do nome da seção de configuração, o tipo do elemento de vinculação e como criar o elemento de vinculação são definidos.</span><span class="sxs-lookup"><span data-stu-id="e0e05-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="e0e05-166">Podemos então registrar a seção de extensão em um arquivo de configuração da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e0e05-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
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
  
## <a name="test-code"></a><span data-ttu-id="e0e05-167">Código de teste</span><span class="sxs-lookup"><span data-stu-id="e0e05-167">Test Code</span></span>  
 <span data-ttu-id="e0e05-168">O código de teste para o uso deste transporte de amostra está disponível nos diretórios Cliente e Serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e05-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="e0e05-169">Ele consiste em dois testes — um `allowCookies` teste `true` usa uma vinculação com set para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e0e05-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="e0e05-170">O segundo teste permite o desligamento explícito (usando a troca de mensagens de término) na vinculação.</span><span class="sxs-lookup"><span data-stu-id="e0e05-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="e0e05-171">Ao executar a amostra, você deve ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e0e05-171">When you run the sample, you should see the following output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0e05-172">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e0e05-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e0e05-173">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="e0e05-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="e0e05-174">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e05-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="e0e05-175">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e05-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e0e05-176">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e05-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
