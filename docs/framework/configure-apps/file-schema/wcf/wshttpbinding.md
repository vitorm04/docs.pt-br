---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 33c1d8ed0240d737f2b5f56b889cc2f31d88d018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735623"
---
# <a name="wshttpbinding"></a><span data-ttu-id="3224a-101">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3224a-101">\<wsHttpBinding></span></span>
<span data-ttu-id="3224a-102">Define uma associação segura, confiável e interoperável adequada para contratos de serviço não duplex.</span><span class="sxs-lookup"><span data-stu-id="3224a-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="3224a-103">A associação implementa as seguintes especificações: WS-Reliable Messaging for fiabilidade e WS-Security para segurança e autenticação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3224a-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="3224a-104">O transporte é HTTP e a codificação de mensagem é codificação de texto/XML.</span><span class="sxs-lookup"><span data-stu-id="3224a-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
<span data-ttu-id="3224a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3224a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3224a-106">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3224a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3224a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="3224a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3224a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**wsHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="3224a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3224a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3224a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3224a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3224a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3224a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="3224a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3224a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3224a-112">Attributes</span></span>  
  
|<span data-ttu-id="3224a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3224a-113">Attribute</span></span>|<span data-ttu-id="3224a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3224a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3224a-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="3224a-115">allowCookies</span></span>|<span data-ttu-id="3224a-116">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="3224a-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="3224a-117">O padrão é falso.</span><span class="sxs-lookup"><span data-stu-id="3224a-117">The default is false.</span></span><br /><br /> <span data-ttu-id="3224a-118">Você pode usar essa propriedade ao interagir com serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="3224a-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="3224a-119">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="3224a-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="3224a-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="3224a-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="3224a-121">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="3224a-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="3224a-122">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3224a-122">The default is `false`.</span></span>|  
|<span data-ttu-id="3224a-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="3224a-123">closeTimeout</span></span>|<span data-ttu-id="3224a-124">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="3224a-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3224a-125">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3224a-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3224a-126">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3224a-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="3224a-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="3224a-127">hostnameComparisonMode</span></span>|<span data-ttu-id="3224a-128">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="3224a-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="3224a-129">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="3224a-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="3224a-130">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="3224a-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="3224a-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="3224a-131">maxBufferPoolSize</span></span>|<span data-ttu-id="3224a-132">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="3224a-133">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="3224a-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="3224a-134">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="3224a-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="3224a-135">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="3224a-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="3224a-136">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="3224a-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="3224a-137">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="3224a-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="3224a-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="3224a-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="3224a-139">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="3224a-140">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="3224a-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="3224a-141">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3224a-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="3224a-142">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="3224a-142">The default is 65536.</span></span>|  
|<span data-ttu-id="3224a-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="3224a-143">messageEncoding</span></span>|<span data-ttu-id="3224a-144">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="3224a-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="3224a-145">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3224a-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3224a-146">-Text: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="3224a-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="3224a-147">-MTOM: usar um codificador MTOM (mecanismo de organização de transmissão de mensagens) 1,0.</span><span class="sxs-lookup"><span data-stu-id="3224a-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="3224a-148">-O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="3224a-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="3224a-149">Este atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="3224a-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="3224a-150">name</span><span class="sxs-lookup"><span data-stu-id="3224a-150">name</span></span>|<span data-ttu-id="3224a-151">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3224a-152">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3224a-153">A partir do [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="3224a-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3224a-154">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3224a-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="3224a-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="3224a-155">openTimeout</span></span>|<span data-ttu-id="3224a-156">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="3224a-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3224a-157">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3224a-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3224a-158">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3224a-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="3224a-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="3224a-159">proxyAddress</span></span>|<span data-ttu-id="3224a-160">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="3224a-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="3224a-161">Se `useSystemWebProxy` for `true`, essa configuração deverá ser `null`.</span><span class="sxs-lookup"><span data-stu-id="3224a-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="3224a-162">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="3224a-162">The default is `null`.</span></span>|  
|<span data-ttu-id="3224a-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="3224a-163">receiveTimeout</span></span>|<span data-ttu-id="3224a-164">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="3224a-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3224a-165">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3224a-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3224a-166">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3224a-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="3224a-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="3224a-167">sendTimeout</span></span>|<span data-ttu-id="3224a-168">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="3224a-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3224a-169">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3224a-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3224a-170">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3224a-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="3224a-171">codificação de</span><span class="sxs-lookup"><span data-stu-id="3224a-171">textEncoding</span></span>|<span data-ttu-id="3224a-172">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3224a-173">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3224a-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3224a-174">-UnicodeFffeTextEncoding: codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="3224a-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="3224a-175">-Utf16TextEncoding: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="3224a-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="3224a-176">-Utf8TextEncoding: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="3224a-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="3224a-177">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="3224a-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="3224a-178">Este atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="3224a-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="3224a-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="3224a-179">transactionFlow</span></span>|<span data-ttu-id="3224a-180">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="3224a-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="3224a-181">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3224a-181">The default is `false`.</span></span>|  
|<span data-ttu-id="3224a-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="3224a-182">useDefaultWebProxy</span></span>|<span data-ttu-id="3224a-183">Um valor booliano que especifica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="3224a-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="3224a-184">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="3224a-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3224a-185">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3224a-185">Child Elements</span></span>  
  
|<span data-ttu-id="3224a-186">Elemento</span><span class="sxs-lookup"><span data-stu-id="3224a-186">Element</span></span>|<span data-ttu-id="3224a-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="3224a-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3224a-188">\<Security ></span><span class="sxs-lookup"><span data-stu-id="3224a-188">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="3224a-189">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="3224a-190">Este elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3224a-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="3224a-191">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3224a-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="3224a-192">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="3224a-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3224a-193">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="3224a-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="3224a-194">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3224a-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="3224a-195">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="3224a-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3224a-196">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3224a-196">Parent Elements</span></span>  
  
|<span data-ttu-id="3224a-197">Elemento</span><span class="sxs-lookup"><span data-stu-id="3224a-197">Element</span></span>|<span data-ttu-id="3224a-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="3224a-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3224a-199">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="3224a-199">\<bindings></span></span>](bindings.md)|<span data-ttu-id="3224a-200">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="3224a-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3224a-201">Comentários</span><span class="sxs-lookup"><span data-stu-id="3224a-201">Remarks</span></span>  
 <span data-ttu-id="3224a-202">O `WSHttpBinding` é semelhante ao `BasicHttpBinding`, mas fornece mais recursos de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="3224a-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="3224a-203">Ele usa o transporte HTTP e fornece segurança de mensagem, como a BasicHttpBinding, mas também fornece transações, mensagens confiáveis e WS-Addressing, habilitado por padrão ou disponível por meio de uma configuração de controle único.</span><span class="sxs-lookup"><span data-stu-id="3224a-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3224a-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3224a-204">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3224a-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3224a-205">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="3224a-206">Associações</span><span class="sxs-lookup"><span data-stu-id="3224a-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3224a-207">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3224a-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3224a-208">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3224a-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3224a-209">\<binding ></span><span class="sxs-lookup"><span data-stu-id="3224a-209">\<binding></span></span>](bindings.md)
