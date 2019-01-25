---
title: '&lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 7d74ca7f4c44eafedaa95661797cce983967e846
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631734"
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="31a16-102">&lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="31a16-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="31a16-103">Representa uma associação que um serviço do WCF (Windows Communication Foundation) pode usar para configurar e expor pontos de extremidade capazes de se comunicar com clientes e serviços Web baseados em ASMX e outros serviços que estejam em conformidade com o WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="31a16-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="31a16-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="31a16-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="31a16-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="31a16-105">\<bindings></span></span>  
<span data-ttu-id="31a16-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="31a16-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31a16-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31a16-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31a16-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="31a16-108">Attributes and Elements</span></span>  
 <span data-ttu-id="31a16-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="31a16-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31a16-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="31a16-110">Attributes</span></span>  
  
|<span data-ttu-id="31a16-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="31a16-111">Attribute</span></span>|<span data-ttu-id="31a16-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="31a16-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="31a16-113">Um valor booliano que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="31a16-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="31a16-114">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="31a16-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="31a16-115">Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="31a16-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="31a16-116">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações futuras de cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="31a16-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="31a16-117">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="31a16-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="31a16-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="31a16-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="31a16-119">Um recurso da Internet é local se ele tiver um endereço local.</span><span class="sxs-lookup"><span data-stu-id="31a16-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="31a16-120">Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="31a16-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="31a16-121">Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="31a16-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="31a16-122">Se esse atributo for `true`, as solicitações para recursos locais da Internet não usam o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="31a16-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="31a16-123">Use o nome de host (em vez do localhost) se desejar que os clientes para passar por um proxy ao conversar com os serviços no mesmo computador, quando esse atributo é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="31a16-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="31a16-124">Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="31a16-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="31a16-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="31a16-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="31a16-126">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="31a16-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31a16-127">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="31a16-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="31a16-128">Especifica a versão do SOAP usada para as mensagens processadas por essa associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="31a16-129">O único valor válido é Soap11.</span><span class="sxs-lookup"><span data-stu-id="31a16-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="31a16-130">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="31a16-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="31a16-131">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="31a16-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="31a16-132">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="31a16-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="31a16-133">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="31a16-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="31a16-134">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="31a16-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="31a16-135">O Gerenciador de Buffer minimiza o custo do uso de buffers por meio de um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="31a16-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="31a16-136">Buffers são necessários para processar as mensagens pelo serviço quando eles saírem do canal.</span><span class="sxs-lookup"><span data-stu-id="31a16-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="31a16-137">Se não houver memória suficiente no pool de buffers para processar a carga de mensagem, o Gerenciador de Buffer deve alocar mais memória do heap CLR, o que aumenta a sobrecarga de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="31a16-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="31a16-138">Ampla alocação do heap de lixo do CLR é uma indicação de que o tamanho do pool de buffers é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="31a16-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="31a16-139">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena as mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="31a16-140">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="31a16-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="31a16-141">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos de mensagem pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="31a16-142">O remetente recebe uma falha de SOAP, se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="31a16-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="31a16-143">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="31a16-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="31a16-144">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="31a16-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="31a16-145">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="31a16-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="31a16-146">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="31a16-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="31a16-147">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="31a16-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="31a16-148">-Mtom: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="31a16-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="31a16-149">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="31a16-149">The default is Text.</span></span> <span data-ttu-id="31a16-150">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="31a16-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="31a16-151">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="31a16-152">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="31a16-153">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="31a16-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="31a16-154">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="31a16-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="31a16-155">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="31a16-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="31a16-156">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="31a16-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="31a16-157">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="31a16-158">O valor padrão é "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="31a16-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="31a16-159">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="31a16-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="31a16-160">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="31a16-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="31a16-161">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="31a16-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31a16-162">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="31a16-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="31a16-163">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="31a16-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="31a16-164">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="31a16-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="31a16-165">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="31a16-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="31a16-166">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="31a16-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="31a16-167">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="31a16-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31a16-168">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="31a16-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="31a16-169">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="31a16-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="31a16-170">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="31a16-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31a16-171">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="31a16-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="31a16-172">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="31a16-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="31a16-173">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="31a16-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="31a16-174">-   BigEndianUnicode: Unicode BigEndian de codificação.</span><span class="sxs-lookup"><span data-stu-id="31a16-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="31a16-175">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="31a16-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="31a16-176">-   UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="31a16-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="31a16-177">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="31a16-177">The default is UTF8.</span></span> <span data-ttu-id="31a16-178">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="31a16-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="31a16-179">Válido <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="31a16-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="31a16-180">Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="31a16-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="31a16-181">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="31a16-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31a16-182">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="31a16-182">Child Elements</span></span>  
  
|<span data-ttu-id="31a16-183">Elemento</span><span class="sxs-lookup"><span data-stu-id="31a16-183">Element</span></span>|<span data-ttu-id="31a16-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="31a16-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31a16-185">\<security></span><span class="sxs-lookup"><span data-stu-id="31a16-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="31a16-186">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="31a16-187">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="31a16-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="31a16-188">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="31a16-188">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="31a16-189">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="31a16-190">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="31a16-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31a16-191">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="31a16-191">Parent Elements</span></span>  
  
|<span data-ttu-id="31a16-192">Elemento</span><span class="sxs-lookup"><span data-stu-id="31a16-192">Element</span></span>|<span data-ttu-id="31a16-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="31a16-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31a16-194">\<bindings></span><span class="sxs-lookup"><span data-stu-id="31a16-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="31a16-195">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="31a16-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31a16-196">Comentários</span><span class="sxs-lookup"><span data-stu-id="31a16-196">Remarks</span></span>  
 <span data-ttu-id="31a16-197">O BasicHttpBinding usa HTTP como o transporte para enviar mensagens de SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="31a16-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="31a16-198">Um serviço pode usar essa associação para expor pontos de extremidade que estão em conformidade com WS-I BP 1.1, como aqueles que os clientes do ASMX consumir.</span><span class="sxs-lookup"><span data-stu-id="31a16-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="31a16-199">Da mesma forma, um cliente pode usar o BasicHttpBinding para se comunicar com serviços de expor pontos de extremidade que estão em conformidade com WS-I BP 1.1, como serviços Web ASMX ou serviços configurados com o BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="31a16-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="31a16-200">Segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho a um valor diferente de `None`.</span><span class="sxs-lookup"><span data-stu-id="31a16-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="31a16-201">Ele usa um "Text" mensagem codificação e UTF-8 codificação de texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="31a16-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31a16-202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31a16-202">Example</span></span>  
 <span data-ttu-id="31a16-203">O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.BasicHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTP com o primeiro – e second - generation serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="31a16-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="31a16-204">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="31a16-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="31a16-205">O tipo de associação é especificado usando o `binding` atributo do `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="31a16-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="31a16-206">Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="31a16-207">O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo do `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="31a16-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="31a16-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31a16-208">Example</span></span>  
 <span data-ttu-id="31a16-209">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="31a16-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="31a16-210">A funcionalidade do exemplo anterior pode ser feita, removendo o bindingConfiguration do endereço do ponto de extremidade e o nome da associação.</span><span class="sxs-lookup"><span data-stu-id="31a16-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="31a16-211">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="31a16-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a16-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31a16-212">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="31a16-213">Associações</span><span class="sxs-lookup"><span data-stu-id="31a16-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="31a16-214">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="31a16-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="31a16-215">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="31a16-215">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="31a16-216">\<binding></span><span class="sxs-lookup"><span data-stu-id="31a16-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
