---
title: Interoperabilidade com aplicativos POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 64a6d850a32b14bc60cd43466e04b53a7a39be81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579261"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="65fde-102">Interoperabilidade com aplicativos POX</span><span class="sxs-lookup"><span data-stu-id="65fde-102">Interoperability with POX applications</span></span>

<span data-ttu-id="65fde-103">Os aplicativos de "POX (XML antigo") se comunicam por meio da troca de mensagens HTTP brutas que contêm apenas dados de aplicativos XML que não estão incluídos em um envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="65fde-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="65fde-104">O Windows Communication Foundation (WCF) pode fornecer serviços e clientes que usam mensagens POX.</span><span class="sxs-lookup"><span data-stu-id="65fde-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="65fde-105">No serviço, o WCF pode ser usado para implementar serviços que exponham pontos de extremidade para clientes como navegadores da Web e linguagens de script que enviam e recebem mensagens POX.</span><span class="sxs-lookup"><span data-stu-id="65fde-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="65fde-106">No cliente, o modelo de programação do WCF pode ser usado para implementar clientes que se comunicam com serviços baseados em POX.</span><span class="sxs-lookup"><span data-stu-id="65fde-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65fde-107">Este documento foi escrito originalmente para o .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="65fde-107">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="65fde-108">.NET Framework 3,5 tem suporte interno para trabalhar com aplicativos POX.</span><span class="sxs-lookup"><span data-stu-id="65fde-108">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="65fde-109">Para obter mais informações sobre como consultar o [modelo de programação do WCF Web http](wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="65fde-109">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="65fde-110">Programação POX com WCF</span><span class="sxs-lookup"><span data-stu-id="65fde-110">POX programming with WCF</span></span>

<span data-ttu-id="65fde-111">Os serviços WCF que se comunicam por HTTP usando mensagens POX usam um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="65fde-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="65fde-112">Essa associação personalizada contém dois elementos:</span><span class="sxs-lookup"><span data-stu-id="65fde-112">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="65fde-113">O codificador de mensagem de texto do WCF padrão é especialmente configurado para usar o <xref:System.ServiceModel.Channels.MessageVersion.None%2A> valor, que permite processar cargas de mensagens XML que não chegam encapsuladas em um envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="65fde-113">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="65fde-114">Os clientes WCF que se comunicam por HTTP usando mensagens POX usam uma associação semelhante (mostrada no código imperativo a seguir).</span><span class="sxs-lookup"><span data-stu-id="65fde-114">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="65fde-115">Como os clientes POX devem especificar explicitamente os URIs para os quais eles enviam mensagens, eles geralmente devem configurar o <xref:System.ServiceModel.Channels.HttpTransportBindingElement> para um modo de endereçamento manual, definindo a <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> propriedade como `true` no elemento.</span><span class="sxs-lookup"><span data-stu-id="65fde-115">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="65fde-116">Isso permite que as mensagens sejam resolvidas explicitamente pelo código do aplicativo e não é necessário criar uma nova <xref:System.ServiceModel.ChannelFactory> toda vez que um aplicativo envia uma mensagem para um URI http diferente.</span><span class="sxs-lookup"><span data-stu-id="65fde-116">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="65fde-117">Como as mensagens POX não usam cabeçalhos SOAP para transmitir informações importantes de protocolo, os clientes POX e os serviços geralmente devem manipular partes da solicitação HTTP subjacente usada para enviar ou receber uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="65fde-117">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="65fde-118">As informações de protocolo específicas de HTTP, como os cabeçalhos HTTP e os códigos de status, são apresentadas no modelo de programação do WCF por meio de duas classes:</span><span class="sxs-lookup"><span data-stu-id="65fde-118">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="65fde-119"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, que contém informações sobre a solicitação HTTP, como o método HTTP e cabeçalhos de solicitação.</span><span class="sxs-lookup"><span data-stu-id="65fde-119"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="65fde-120"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, que contém informações sobre a resposta HTTP, como o código de status HTTP e a descrição do status, bem como quaisquer cabeçalhos de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="65fde-120"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="65fde-121">O exemplo de código a seguir mostra como criar uma mensagem de solicitação HTTP GET que é endereçada ao `http://localhost:8100/customers` .</span><span class="sxs-lookup"><span data-stu-id="65fde-121">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="65fde-122">Primeiro, uma solicitação vazia <xref:System.ServiceModel.Channels.Message> é criada chamando <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="65fde-122">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="65fde-123">O <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parâmetro é usado para indicar que um envelope SOAP não é necessário e <xref:System.String.Empty> o parâmetro é passado como a ação.</span><span class="sxs-lookup"><span data-stu-id="65fde-123">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="65fde-124">Em seguida, a mensagem de solicitação é resolvida definindo <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> o cabeçalho como o URI desejado.</span><span class="sxs-lookup"><span data-stu-id="65fde-124">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="65fde-125">Em seguida, um <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> é criado e o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> é definido como o método Get do verbo HTTP e o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> é definido como `true` para indicar que nenhum dado deve ser enviado no corpo da mensagem de solicitação HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="65fde-125">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="65fde-126">Por fim, a propriedade Request é adicionada à <xref:System.ServiceModel.Channels.Message.Properties%2A> coleção da mensagem de solicitação para que ela possa influenciar como o transporte http envia a solicitação.</span><span class="sxs-lookup"><span data-stu-id="65fde-126">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="65fde-127">A mensagem está pronta para ser enviada por uma instância apropriada do <xref:System.ServiceModel.Channels.IRequestChannel> .</span><span class="sxs-lookup"><span data-stu-id="65fde-127">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="65fde-128">Técnicas semelhantes podem ser usadas no serviço para extrair o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> de uma mensagem de entrada e construir uma resposta.</span><span class="sxs-lookup"><span data-stu-id="65fde-128">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
