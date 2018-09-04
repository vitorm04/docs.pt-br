---
title: '&lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: 31db3e8e8e441c8496c5e711702111394755a90b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523402"
---
# <a name="ltnethttpbindinggt"></a><span data-ttu-id="349b0-102">&lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="349b0-102">&lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="349b0-103">Representa uma associação que um serviço do Windows Communication Foundation (WCF) pode usar para configurar e expor pontos de extremidade que podem se comunicar por HTTP.</span><span class="sxs-lookup"><span data-stu-id="349b0-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="349b0-104">Quando usado com um contrato duplex, soquetes da Web será usado, caso contrário, o HTTP será usado.</span><span class="sxs-lookup"><span data-stu-id="349b0-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
 <span data-ttu-id="349b0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="349b0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="349b0-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="349b0-106">\<bindings></span></span>  
<span data-ttu-id="349b0-107">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="349b0-107">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="349b0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="349b0-108">Syntax</span></span>  

```xml  
<netHttpBinding>  
   <binding   
       allowCookies="Boolean"  
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
</netHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="349b0-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="349b0-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="349b0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="349b0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="349b0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="349b0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="349b0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="349b0-112">Attributes</span></span>  
  
|<span data-ttu-id="349b0-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="349b0-113">Attribute</span></span>|<span data-ttu-id="349b0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="349b0-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="349b0-115">Um valor booliano que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="349b0-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="349b0-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="349b0-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="349b0-117">Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="349b0-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="349b0-118">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações futuras de cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="349b0-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="349b0-119">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="349b0-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="349b0-120">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="349b0-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="349b0-121">Um recurso da Internet é local se ele tiver um endereço local.</span><span class="sxs-lookup"><span data-stu-id="349b0-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="349b0-122">Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="349b0-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="349b0-123">Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="349b0-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="349b0-124">Se esse atributo for `true`, as solicitações para recursos locais da Internet não usam o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="349b0-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="349b0-125">Use o nome de host (em vez do localhost) se desejar que os clientes para passar por um proxy ao conversar com os serviços no mesmo computador, quando esse atributo é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="349b0-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="349b0-126">Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="349b0-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="349b0-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="349b0-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="349b0-128">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="349b0-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="349b0-129">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="349b0-129">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="349b0-130">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="349b0-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="349b0-131">Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="349b0-131">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="349b0-132">O valor padrão é `StrongWildcard`>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="349b0-132">The default value is `StrongWildcard`>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="349b0-133">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="349b0-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="349b0-134">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="349b0-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="349b0-135">O Gerenciador de Buffer minimiza o custo do uso de buffers por meio de um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="349b0-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="349b0-136">Buffers são necessários para processar as mensagens pelo serviço quando eles saírem do canal.</span><span class="sxs-lookup"><span data-stu-id="349b0-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="349b0-137">Se não houver memória suficiente no pool de buffers para processar a carga de mensagem, o Gerenciador de Buffer deve alocar mais memória do heap CLR, o que aumenta a sobrecarga de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="349b0-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="349b0-138">Ampla alocação do heap de lixo do CLR é uma indicação de que o tamanho do pool de buffers é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="349b0-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="349b0-139">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena as mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="349b0-140">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="349b0-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="349b0-141">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos de mensagem pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="349b0-142">O remetente recebe uma falha de SOAP, se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="349b0-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="349b0-143">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="349b0-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="349b0-144">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="349b0-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="349b0-145">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="349b0-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="349b0-146">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="349b0-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="349b0-147">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="349b0-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="349b0-148">-Mtom: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="349b0-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="349b0-149">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="349b0-149">The default is Text.</span></span> <span data-ttu-id="349b0-150">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="349b0-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="349b0-151">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="349b0-152">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="349b0-153">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="349b0-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="349b0-154">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="349b0-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="349b0-155">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="349b0-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="349b0-156">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="349b0-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="349b0-157">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="349b0-158">O valor padrão é " http://tempuri.org/Bindings ".</span><span class="sxs-lookup"><span data-stu-id="349b0-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="349b0-159">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="349b0-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="349b0-160">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="349b0-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="349b0-161">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="349b0-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="349b0-162">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="349b0-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="349b0-163">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="349b0-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="349b0-164">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="349b0-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="349b0-165">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="349b0-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="349b0-166">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="349b0-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="349b0-167">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="349b0-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="349b0-168">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="349b0-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="349b0-169">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="349b0-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="349b0-170">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="349b0-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="349b0-171">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="349b0-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="349b0-172">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="349b0-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="349b0-173">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="349b0-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="349b0-174">-BigEndianUnicode: O Unicode BigEndian de codificação.</span><span class="sxs-lookup"><span data-stu-id="349b0-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="349b0-175">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="349b0-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="349b0-176">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="349b0-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="349b0-177">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="349b0-177">The default is UTF8.</span></span> <span data-ttu-id="349b0-178">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="349b0-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="349b0-179">Válido <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="349b0-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="349b0-180">Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="349b0-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="349b0-181">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="349b0-181">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="349b0-182">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="349b0-182">Child Elements</span></span>  
  
|<span data-ttu-id="349b0-183">Elemento</span><span class="sxs-lookup"><span data-stu-id="349b0-183">Element</span></span>|<span data-ttu-id="349b0-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="349b0-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="349b0-185">\<security></span><span class="sxs-lookup"><span data-stu-id="349b0-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="349b0-186">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="349b0-187">Esse elemento é do tipo `NetHttpSecurityElement`.</span><span class="sxs-lookup"><span data-stu-id="349b0-187">This element is of type `NetHttpSecurityElement`.</span></span>|  
|[<span data-ttu-id="349b0-188">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="349b0-188">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="349b0-189">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="349b0-190">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="349b0-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="349b0-191">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="349b0-191">Parent Elements</span></span>  
  
|<span data-ttu-id="349b0-192">Elemento</span><span class="sxs-lookup"><span data-stu-id="349b0-192">Element</span></span>|<span data-ttu-id="349b0-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="349b0-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="349b0-194">\<associações ></span><span class="sxs-lookup"><span data-stu-id="349b0-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="349b0-195">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="349b0-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="349b0-196">Comentários</span><span class="sxs-lookup"><span data-stu-id="349b0-196">Remarks</span></span>  
 <span data-ttu-id="349b0-197">O NetHttpBinding usa HTTP como o transporte para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="349b0-197">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="349b0-198">Quando usado com um contrato duplex, soquetes da Web será usado.</span><span class="sxs-lookup"><span data-stu-id="349b0-198">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="349b0-199">Quando usado com um contrato de solicitação-resposta que NetHttpBinding irá se comportar como um BasicHttpBinding com um codificador binário.</span><span class="sxs-lookup"><span data-stu-id="349b0-199">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="349b0-200">Segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho a um valor diferente de `None`.</span><span class="sxs-lookup"><span data-stu-id="349b0-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="349b0-201">Ele usa um "Text" mensagem codificação e UTF-8 codificação de texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="349b0-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="349b0-202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="349b0-202">Example</span></span>  
 <span data-ttu-id="349b0-203">O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.NetHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTP com o primeiro – e second - generation serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="349b0-203">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="349b0-204">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="349b0-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="349b0-205">O tipo de associação é especificado usando o `binding` atributo do `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="349b0-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="349b0-206">Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="349b0-207">O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo do `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="349b0-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="349b0-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="349b0-208">Example</span></span>  
 <span data-ttu-id="349b0-209">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="349b0-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="349b0-210">A funcionalidade do exemplo anterior pode ser feita, removendo o bindingConfiguration do endereço do ponto de extremidade e o nome frm a associação.</span><span class="sxs-lookup"><span data-stu-id="349b0-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
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
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="349b0-211">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="349b0-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349b0-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="349b0-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="349b0-213">Associações</span><span class="sxs-lookup"><span data-stu-id="349b0-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="349b0-214">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="349b0-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="349b0-215">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="349b0-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="349b0-216">\<associação ></span><span class="sxs-lookup"><span data-stu-id="349b0-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
