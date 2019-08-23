---
title: <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: ff589c502333851de4dcf23101bb14fac767d25d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933080"
---
# <a name="nethttpbinding"></a><span data-ttu-id="e9db8-101">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e9db8-101">\<netHttpBinding></span></span>
<span data-ttu-id="e9db8-102">Representa uma associação que um serviço Windows Communication Foundation (WCF) pode usar para configurar e expor pontos de extremidade que são capazes de se comunicar via HTTP.</span><span class="sxs-lookup"><span data-stu-id="e9db8-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="e9db8-103">Quando usado com um contrato duplex, os Web Sockets serão usados; caso contrário, HTTP será usado.</span><span class="sxs-lookup"><span data-stu-id="e9db8-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
 <span data-ttu-id="e9db8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e9db8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9db8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e9db8-105">\<bindings></span></span>  
<span data-ttu-id="e9db8-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e9db8-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9db8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9db8-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
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
</netHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="e9db8-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="e9db8-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9db8-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e9db8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9db8-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e9db8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9db8-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e9db8-111">Attributes</span></span>  
  
|<span data-ttu-id="e9db8-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e9db8-112">Attribute</span></span>|<span data-ttu-id="e9db8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9db8-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="e9db8-114">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="e9db8-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="e9db8-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e9db8-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e9db8-116">Você pode usar essa propriedade ao interagir com serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="e9db8-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="e9db8-117">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="e9db8-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="e9db8-118">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="e9db8-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e9db8-119">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e9db8-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e9db8-120">Um recurso da Internet será local se ele tiver um endereço local.</span><span class="sxs-lookup"><span data-stu-id="e9db8-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="e9db8-121">Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="e9db8-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="e9db8-122">Definir esse atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais.</span><span class="sxs-lookup"><span data-stu-id="e9db8-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="e9db8-123">Se esse atributo for `true`, as solicitações para os recursos locais da Internet não usarão o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="e9db8-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="e9db8-124">Use o nome do host (em vez de localhost) se desejar que os clientes passem por um proxy ao se comunicar com os serviços no mesmo computador quando esse `true`atributo for definido como.</span><span class="sxs-lookup"><span data-stu-id="e9db8-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="e9db8-125">Quando esse atributo é `false`, todas as solicitações da Internet são feitas por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="e9db8-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="e9db8-126">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="e9db8-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e9db8-127">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9db8-128">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e9db8-128">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="e9db8-129">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="e9db8-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="e9db8-130">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="e9db8-130">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e9db8-131">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="e9db8-131">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e9db8-132">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagens que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="e9db8-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="e9db8-133">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="e9db8-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="e9db8-134">O Gerenciador de buffer minimiza o custo do uso de buffers usando um pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="e9db8-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="e9db8-135">Os buffers são necessários para processar mensagens pelo serviço quando elas saem do canal.</span><span class="sxs-lookup"><span data-stu-id="e9db8-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="e9db8-136">Se não houver memória suficiente no pool de buffers para processar a carga de mensagens, o Gerenciador de buffer deverá alocar memória adicional do heap do CLR, o que aumenta a sobrecarga da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e9db8-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="e9db8-137">A alocação extensiva do heap de lixo do CLR é uma indicação de que o tamanho do pool de buffers é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="e9db8-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="e9db8-138">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto elas são processadas para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="e9db8-139">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="e9db8-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e9db8-140">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, para uma mensagem que pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e9db8-141">O remetente receberá uma falha de SOAP se a mensagem for muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="e9db8-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="e9db8-142">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e9db8-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e9db8-143">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="e9db8-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="e9db8-144">Define o codificador usado para codificar a mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="e9db8-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="e9db8-145">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e9db8-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e9db8-146">Texto Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="e9db8-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="e9db8-147">MTOM Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).</span><span class="sxs-lookup"><span data-stu-id="e9db8-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="e9db8-148">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="e9db8-148">The default is Text.</span></span> <span data-ttu-id="e9db8-149">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="e9db8-150">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e9db8-151">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e9db8-152">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="e9db8-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="e9db8-153">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="e9db8-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="e9db8-154">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9db8-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e9db8-155">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9db8-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="e9db8-156">Especifica o namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="e9db8-157">O valor padrão é "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="e9db8-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="e9db8-158">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="e9db8-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="e9db8-159">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="e9db8-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e9db8-160">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9db8-161">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e9db8-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="e9db8-162">Um URI que contém o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="e9db8-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="e9db8-163">Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e9db8-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="e9db8-164">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="e9db8-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e9db8-165">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="e9db8-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e9db8-166">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9db8-167">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e9db8-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e9db8-168">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="e9db8-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e9db8-169">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9db8-170">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e9db8-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="e9db8-171">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e9db8-172">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e9db8-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e9db8-173">BigEndianUnicode Codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="e9db8-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="e9db8-174">Unicode codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="e9db8-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="e9db8-175">UTF8 codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="e9db8-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="e9db8-176">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="e9db8-176">The default is UTF8.</span></span> <span data-ttu-id="e9db8-177">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="e9db8-178">Um valor <xref:System.ServiceModel.TransferMode> válido que especifica se as mensagens são armazenadas em buffer ou transmitidas em uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="e9db8-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="e9db8-179">Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível.</span><span class="sxs-lookup"><span data-stu-id="e9db8-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="e9db8-180">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="e9db8-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="e9db8-181">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e9db8-181">Child Elements</span></span>  
  
|<span data-ttu-id="e9db8-182">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9db8-182">Element</span></span>|<span data-ttu-id="e9db8-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9db8-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9db8-184">\<security></span><span class="sxs-lookup"><span data-stu-id="e9db8-184">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="e9db8-185">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="e9db8-186">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="e9db8-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9db8-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e9db8-188">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e9db8-189">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e9db8-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9db8-190">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e9db8-190">Parent Elements</span></span>  
  
|<span data-ttu-id="e9db8-191">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9db8-191">Element</span></span>|<span data-ttu-id="e9db8-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9db8-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9db8-193">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e9db8-193">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e9db8-194">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e9db8-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9db8-195">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9db8-195">Remarks</span></span>  
 <span data-ttu-id="e9db8-196">O NetHttpBinding usa HTTP como o transporte para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="e9db8-196">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="e9db8-197">Quando usado com um contrato duplex, os Web Sockets serão usados.</span><span class="sxs-lookup"><span data-stu-id="e9db8-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="e9db8-198">Quando usado com um contrato de solicitação-resposta, NetHttpBinding se comportará como um BasicHttpBinding com um codificador binário.</span><span class="sxs-lookup"><span data-stu-id="e9db8-198">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="e9db8-199">A segurança é desativada por padrão, mas pode ser adicionada, definindo o atributo mode do `None` [ \<elemento filho Security >](security-of-basichttpbinding.md) como um valor diferente de.</span><span class="sxs-lookup"><span data-stu-id="e9db8-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="e9db8-200">Ele usa uma codificação de mensagem "texto" e codificação de texto UTF-8 por padrão.</span><span class="sxs-lookup"><span data-stu-id="e9db8-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9db8-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9db8-201">Example</span></span>  
 <span data-ttu-id="e9db8-202">O exemplo a seguir demonstra o uso <xref:System.ServiceModel.NetHttpBinding> do que fornece comunicação http e a interoperabilidade máxima com serviços da Web de primeira e segunda geração.</span><span class="sxs-lookup"><span data-stu-id="e9db8-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="e9db8-203">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="e9db8-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="e9db8-204">O tipo de associação é especificado usando `binding` o atributo `<endpoint>` do elemento.</span><span class="sxs-lookup"><span data-stu-id="e9db8-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="e9db8-205">Se você quiser configurar a ligação básica e alterar algumas de suas configurações, será necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="e9db8-206">O ponto de extremidade deve referenciar a configuração de associação por `bindingConfiguration` nome usando o `<endpoint>` atributo do elemento, conforme mostrado no código de configuração a seguir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e9db8-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
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
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="e9db8-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9db8-207">Example</span></span>  
 <span data-ttu-id="e9db8-208">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9db8-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e9db8-209">A funcionalidade do exemplo anterior pode ser realizada removendo o bindingConfiguration do endereço do ponto de extremidade e o nome da associação.</span><span class="sxs-lookup"><span data-stu-id="e9db8-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
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
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="e9db8-210">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9db8-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9db8-211">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9db8-211">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="e9db8-212">Associações</span><span class="sxs-lookup"><span data-stu-id="e9db8-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9db8-213">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="e9db8-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9db8-214">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e9db8-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e9db8-215">\<binding></span><span class="sxs-lookup"><span data-stu-id="e9db8-215">\<binding></span></span>](../../../misc/binding.md)
