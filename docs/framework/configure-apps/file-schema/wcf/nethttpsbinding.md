---
title: '&lt;netHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 315420a6561d68ff714cefedf5161892342b3ff1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="469d7-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="469d7-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="469d7-103">Representa uma associação que um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço pode usar para configurar e expor pontos de extremidade que podem se comunicar por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="469d7-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="469d7-104">Quando usado com um contrato duplex, soquetes da Web será usado, caso contrário, o HTTPS será usado.</span><span class="sxs-lookup"><span data-stu-id="469d7-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="469d7-105">Elemento raiz</span><span class="sxs-lookup"><span data-stu-id="469d7-105">Root Element</span></span>  
<span data-ttu-id="469d7-106">Próximo elemento</span><span class="sxs-lookup"><span data-stu-id="469d7-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="469d7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="469d7-107">Syntax</span></span>  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan"   
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
           maxBufferPoolSize="Integer"  
           maxBufferSize="Integer"  
           maxReceivedMessageSize="Integer"  
           messageEncoding="Binary/Text/Mtom"  
           name="string"   
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
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="469d7-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="469d7-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="469d7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="469d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="469d7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="469d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="469d7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="469d7-111">Attributes</span></span>  
  
|<span data-ttu-id="469d7-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="469d7-112">Attribute</span></span>|<span data-ttu-id="469d7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="469d7-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="469d7-114">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="469d7-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="469d7-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="469d7-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="469d7-116">Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="469d7-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="469d7-117">Dessa forma, você poderá ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras desse serviço.</span><span class="sxs-lookup"><span data-stu-id="469d7-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="469d7-118">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="469d7-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="469d7-119">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="469d7-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="469d7-120">Um recurso de Internet é local se ele tem um endereço local.</span><span class="sxs-lookup"><span data-stu-id="469d7-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="469d7-121">Um endereço local é aquele que está no mesmo computador, a rede local ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como no URIs "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="469d7-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="469d7-122">Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="469d7-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="469d7-123">Se esse atributo for `true`, solicitações aos recursos da Internet locais não usar o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="469d7-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="469d7-124">Use o nome do host (em vez de localhost) se desejar que os clientes para passar por um proxy ao conversar com serviços no mesmo computador, quando esse atributo é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="469d7-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="469d7-125">Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="469d7-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="469d7-126">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="469d7-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="469d7-127">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="469d7-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="469d7-128">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="469d7-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="469d7-129">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="469d7-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="469d7-130">Esse atributo é do tipo `HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="469d7-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="469d7-131">O valor padrão é `StrongWildcard`, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="469d7-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="469d7-132">Um valor inteiro que especifica a quantidade máxima de memória que é alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="469d7-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="469d7-133">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="469d7-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="469d7-134">O Gerenciador de Buffer minimiza o custo do uso de buffers usando um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="469d7-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="469d7-135">Buffers são necessários para processar mensagens pelo serviço quando estiverem fora do canal.</span><span class="sxs-lookup"><span data-stu-id="469d7-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="469d7-136">Se não houver memória suficiente no pool de buffers para processar a carga da mensagem, o Gerenciador de Buffer deve alocar mais memória do heap CLR, o que aumenta a sobrecarga de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="469d7-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="469d7-137">Ampla alocação do heap de lixo CLR é uma indicação de que o tamanho do pool de buffer é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="469d7-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="469d7-138">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="469d7-139">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="469d7-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="469d7-140">Um inteiro positivo que define o tamanho máximo, em bytes, incluindo os cabeçalhos de uma mensagem que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="469d7-141">O remetente recebe uma falha de SOAP se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="469d7-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="469d7-142">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="469d7-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="469d7-143">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="469d7-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="469d7-144">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="469d7-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="469d7-145">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="469d7-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="469d7-146">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="469d7-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="469d7-147">-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="469d7-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="469d7-148">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="469d7-148">The default is Text.</span></span> <span data-ttu-id="469d7-149">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="469d7-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="469d7-150">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="469d7-151">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="469d7-152">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="469d7-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="469d7-153">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="469d7-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="469d7-154">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="469d7-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="469d7-155">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="469d7-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="469d7-156">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="469d7-157">O valor padrão é "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="469d7-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="469d7-158">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="469d7-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="469d7-159">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="469d7-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="469d7-160">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="469d7-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="469d7-161">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="469d7-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="469d7-162">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="469d7-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="469d7-163">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="469d7-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="469d7-164">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="469d7-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="469d7-165">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="469d7-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="469d7-166">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="469d7-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="469d7-167">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="469d7-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="469d7-168">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="469d7-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="469d7-169">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="469d7-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="469d7-170">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="469d7-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="469d7-171">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="469d7-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="469d7-172">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="469d7-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="469d7-173">-BigEndianUnicode: O Unicode BigEndian codificação.</span><span class="sxs-lookup"><span data-stu-id="469d7-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="469d7-174">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="469d7-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="469d7-175">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="469d7-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="469d7-176">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="469d7-176">The default is UTF8.</span></span> <span data-ttu-id="469d7-177">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="469d7-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="469d7-178">Uma opção válida <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenados em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="469d7-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="469d7-179">Um valor booleano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="469d7-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="469d7-180">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="469d7-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="469d7-181">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="469d7-181">Child Elements</span></span>  
  
|<span data-ttu-id="469d7-182">Elemento</span><span class="sxs-lookup"><span data-stu-id="469d7-182">Element</span></span>|<span data-ttu-id="469d7-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="469d7-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="469d7-184">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="469d7-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="469d7-185">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="469d7-186">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="469d7-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="469d7-187">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="469d7-187">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="469d7-188">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="469d7-189">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="469d7-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="469d7-190">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="469d7-190">Parent Elements</span></span>  
  
|<span data-ttu-id="469d7-191">Elemento</span><span class="sxs-lookup"><span data-stu-id="469d7-191">Element</span></span>|<span data-ttu-id="469d7-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="469d7-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="469d7-193">\<associações ></span><span class="sxs-lookup"><span data-stu-id="469d7-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="469d7-194">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="469d7-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="469d7-195">Comentários</span><span class="sxs-lookup"><span data-stu-id="469d7-195">Remarks</span></span>  
 <span data-ttu-id="469d7-196">O NetHttpsBinding usa HTTPS como o transporte para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="469d7-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="469d7-197">Quando usado com um contrato duplex, soquetes da Web será usado.</span><span class="sxs-lookup"><span data-stu-id="469d7-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="469d7-198">Quando usado com um contrato de solicitação-resposta que nethttpsbinding irão se comportar como um BasicHttpsBinding com um codificador binário.</span><span class="sxs-lookup"><span data-stu-id="469d7-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="469d7-199">A segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho com um valor diferente de `None`.</span><span class="sxs-lookup"><span data-stu-id="469d7-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="469d7-200">Ele usa um "Texto" mensagem codificação e UTF-8 codificação de texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="469d7-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="469d7-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="469d7-201">Example</span></span>  
 <span data-ttu-id="469d7-202">O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.NetHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTPS com primeiro - e second - generation serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="469d7-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="469d7-203">A associação é especificada nos arquivos de configuração do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="469d7-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="469d7-204">O tipo de associação é especificado usando o `binding` atributo o `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="469d7-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="469d7-205">Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="469d7-206">O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo o `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="469d7-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
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
               messageEncoding="Binary" 
               textEncoding="utf-8" 
               bypassProxyOnLocal="false" 
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="469d7-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="469d7-207">Example</span></span>  
 <span data-ttu-id="469d7-208">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="469d7-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="469d7-209">A funcionalidade do exemplo anterior pode ser feita, removendo o bindingConfiguration do endereço do ponto de extremidade e o gerenciamento de registros agrupados nome a associação.</span><span class="sxs-lookup"><span data-stu-id="469d7-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
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
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="469d7-210">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="469d7-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469d7-211">Consulte também</span><span class="sxs-lookup"><span data-stu-id="469d7-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="469d7-212">Associações</span><span class="sxs-lookup"><span data-stu-id="469d7-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="469d7-213">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="469d7-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="469d7-214">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="469d7-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="469d7-215">\<associação ></span><span class="sxs-lookup"><span data-stu-id="469d7-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
