---
title: Interoperabilidade com aplicativos de POX
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6dbdd72dce196ea58550cff956a7b0e6fe0b1a73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="9db0f-102">Interoperabilidade com aplicativos de POX</span><span class="sxs-lookup"><span data-stu-id="9db0f-102">Interoperability with POX Applications</span></span>
<span data-ttu-id="9db0f-103">"Plain Old XML" (POX) os aplicativos se comunicam troca de mensagens HTTP brutas que contêm apenas dados de aplicativo XML que não são incluídos em um envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="9db0f-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="9db0f-104">pode fornecer serviços e clientes que usam mensagens POX.</span><span class="sxs-lookup"><span data-stu-id="9db0f-104"> can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="9db0f-105">Sobre o serviço, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode ser usado para implementar serviços que expõe pontos de extremidade para os clientes, como navegadores da Web e linguagens de script que enviar e recebem mensagens POX.</span><span class="sxs-lookup"><span data-stu-id="9db0f-105">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="9db0f-106">No cliente, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação pode ser usado para implementar a clientes que se comunicam com serviços baseados em POX.</span><span class="sxs-lookup"><span data-stu-id="9db0f-106">On the client, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9db0f-107">Este documento foi gravado originalmente para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="9db0f-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]<span data-ttu-id="9db0f-108">3.5 tem suporte interno para trabalhar com aplicativos de POX.</span><span class="sxs-lookup"><span data-stu-id="9db0f-108"> 3.5 has built-in support for working with POX applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9db0f-109">consulte [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="9db0f-109"> see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span></span>  
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="9db0f-110">Programação de POX com WCF</span><span class="sxs-lookup"><span data-stu-id="9db0f-110">POX Programming with WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9db0f-111">serviços que se comunicam por HTTP usando mensagens POX, use um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="9db0f-111"> services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="9db0f-112">Essa associação personalizada contém dois elementos:</span><span class="sxs-lookup"><span data-stu-id="9db0f-112">This custom binding contains two elements:</span></span>  
  
-   <span data-ttu-id="9db0f-113">O [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) e</span><span class="sxs-lookup"><span data-stu-id="9db0f-113">The [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) and</span></span>  
  
-   <span data-ttu-id="9db0f-114">O [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="9db0f-114">The [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
 <span data-ttu-id="9db0f-115">O padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] codificador de mensagem de texto é especialmente configurado para usar o <xref:System.ServiceModel.Channels.MessageVersion.None%2A> valor, o que permite processar XML cargas de mensagem que não chegam encapsuladas em um envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="9db0f-115">The standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9db0f-116">os clientes que se comunicam por HTTP usando mensagens POX usam uma associação semelhante (mostrada no seguinte código obrigatório).</span><span class="sxs-lookup"><span data-stu-id="9db0f-116"> clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 <span data-ttu-id="9db0f-117">Como clientes POX devem especificar explicitamente os URIs que enviam mensagens, eles geralmente devem configurar o <xref:System.ServiceModel.Channels.HttpTransportBindingElement> para um modo de endereçamento manual definindo a <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> propriedade `true` no elemento.</span><span class="sxs-lookup"><span data-stu-id="9db0f-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="9db0f-118">Isso permite que mensagens sejam tratados explicitamente pelo código do aplicativo e não é necessário criar um novo <xref:System.ServiceModel.ChannelFactory> toda vez que um aplicativo envia uma mensagem para um URI diferente de HTTP.</span><span class="sxs-lookup"><span data-stu-id="9db0f-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>  
  
 <span data-ttu-id="9db0f-119">Como mensagens POX não usar cabeçalhos SOAP para transmitir informações importantes de protocolo, clientes POX e serviços geralmente devem manipular partes da solicitação HTTP subjacente usado para enviar ou receber uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9db0f-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="9db0f-120">Informações de protocolo HTTP específicas, como os cabeçalhos HTTP e códigos de status são apresentados no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação por meio de duas classes:</span><span class="sxs-lookup"><span data-stu-id="9db0f-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model through two classes:</span></span>  
  
-   <span data-ttu-id="9db0f-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, que contém informações sobre a solicitação HTTP, como os cabeçalhos de solicitação e o método HTTP.</span><span class="sxs-lookup"><span data-stu-id="9db0f-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>  
  
-   <span data-ttu-id="9db0f-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, que contém informações sobre a resposta HTTP, como a descrição de status e o código de status HTTP, bem como quaisquer cabeçalhos de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="9db0f-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>  
  
 <span data-ttu-id="9db0f-123">O exemplo de código a seguir mostra como criar uma mensagem HTTP GET solicitação endereçado http://localhost:8100/clientes.</span><span class="sxs-lookup"><span data-stu-id="9db0f-123">The following code example shows how to create an HTTP GET request message that is addressed to http://localhost:8100/customers.</span></span>  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 <span data-ttu-id="9db0f-124">Primeiro, uma solicitação vazia <xref:System.ServiceModel.Channels.Message> é criado chamando <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="9db0f-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="9db0f-125">O <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parâmetro é usado para indicar que não é necessário um envelope SOAP e <xref:System.String.Empty> parâmetro é passado como a ação.</span><span class="sxs-lookup"><span data-stu-id="9db0f-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="9db0f-126">A mensagem de solicitação é processada definindo <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> cabeçalho para o URI desejado.</span><span class="sxs-lookup"><span data-stu-id="9db0f-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="9db0f-127">Em seguida, uma <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> é criado e o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> está definido para o verbo HTTP GET método e o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> é definido como `true` para indicar que nenhum dado deve ser enviado no corpo da mensagem de solicitação HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="9db0f-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="9db0f-128">Por fim, a propriedade de solicitação é adicionada para o <xref:System.ServiceModel.Channels.Message.Properties%2A> coleção da mensagem de solicitação para que ele pode influenciar como o transporte HTTP envia a solicitação.</span><span class="sxs-lookup"><span data-stu-id="9db0f-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="9db0f-129">A mensagem está pronta para ser enviados em uma instância apropriada do <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="9db0f-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>  
  
 <span data-ttu-id="9db0f-130">Técnicas semelhantes podem ser usadas no serviço para extrair a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> de uma mensagem de entrada e a construção de uma resposta.</span><span class="sxs-lookup"><span data-stu-id="9db0f-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
