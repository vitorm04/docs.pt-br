---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 64a7cba7b1bbc55a4504e3af4784fcb2a84f0fa1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="httpcookiesession"></a><span data-ttu-id="3fb20-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="3fb20-102">HttpCookieSession</span></span>
<span data-ttu-id="3fb20-103">Este exemplo demonstra como criar um canal de protocolo personalizado para usar cookies HTTP para o gerenciamento de sessão.</span><span class="sxs-lookup"><span data-stu-id="3fb20-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="3fb20-104">Esse canal permite a comunicação entre serviços Windows Communication Foundation (WCF) e clientes ASMX ou entre clientes e serviços ASMX WCF.</span><span class="sxs-lookup"><span data-stu-id="3fb20-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="3fb20-105">Quando um cliente chama um método da Web em um serviço Web ASMX que é baseada em sessão, o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] mecanismo faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3fb20-105">When a client calls a Web method in an ASMX Web service that is session-based, the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] engine does the following:</span></span>  
  
-   <span data-ttu-id="3fb20-106">Gera uma ID exclusiva (ID de sessão).</span><span class="sxs-lookup"><span data-stu-id="3fb20-106">Generates a unique ID (session ID).</span></span>  
  
-   <span data-ttu-id="3fb20-107">Gera o objeto de sessão e a associa a ID exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3fb20-107">Generates the session object and associates it with the unique ID.</span></span>  
  
-   <span data-ttu-id="3fb20-108">Adiciona a ID exclusiva para um cabeçalho de resposta HTTP de Set-Cookie e o envia ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3fb20-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
-   <span data-ttu-id="3fb20-109">Identifica o cliente em chamadas subsequentes com base na ID de sessão envia a ele.</span><span class="sxs-lookup"><span data-stu-id="3fb20-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="3fb20-110">O cliente inclui a ID de sessão em suas solicitações subsequentes para o servidor.</span><span class="sxs-lookup"><span data-stu-id="3fb20-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="3fb20-111">O servidor usa a ID de sessão do cliente para carregar o objeto de sessão apropriada para o contexto HTTP atual.</span><span class="sxs-lookup"><span data-stu-id="3fb20-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3fb20-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3fb20-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3fb20-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3fb20-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3fb20-114">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3fb20-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3fb20-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3fb20-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="3fb20-116">Padrão de troca de mensagens de canal HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="3fb20-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="3fb20-117">Este exemplo habilita sessões para cenários como ASMX.</span><span class="sxs-lookup"><span data-stu-id="3fb20-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="3fb20-118">Na parte inferior da pilha nosso canal, temos o transporte HTTP que dá suporte a <xref:System.ServiceModel.Channels.IRequestChannel> e <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="3fb20-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="3fb20-119">É o trabalho do canal para fornecer sessões para os níveis mais altos da pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="3fb20-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="3fb20-120">O exemplo implementa dois canais (<xref:System.ServiceModel.Channels.IRequestSessionChannel> e <xref:System.ServiceModel.Channels.IReplySessionChannel>) que dão suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="3fb20-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="3fb20-121">Canal de serviço</span><span class="sxs-lookup"><span data-stu-id="3fb20-121">Service Channel</span></span>  
 <span data-ttu-id="3fb20-122">O exemplo fornece um canal de serviço no `HttpCookieReplySessionChannelListener` classe.</span><span class="sxs-lookup"><span data-stu-id="3fb20-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="3fb20-123">Essa classe implementa o <xref:System.ServiceModel.Channels.IChannelListener> interface e converte o <xref:System.ServiceModel.Channels.IReplyChannel> channel das inferior na pilha de canais para um <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3fb20-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="3fb20-124">Esse processo pode ser dividido nas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="3fb20-124">This process can be divided into the following parts:</span></span>  
  
-   <span data-ttu-id="3fb20-125">Quando o ouvinte do canal é aberto, ele aceita um canal interno de seu ouvinte interna.</span><span class="sxs-lookup"><span data-stu-id="3fb20-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="3fb20-126">Porque o ouvinte interno é um ouvinte de datagrama e o tempo de vida de um canal aceito será desacoplado do tempo de vida do ouvinte, podemos fechar o ouvinte interno e apenas manter o canal interno</span><span class="sxs-lookup"><span data-stu-id="3fb20-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   <span data-ttu-id="3fb20-127">Ao concluir o processo de abertura, configuramos um loop de mensagem para receber mensagens do canal interno.</span><span class="sxs-lookup"><span data-stu-id="3fb20-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   <span data-ttu-id="3fb20-128">Quando uma mensagem chega, o canal de serviço examina o identificador de sessão e desmultiplexa para o canal de sessão apropriada.</span><span class="sxs-lookup"><span data-stu-id="3fb20-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="3fb20-129">O ouvinte de canal mantém um dicionário que mapeia os identificadores de sessão para as instâncias de canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="3fb20-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="3fb20-130">O `HttpCookieReplySessionChannel` classe implementa <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3fb20-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="3fb20-131">Os níveis superiores do canal de pilha de chamada a <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> método para solicitações de leitura para esta sessão.</span><span class="sxs-lookup"><span data-stu-id="3fb20-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="3fb20-132">Cada canal de sessão tem uma fila de mensagens particular que é preenchida pelo canal de serviço.</span><span class="sxs-lookup"><span data-stu-id="3fb20-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="3fb20-133">No caso de quando alguém chama o <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> método e não existem mensagens na fila de mensagens, o canal espera por um certo período de tempo antes de desligar em si.</span><span class="sxs-lookup"><span data-stu-id="3fb20-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="3fb20-134">Isso limpa os canais de sessão criados para clientes não WCF.</span><span class="sxs-lookup"><span data-stu-id="3fb20-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="3fb20-135">Usamos o `channelMapping` para controlar a `ReplySessionChannels`, e não podemos fechar nosso subjacente `innerChannel` até que todos os canais aceitos foram fechados.</span><span class="sxs-lookup"><span data-stu-id="3fb20-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="3fb20-136">Dessa forma `HttpCookieReplySessionChannel` pode existir além do tempo de vida de `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="3fb20-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="3fb20-137">Também não temos se preocupar com o ouvinte obtendo limpos sob nos porque os canais aceitos manter uma referência ao seu ouvinte por meio de `OnClosed` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3fb20-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="3fb20-138">Canal do cliente</span><span class="sxs-lookup"><span data-stu-id="3fb20-138">Client channel</span></span>  
 <span data-ttu-id="3fb20-139">O canal de cliente correspondente está no `HttpCookieSessionChannelFactory` classe.</span><span class="sxs-lookup"><span data-stu-id="3fb20-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="3fb20-140">Durante a criação do canal, a fábrica de canais encapsula o canal de solicitação interna com um `HttpCookieRequestSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="3fb20-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="3fb20-141">O `HttpCookieRequestSessionChannel` classe encaminha as chamadas para o canal de solicitação subjacente.</span><span class="sxs-lookup"><span data-stu-id="3fb20-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="3fb20-142">Quando o cliente fecha o proxy, `HttpCookieRequestSessionChannel` envia uma mensagem para o serviço que indica que o canal está sendo fechado.</span><span class="sxs-lookup"><span data-stu-id="3fb20-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="3fb20-143">Portanto, a pilha de canais de serviço normalmente pode encerrar o canal de sessão que está em uso.</span><span class="sxs-lookup"><span data-stu-id="3fb20-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="3fb20-144">Associação e o elemento de associação</span><span class="sxs-lookup"><span data-stu-id="3fb20-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="3fb20-145">Depois de criar os canais de cliente e de serviço, a próxima etapa é para integrá-las em tempo de execução WCF.</span><span class="sxs-lookup"><span data-stu-id="3fb20-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="3fb20-146">Canais são expostos para o WCF por meio de associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="3fb20-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="3fb20-147">Uma associação consiste em um ou vários elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="3fb20-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="3fb20-148">O WCF oferece várias associações definidas pelo sistema; Por exemplo, BasicHttpBinding ou WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="3fb20-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="3fb20-149">O `HttpCookieSessionBindingElement` classe contém a implementação para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="3fb20-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="3fb20-150">Ela substitui a escuta de canal e métodos de criação de fábrica de canal para fazer o canal necessário instanciações de fábrica de canal ou de escuta.</span><span class="sxs-lookup"><span data-stu-id="3fb20-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="3fb20-151">O exemplo usa declarações de política para a descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="3fb20-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="3fb20-152">Isso permite que o exemplo publicar seus requisitos de canal para outros clientes que podem consumir o serviço.</span><span class="sxs-lookup"><span data-stu-id="3fb20-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="3fb20-153">Por exemplo, esse elemento de associação publica declarações de política para informar os clientes potenciais que ele oferece suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="3fb20-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="3fb20-154">Como o exemplo permite que o `ExchangeTerminateMessage` propriedade na configuração de elemento de associação, ele adiciona as declarações necessárias para mostrar que o serviço oferece suporte a uma ação de troca extras de mensagem para terminar a conversa da sessão.</span><span class="sxs-lookup"><span data-stu-id="3fb20-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="3fb20-155">Os clientes podem, em seguida, usar essa ação.</span><span class="sxs-lookup"><span data-stu-id="3fb20-155">Clients can then use this action.</span></span> <span data-ttu-id="3fb20-156">O código a seguir WSDL mostra as declarações de política criadas a partir de `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3fb20-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
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
  
 <span data-ttu-id="3fb20-157">O `HttpCookieSessionBinding` classe é uma associação fornecida pelo sistema que usa o elemento de associação descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3fb20-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="3fb20-158">Adicionando o canal para o sistema de configuração</span><span class="sxs-lookup"><span data-stu-id="3fb20-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="3fb20-159">O exemplo fornece duas classes que expõem o canal de exemplo por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="3fb20-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="3fb20-160">A primeira é uma <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> para o `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3fb20-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="3fb20-161">A maior parte da implementação é delegada ao `HttpCookieSessionBindingConfigurationElement`, que é derivado de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="3fb20-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="3fb20-162">O `HttpCookieSessionBindingConfigurationElement` tem propriedades que correspondem às propriedades em `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3fb20-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="3fb20-163">Seção de extensão do elemento de associação</span><span class="sxs-lookup"><span data-stu-id="3fb20-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="3fb20-164">A seção `HttpCookieSessionBindingElementSection` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `HttpCookieSessionBindingElement` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="3fb20-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="3fb20-165">Com algumas substituições o nome da seção de configuração, o tipo de elemento de associação e como criar o elemento de associação são definidos.</span><span class="sxs-lookup"><span data-stu-id="3fb20-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="3fb20-166">Em seguida, é possível registrar a seção de extensão em um arquivo de configuração da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3fb20-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
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
  
## <a name="test-code"></a><span data-ttu-id="3fb20-167">Código de teste</span><span class="sxs-lookup"><span data-stu-id="3fb20-167">Test Code</span></span>  
 <span data-ttu-id="3fb20-168">Código de teste para usar esse transporte de exemplo está disponível nos diretórios de cliente e de serviço.</span><span class="sxs-lookup"><span data-stu-id="3fb20-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="3fb20-169">Ele consiste em dois testes — um teste usa uma associação com `allowCookies` definida como `true` no cliente.</span><span class="sxs-lookup"><span data-stu-id="3fb20-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="3fb20-170">O segundo teste permite desligamento explícito (usando a troca de mensagens de término) na associação.</span><span class="sxs-lookup"><span data-stu-id="3fb20-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="3fb20-171">Quando você executar o exemplo, você verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3fb20-171">When you run the sample, you should see the following output:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3fb20-172">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3fb20-172">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3fb20-173">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="3fb20-173">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="3fb20-174">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb20-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="3fb20-175">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb20-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="3fb20-176">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb20-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb20-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fb20-177">See Also</span></span>
