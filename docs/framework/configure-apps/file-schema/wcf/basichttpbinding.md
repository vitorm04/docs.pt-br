---
title: '&lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 75ac5acab14c053adb1b1bec164e52be57670839
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751695"
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="87e44-102">&lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="87e44-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="87e44-103">Representa uma associação que um serviço do WCF (Windows Communication Foundation) pode usar para configurar e expor pontos de extremidade capazes de se comunicar com clientes e serviços Web baseados em ASMX e outros serviços que estejam em conformidade com o WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="87e44-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="87e44-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87e44-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87e44-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="87e44-105">\<bindings></span></span>  
<span data-ttu-id="87e44-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="87e44-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e44-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87e44-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
              name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87e44-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87e44-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87e44-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87e44-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87e44-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="87e44-110">Attributes</span></span>  
  
|<span data-ttu-id="87e44-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="87e44-111">Attribute</span></span>|<span data-ttu-id="87e44-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="87e44-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="87e44-113">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="87e44-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="87e44-114">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="87e44-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="87e44-115">Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="87e44-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="87e44-116">Dessa forma, você poderá ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras desse serviço.</span><span class="sxs-lookup"><span data-stu-id="87e44-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="87e44-117">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="87e44-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="87e44-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="87e44-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="87e44-119">Um recurso de Internet é local se ele tem um endereço local.</span><span class="sxs-lookup"><span data-stu-id="87e44-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="87e44-120">Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/"e"http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="87e44-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="87e44-121">Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="87e44-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="87e44-122">Se esse atributo for `true`, solicitações aos recursos da Internet locais não usar o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="87e44-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="87e44-123">Use o nome do host (em vez de localhost) se desejar que os clientes para passar por um proxy ao conversar com serviços no mesmo computador, quando esse atributo é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="87e44-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="87e44-124">Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="87e44-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="87e44-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="87e44-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="87e44-126">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87e44-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87e44-127">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="87e44-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="87e44-128">Especifica a versão do SOAP que é usado para as mensagens processadas por essa associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="87e44-129">O único valor válido é Soap11.</span><span class="sxs-lookup"><span data-stu-id="87e44-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="87e44-130">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="87e44-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="87e44-131">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="87e44-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="87e44-132">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="87e44-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="87e44-133">Um valor inteiro que especifica a quantidade máxima de memória que é alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="87e44-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="87e44-134">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="87e44-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="87e44-135">O Gerenciador de Buffer minimiza o custo do uso de buffers usando um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="87e44-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="87e44-136">Buffers são necessários para processar mensagens pelo serviço quando estiverem fora do canal.</span><span class="sxs-lookup"><span data-stu-id="87e44-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="87e44-137">Se não houver memória suficiente no pool de buffers para processar a carga da mensagem, o Gerenciador de Buffer deve alocar mais memória do heap CLR, o que aumenta a sobrecarga de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="87e44-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="87e44-138">Ampla alocação do heap de lixo CLR é uma indicação de que o tamanho do pool de buffer é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="87e44-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="87e44-139">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="87e44-140">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="87e44-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="87e44-141">Um inteiro positivo que define o tamanho máximo, em bytes, incluindo os cabeçalhos de uma mensagem que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="87e44-142">O remetente recebe uma falha de SOAP se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="87e44-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="87e44-143">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="87e44-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="87e44-144">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="87e44-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="87e44-145">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="87e44-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="87e44-146">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="87e44-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="87e44-147">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="87e44-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="87e44-148">-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="87e44-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="87e44-149">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="87e44-149">The default is Text.</span></span> <span data-ttu-id="87e44-150">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="87e44-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="87e44-151">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="87e44-152">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="87e44-153">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="87e44-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="87e44-154">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="87e44-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="87e44-155">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="87e44-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="87e44-156">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="87e44-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="87e44-157">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="87e44-158">O valor padrão é "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="87e44-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="87e44-159">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="87e44-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="87e44-160">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="87e44-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="87e44-161">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87e44-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87e44-162">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="87e44-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="87e44-163">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="87e44-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="87e44-164">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="87e44-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="87e44-165">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="87e44-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="87e44-166">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="87e44-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="87e44-167">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87e44-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87e44-168">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="87e44-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="87e44-169">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="87e44-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="87e44-170">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87e44-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87e44-171">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="87e44-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="87e44-172">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="87e44-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="87e44-173">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="87e44-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="87e44-174">-BigEndianUnicode: O Unicode BigEndian codificação.</span><span class="sxs-lookup"><span data-stu-id="87e44-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="87e44-175">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="87e44-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="87e44-176">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="87e44-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="87e44-177">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="87e44-177">The default is UTF8.</span></span> <span data-ttu-id="87e44-178">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="87e44-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="87e44-179">Uma opção válida <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenados em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="87e44-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="87e44-180">Um valor booleano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="87e44-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="87e44-181">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="87e44-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87e44-182">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87e44-182">Child Elements</span></span>  
  
|<span data-ttu-id="87e44-183">Elemento</span><span class="sxs-lookup"><span data-stu-id="87e44-183">Element</span></span>|<span data-ttu-id="87e44-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="87e44-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87e44-185">\<security></span><span class="sxs-lookup"><span data-stu-id="87e44-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="87e44-186">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="87e44-187">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="87e44-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="87e44-188">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="87e44-188">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="87e44-189">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="87e44-190">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="87e44-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87e44-191">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87e44-191">Parent Elements</span></span>  
  
|<span data-ttu-id="87e44-192">Elemento</span><span class="sxs-lookup"><span data-stu-id="87e44-192">Element</span></span>|<span data-ttu-id="87e44-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="87e44-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87e44-194">\<associações ></span><span class="sxs-lookup"><span data-stu-id="87e44-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="87e44-195">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="87e44-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e44-196">Comentários</span><span class="sxs-lookup"><span data-stu-id="87e44-196">Remarks</span></span>  
 <span data-ttu-id="87e44-197">O BasicHttpBinding usa HTTP como o transporte para enviar mensagens de SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="87e44-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="87e44-198">Um serviço pode usar essa associação para expor pontos de extremidade que está de acordo com WS-I BP 1.1, como aqueles que clientes ASMX consumam.</span><span class="sxs-lookup"><span data-stu-id="87e44-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="87e44-199">Da mesma forma, um cliente pode usar o BasicHttpBinding para se comunicar com serviços expor pontos de extremidade que está de acordo com WS-I BP 1.1, como serviços Web ASMX ou serviços configurados com o BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="87e44-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="87e44-200">A segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho com um valor diferente de `None`.</span><span class="sxs-lookup"><span data-stu-id="87e44-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="87e44-201">Ele usa um "Texto" mensagem codificação e UTF-8 codificação de texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="87e44-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87e44-202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87e44-202">Example</span></span>  
 <span data-ttu-id="87e44-203">O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.BasicHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTP com o primeiro - e second - generation serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="87e44-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="87e44-204">A associação é especificada nos arquivos de configuração do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="87e44-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="87e44-205">O tipo de associação é especificado usando o `binding` atributo o `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="87e44-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="87e44-206">Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="87e44-207">O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo o `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="87e44-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="87e44-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87e44-208">Example</span></span>  
 <span data-ttu-id="87e44-209">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="87e44-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="87e44-210">A funcionalidade do exemplo anterior pode ser feita, removendo o bindingConfiguration do endereço do ponto de extremidade e o gerenciamento de registros agrupados nome a associação.</span><span class="sxs-lookup"><span data-stu-id="87e44-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
        <binding   
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="87e44-211">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="87e44-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e44-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87e44-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="87e44-213">Associações</span><span class="sxs-lookup"><span data-stu-id="87e44-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="87e44-214">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="87e44-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="87e44-215">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="87e44-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="87e44-216">\<associação ></span><span class="sxs-lookup"><span data-stu-id="87e44-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
