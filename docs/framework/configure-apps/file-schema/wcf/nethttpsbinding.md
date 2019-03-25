---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 06ef1be62865a5710dcb112caa744fa2cb5c0ea4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409530"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="1c1e0-101">\<netHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="1c1e0-101">\<netHttpsBinding></span></span>
<span data-ttu-id="1c1e0-102">Representa uma associação que um serviço do Windows Communication Foundation (WCF) pode usar para configurar e expor pontos de extremidade que podem se comunicar por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="1c1e0-103">Quando usado com um contrato duplex, soquetes da Web será usado, caso contrário, o HTTPS será usado.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="1c1e0-104">Elemento raiz</span><span class="sxs-lookup"><span data-stu-id="1c1e0-104">Root Element</span></span>  
<span data-ttu-id="1c1e0-105">Próximo elemento</span><span class="sxs-lookup"><span data-stu-id="1c1e0-105">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1e0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c1e0-106">Syntax</span></span>  
  
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
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="1c1e0-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="1c1e0-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c1e0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1c1e0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1c1e0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c1e0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1c1e0-110">Attributes</span></span>  
  
|<span data-ttu-id="1c1e0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="1c1e0-111">Attribute</span></span>|<span data-ttu-id="1c1e0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c1e0-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="1c1e0-113">Um valor booliano que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="1c1e0-114">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1c1e0-115">Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="1c1e0-116">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações futuras de cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="1c1e0-117">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="1c1e0-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1c1e0-119">Um recurso da Internet é local se ele tiver um endereço local.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="1c1e0-120">Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="1c1e0-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="1c1e0-121">Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="1c1e0-122">Se esse atributo for `true`, as solicitações para recursos locais da Internet não usam o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="1c1e0-123">Use o nome de host (em vez do localhost) se desejar que os clientes para passar por um proxy ao conversar com os serviços no mesmo computador, quando esse atributo é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="1c1e0-124">Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="1c1e0-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1c1e0-126">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1c1e0-127">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="1c1e0-128">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1c1e0-129">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1c1e0-130">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="1c1e0-131">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="1c1e0-132">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="1c1e0-133">O Gerenciador de Buffer minimiza o custo do uso de buffers por meio de um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="1c1e0-134">Buffers são necessários para processar as mensagens pelo serviço quando eles saírem do canal.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="1c1e0-135">Se não houver memória suficiente no pool de buffers para processar a carga de mensagem, o Gerenciador de Buffer deve alocar mais memória do heap CLR, o que aumenta a sobrecarga de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="1c1e0-136">Ampla alocação do heap de lixo do CLR é uma indicação de que o tamanho do pool de buffers é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="1c1e0-137">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena as mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="1c1e0-138">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="1c1e0-139">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos de mensagem pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1c1e0-140">O remetente recebe uma falha de SOAP, se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="1c1e0-141">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1c1e0-142">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="1c1e0-143">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="1c1e0-144">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1c1e0-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c1e0-145">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="1c1e0-146">-Mtom: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="1c1e0-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="1c1e0-147">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-147">The default is Text.</span></span> <span data-ttu-id="1c1e0-148">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="1c1e0-149">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1c1e0-150">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1c1e0-151">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-151">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="1c1e0-152">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-152">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="1c1e0-153">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1c1e0-154">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1c1e0-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="1c1e0-155">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-155">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="1c1e0-156">O valor padrão é "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="1c1e0-156">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="1c1e0-157">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-157">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="1c1e0-158">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1c1e0-159">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1c1e0-160">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-160">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="1c1e0-161">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-161">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="1c1e0-162">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-162">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="1c1e0-163">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-163">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1c1e0-164">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1c1e0-165">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1c1e0-166">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-166">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1c1e0-167">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1c1e0-168">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1c1e0-169">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-169">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="1c1e0-170">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="1c1e0-171">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1c1e0-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c1e0-172">-   BigEndianUnicode: Unicode BigEndian de codificação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="1c1e0-173">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="1c1e0-174">-   UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="1c1e0-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="1c1e0-175">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-175">The default is UTF8.</span></span> <span data-ttu-id="1c1e0-176">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="1c1e0-177">Válido <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-177">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="1c1e0-178">Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-178">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="1c1e0-179">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-179">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="1c1e0-180">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1c1e0-180">Child Elements</span></span>  
  
|<span data-ttu-id="1c1e0-181">Elemento</span><span class="sxs-lookup"><span data-stu-id="1c1e0-181">Element</span></span>|<span data-ttu-id="1c1e0-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c1e0-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c1e0-183">\<security></span><span class="sxs-lookup"><span data-stu-id="1c1e0-183">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="1c1e0-184">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="1c1e0-185">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-185">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="1c1e0-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c1e0-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="1c1e0-187">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-187">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1c1e0-188">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-188">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c1e0-189">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1c1e0-189">Parent Elements</span></span>  
  
|<span data-ttu-id="1c1e0-190">Elemento</span><span class="sxs-lookup"><span data-stu-id="1c1e0-190">Element</span></span>|<span data-ttu-id="1c1e0-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c1e0-191">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c1e0-192">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1c1e0-192">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="1c1e0-193">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-193">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c1e0-194">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c1e0-194">Remarks</span></span>  
 <span data-ttu-id="1c1e0-195">O NetHttpsBinding usa HTTPS como o transporte para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-195">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="1c1e0-196">Quando usado com um contrato duplex, soquetes da Web será usado.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-196">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="1c1e0-197">Quando usado com um contrato de solicitação-resposta que nethttpsbinding irá se comportar como um BasicHttpsBinding com um codificador binário.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-197">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="1c1e0-198">Segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho a um valor diferente de `None`.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-198">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="1c1e0-199">Ele usa um "Text" mensagem codificação e UTF-8 codificação de texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-199">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c1e0-200">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c1e0-200">Example</span></span>  
 <span data-ttu-id="1c1e0-201">O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.NetHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTPS com o primeiro – e second - generation serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-201">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="1c1e0-202">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-202">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="1c1e0-203">O tipo de associação é especificado usando o `binding` atributo do `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-203">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="1c1e0-204">Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-204">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="1c1e0-205">O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo do `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-205">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1c1e0-206">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c1e0-206">Example</span></span>  
 <span data-ttu-id="1c1e0-207">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-207">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1c1e0-208">A funcionalidade do exemplo anterior pode ser feita, removendo o bindingConfiguration do endereço do ponto de extremidade e o nome da associação.</span><span class="sxs-lookup"><span data-stu-id="1c1e0-208">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
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
  
 <span data-ttu-id="1c1e0-209">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1c1e0-209">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1e0-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c1e0-210">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="1c1e0-211">Associações</span><span class="sxs-lookup"><span data-stu-id="1c1e0-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1c1e0-212">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="1c1e0-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1c1e0-213">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1c1e0-213">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1c1e0-214">\<binding></span><span class="sxs-lookup"><span data-stu-id="1c1e0-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
