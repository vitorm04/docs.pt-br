---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 81f0101ce1dc2195cfc2f556e38a8551f674d13b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941517"
---
# <a name="wshttpbinding"></a><span data-ttu-id="5372b-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5372b-101">\<wsHttpBinding></span></span>
<span data-ttu-id="5372b-102">Define uma associação segura, confiável e interoperável adequada para contratos de serviço não duplex.</span><span class="sxs-lookup"><span data-stu-id="5372b-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="5372b-103">A associação implementa as seguintes especificações: Sistema de mensagens WS-Reliable para confiabilidade e WS-Security para segurança e autenticação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5372b-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="5372b-104">O transporte é HTTP e a codificação de mensagem é codificação de texto/XML.</span><span class="sxs-lookup"><span data-stu-id="5372b-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="5372b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5372b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5372b-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5372b-106">\<bindings></span></span>  
<span data-ttu-id="5372b-107">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5372b-107">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5372b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5372b-108">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5372b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5372b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5372b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="5372b-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5372b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5372b-111">Attributes</span></span>  
  
|<span data-ttu-id="5372b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="5372b-112">Attribute</span></span>|<span data-ttu-id="5372b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5372b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5372b-114">allowCookies</span><span class="sxs-lookup"><span data-stu-id="5372b-114">allowCookies</span></span>|<span data-ttu-id="5372b-115">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="5372b-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="5372b-116">O padrão é falso.</span><span class="sxs-lookup"><span data-stu-id="5372b-116">The default is false.</span></span><br /><br /> <span data-ttu-id="5372b-117">Você pode usar essa propriedade ao interagir com serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="5372b-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="5372b-118">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="5372b-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="5372b-119">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="5372b-119">bypassProxyOnLocal</span></span>|<span data-ttu-id="5372b-120">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="5372b-120">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="5372b-121">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5372b-121">The default is `false`.</span></span>|  
|<span data-ttu-id="5372b-122">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="5372b-122">closeTimeout</span></span>|<span data-ttu-id="5372b-123">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="5372b-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5372b-124">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5372b-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5372b-125">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5372b-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5372b-126">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="5372b-126">hostnameComparisonMode</span></span>|<span data-ttu-id="5372b-127">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="5372b-127">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="5372b-128">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="5372b-128">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="5372b-129">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="5372b-129">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="5372b-130">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5372b-130">maxBufferPoolSize</span></span>|<span data-ttu-id="5372b-131">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-131">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="5372b-132">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="5372b-132">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="5372b-133">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="5372b-133">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="5372b-134">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="5372b-134">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="5372b-135">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="5372b-135">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="5372b-136">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="5372b-136">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="5372b-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5372b-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="5372b-138">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5372b-139">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="5372b-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="5372b-140">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5372b-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5372b-141">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="5372b-141">The default is 65536.</span></span>|  
|<span data-ttu-id="5372b-142">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="5372b-142">messageEncoding</span></span>|<span data-ttu-id="5372b-143">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="5372b-143">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="5372b-144">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5372b-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5372b-145">Texto Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="5372b-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="5372b-146">MTOM Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).</span><span class="sxs-lookup"><span data-stu-id="5372b-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="5372b-147">-O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="5372b-147">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="5372b-148">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="5372b-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="5372b-149">name</span><span class="sxs-lookup"><span data-stu-id="5372b-149">name</span></span>|<span data-ttu-id="5372b-150">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5372b-151">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5372b-152">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5372b-152">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5372b-153">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5372b-153">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="5372b-154">openTimeout</span><span class="sxs-lookup"><span data-stu-id="5372b-154">openTimeout</span></span>|<span data-ttu-id="5372b-155">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="5372b-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5372b-156">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5372b-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5372b-157">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5372b-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5372b-158">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="5372b-158">proxyAddress</span></span>|<span data-ttu-id="5372b-159">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="5372b-159">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="5372b-160">Se `useSystemWebProxy` `null`for `true`, essa configuração deverá ser.</span><span class="sxs-lookup"><span data-stu-id="5372b-160">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="5372b-161">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="5372b-161">The default is `null`.</span></span>|  
|<span data-ttu-id="5372b-162">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5372b-162">receiveTimeout</span></span>|<span data-ttu-id="5372b-163">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="5372b-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5372b-164">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5372b-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5372b-165">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5372b-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5372b-166">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="5372b-166">sendTimeout</span></span>|<span data-ttu-id="5372b-167">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="5372b-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5372b-168">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5372b-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5372b-169">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5372b-169">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5372b-170">textEncoding</span><span class="sxs-lookup"><span data-stu-id="5372b-170">textEncoding</span></span>|<span data-ttu-id="5372b-171">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-171">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5372b-172">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5372b-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5372b-173">-   UnicodeFffeTextEncoding: Codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="5372b-173">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="5372b-174">- Utf16TextEncoding: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="5372b-174">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="5372b-175">- Utf8TextEncoding: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="5372b-175">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="5372b-176">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="5372b-176">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="5372b-177">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="5372b-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="5372b-178">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="5372b-178">transactionFlow</span></span>|<span data-ttu-id="5372b-179">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="5372b-179">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="5372b-180">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5372b-180">The default is `false`.</span></span>|  
|<span data-ttu-id="5372b-181">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="5372b-181">useDefaultWebProxy</span></span>|<span data-ttu-id="5372b-182">Um valor booliano que especifica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="5372b-182">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="5372b-183">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="5372b-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5372b-184">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5372b-184">Child Elements</span></span>  
  
|<span data-ttu-id="5372b-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="5372b-185">Element</span></span>|<span data-ttu-id="5372b-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="5372b-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5372b-187">\<security></span><span class="sxs-lookup"><span data-stu-id="5372b-187">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="5372b-188">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="5372b-189">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5372b-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="5372b-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5372b-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="5372b-191">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5372b-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5372b-192">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5372b-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="5372b-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5372b-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="5372b-194">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="5372b-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5372b-195">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5372b-195">Parent Elements</span></span>  
  
|<span data-ttu-id="5372b-196">Elemento</span><span class="sxs-lookup"><span data-stu-id="5372b-196">Element</span></span>|<span data-ttu-id="5372b-197">Descrição</span><span class="sxs-lookup"><span data-stu-id="5372b-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5372b-198">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5372b-198">\<bindings></span></span>](bindings.md)|<span data-ttu-id="5372b-199">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5372b-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5372b-200">Comentários</span><span class="sxs-lookup"><span data-stu-id="5372b-200">Remarks</span></span>  
 <span data-ttu-id="5372b-201">O `WSHttpBinding` é semelhante ao, `BasicHttpBinding` mas fornece mais recursos de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="5372b-201">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="5372b-202">Ele usa o transporte HTTP e fornece segurança de mensagem, como a BasicHttpBinding, mas também fornece transações, mensagens confiáveis e WS-Addressing, habilitado por padrão ou disponível por meio de uma configuração de controle único.</span><span class="sxs-lookup"><span data-stu-id="5372b-202">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5372b-203">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5372b-203">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="5372b-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5372b-204">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="5372b-205">Associações</span><span class="sxs-lookup"><span data-stu-id="5372b-205">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5372b-206">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5372b-206">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5372b-207">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5372b-207">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5372b-208">\<binding></span><span class="sxs-lookup"><span data-stu-id="5372b-208">\<binding></span></span>](../../../misc/binding.md)
