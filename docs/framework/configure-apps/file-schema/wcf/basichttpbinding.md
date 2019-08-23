---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 2ae8a9d2ad7bf3607394e65570b8961fd2d58606
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919877"
---
# <a name="basichttpbinding"></a><span data-ttu-id="f39e1-101">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f39e1-101">\<basicHttpBinding></span></span>
<span data-ttu-id="f39e1-102">Representa uma associação que um serviço do WCF (Windows Communication Foundation) pode usar para configurar e expor pontos de extremidade capazes de se comunicar com clientes e serviços Web baseados em ASMX e outros serviços que estejam em conformidade com o WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="f39e1-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="f39e1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f39e1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f39e1-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f39e1-104">\<bindings></span></span>  
<span data-ttu-id="f39e1-105">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f39e1-105">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39e1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f39e1-106">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f39e1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f39e1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f39e1-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f39e1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f39e1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f39e1-109">Attributes</span></span>  
  
|<span data-ttu-id="f39e1-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="f39e1-110">Attribute</span></span>|<span data-ttu-id="f39e1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f39e1-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="f39e1-112">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="f39e1-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="f39e1-113">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f39e1-114">Você pode usar essa propriedade ao interagir com serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="f39e1-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="f39e1-115">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="f39e1-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="f39e1-116">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="f39e1-116">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="f39e1-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f39e1-118">Um recurso da Internet será local se ele tiver um endereço local.</span><span class="sxs-lookup"><span data-stu-id="f39e1-118">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="f39e1-119">Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="f39e1-119">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="f39e1-120">Definir esse atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="f39e1-120">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="f39e1-121">Se esse atributo for `true`, as solicitações para os recursos locais da Internet não usarão o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="f39e1-121">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="f39e1-122">Use o nome do host (em vez de localhost) se desejar que os clientes passem por um proxy ao se comunicar com os serviços no mesmo computador quando esse `true`atributo for definido como.</span><span class="sxs-lookup"><span data-stu-id="f39e1-122">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="f39e1-123">Quando esse atributo é `false`, todas as solicitações da Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="f39e1-123">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="f39e1-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="f39e1-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f39e1-125">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f39e1-126">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f39e1-126">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="f39e1-127">Especifica a versão do SOAP que é usada para mensagens que são processadas por essa associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-127">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="f39e1-128">O único valor válido é Soap11.</span><span class="sxs-lookup"><span data-stu-id="f39e1-128">The only valid value is Soap11.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="f39e1-129">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="f39e1-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f39e1-130">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="f39e1-130">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f39e1-131">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="f39e1-131">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="f39e1-132">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagens que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="f39e1-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="f39e1-133">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="f39e1-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="f39e1-134">O Gerenciador de buffer minimiza o custo do uso de buffers usando um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="f39e1-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="f39e1-135">Os buffers são necessários para processar mensagens pelo serviço quando elas saem do canal.</span><span class="sxs-lookup"><span data-stu-id="f39e1-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="f39e1-136">Se não houver memória suficiente no pool de buffers para processar a carga de mensagens, o Gerenciador de buffer deverá alocar memória adicional do heap do CLR, o que aumenta a sobrecarga da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f39e1-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="f39e1-137">A alocação extensiva do heap de lixo do CLR é uma indicação de que o tamanho do pool de buffers é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="f39e1-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="f39e1-138">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto elas são processadas para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="f39e1-139">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="f39e1-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="f39e1-140">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, para uma mensagem que pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f39e1-141">O remetente receberá uma falha de SOAP se a mensagem for muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="f39e1-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="f39e1-142">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f39e1-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f39e1-143">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="f39e1-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="f39e1-144">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="f39e1-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="f39e1-145">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f39e1-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f39e1-146">Texto Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="f39e1-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="f39e1-147">MTOM Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).</span><span class="sxs-lookup"><span data-stu-id="f39e1-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="f39e1-148">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="f39e1-148">The default is Text.</span></span> <span data-ttu-id="f39e1-149">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="f39e1-150">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f39e1-151">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f39e1-152">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="f39e1-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f39e1-153">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="f39e1-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f39e1-154">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f39e1-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f39e1-155">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f39e1-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="f39e1-156">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="f39e1-157">O valor padrão é "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="f39e1-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="f39e1-158">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="f39e1-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="f39e1-159">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="f39e1-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f39e1-160">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f39e1-161">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f39e1-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="f39e1-162">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="f39e1-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="f39e1-163">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="f39e1-164">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f39e1-165">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="f39e1-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f39e1-166">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f39e1-167">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f39e1-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f39e1-168">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="f39e1-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f39e1-169">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f39e1-170">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f39e1-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="f39e1-171">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f39e1-172">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f39e1-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f39e1-173">BigEndianUnicode Codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="f39e1-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="f39e1-174">Unicode codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="f39e1-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="f39e1-175">UTF8 codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="f39e1-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="f39e1-176">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="f39e1-176">The default is UTF8.</span></span> <span data-ttu-id="f39e1-177">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="f39e1-178">Um valor <xref:System.ServiceModel.TransferMode> válido que especifica se as mensagens são armazenadas em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="f39e1-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="f39e1-179">Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="f39e1-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="f39e1-180">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f39e1-181">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f39e1-181">Child Elements</span></span>  
  
|<span data-ttu-id="f39e1-182">Elemento</span><span class="sxs-lookup"><span data-stu-id="f39e1-182">Element</span></span>|<span data-ttu-id="f39e1-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="f39e1-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f39e1-184">\<security></span><span class="sxs-lookup"><span data-stu-id="f39e1-184">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="f39e1-185">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="f39e1-186">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="f39e1-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f39e1-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="f39e1-188">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f39e1-189">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f39e1-190">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f39e1-190">Parent Elements</span></span>  
  
|<span data-ttu-id="f39e1-191">Elemento</span><span class="sxs-lookup"><span data-stu-id="f39e1-191">Element</span></span>|<span data-ttu-id="f39e1-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="f39e1-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f39e1-193">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f39e1-193">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f39e1-194">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="f39e1-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f39e1-195">Comentários</span><span class="sxs-lookup"><span data-stu-id="f39e1-195">Remarks</span></span>  
 <span data-ttu-id="f39e1-196">O BasicHttpBinding usa HTTP como o transporte para enviar mensagens SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="f39e1-196">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="f39e1-197">Um serviço pode usar essa associação para expor pontos de extremidade que estão em conformidade com WS-I BP 1,1, como aqueles que os clientes ASMX consomem.</span><span class="sxs-lookup"><span data-stu-id="f39e1-197">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="f39e1-198">Da mesma forma, um cliente pode usar o BasicHttpBinding para se comunicar com os serviços expondo pontos de extremidade que estão em conformidade com WS-I BP 1,1, como serviços Web ASMX ou serviços configurados com o BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="f39e1-198">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="f39e1-199">A segurança é desativada por padrão, mas pode ser adicionada, definindo o atributo mode do `None` [ \<elemento filho Security >](security-of-basichttpbinding.md) como um valor diferente de.</span><span class="sxs-lookup"><span data-stu-id="f39e1-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="f39e1-200">Ele usa uma codificação de mensagem "texto" e codificação de texto UTF-8 por padrão.</span><span class="sxs-lookup"><span data-stu-id="f39e1-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f39e1-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f39e1-201">Example</span></span>  
 <span data-ttu-id="f39e1-202">O exemplo a seguir demonstra o uso <xref:System.ServiceModel.BasicHttpBinding> do que fornece comunicação http e a interoperabilidade máxima com serviços da Web de primeira e segunda geração.</span><span class="sxs-lookup"><span data-stu-id="f39e1-202">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="f39e1-203">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="f39e1-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="f39e1-204">O tipo de associação é especificado usando `binding` o atributo `<endpoint>` do elemento.</span><span class="sxs-lookup"><span data-stu-id="f39e1-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="f39e1-205">Se você quiser configurar a ligação básica e alterar algumas de suas configurações, será necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="f39e1-206">O ponto de extremidade deve referenciar a configuração de associação por `bindingConfiguration` nome usando o `<endpoint>` atributo do elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f39e1-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="f39e1-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f39e1-207">Example</span></span>  
 <span data-ttu-id="f39e1-208">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f39e1-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f39e1-209">A funcionalidade do exemplo anterior pode ser realizada removendo o bindingConfiguration do endereço do ponto de extremidade e o nome da associação.</span><span class="sxs-lookup"><span data-stu-id="f39e1-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="f39e1-210">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f39e1-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39e1-211">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f39e1-211">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="f39e1-212">Associações</span><span class="sxs-lookup"><span data-stu-id="f39e1-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f39e1-213">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f39e1-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f39e1-214">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f39e1-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f39e1-215">\<binding></span><span class="sxs-lookup"><span data-stu-id="f39e1-215">\<binding></span></span>](../../../misc/binding.md)
