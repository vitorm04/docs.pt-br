---
title: '&lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 480e10b9667712fbd2a3ffa95e1373d72ee1a9df
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269274"
---
# <a name="ltwshttpbindinggt"></a><span data-ttu-id="f6515-102">&lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f6515-102">&lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="f6515-103">Define uma associação segura, confiável e interoperável adequada para contratos de serviço não duplex.</span><span class="sxs-lookup"><span data-stu-id="f6515-103">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="f6515-104">A associação implementa as seguintes especificações: WS-Reliable Messaging para confiabilidade e WS-Security para autenticação e segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6515-104">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="f6515-105">O transporte é HTTP, e a codificação de mensagem é texto/XML de codificação.</span><span class="sxs-lookup"><span data-stu-id="f6515-105">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="f6515-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f6515-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6515-107">\<associações ></span><span class="sxs-lookup"><span data-stu-id="f6515-107">\<bindings></span></span>  
<span data-ttu-id="f6515-108">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f6515-108">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6515-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6515-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding   
        allowCookies="Boolean"  
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
          <message   
             algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                          clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
             establishSecurityContext="Boolean"  
             negotiateServiceCredential="Boolean" />  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6515-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f6515-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6515-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="f6515-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6515-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f6515-112">Attributes</span></span>  
  
|<span data-ttu-id="f6515-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f6515-113">Attribute</span></span>|<span data-ttu-id="f6515-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6515-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6515-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="f6515-115">allowCookies</span></span>|<span data-ttu-id="f6515-116">Um valor booliano que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="f6515-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="f6515-117">O padrão é falso.</span><span class="sxs-lookup"><span data-stu-id="f6515-117">The default is false.</span></span><br /><br /> <span data-ttu-id="f6515-118">Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="f6515-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="f6515-119">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações futuras de cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f6515-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="f6515-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="f6515-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="f6515-121">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="f6515-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="f6515-122">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f6515-122">The default is `false`.</span></span>|  
|<span data-ttu-id="f6515-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f6515-123">closeTimeout</span></span>|<span data-ttu-id="f6515-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="f6515-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f6515-125">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6515-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6515-126">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f6515-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f6515-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f6515-127">hostnameComparisonMode</span></span>|<span data-ttu-id="f6515-128">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="f6515-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f6515-129">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="f6515-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f6515-130">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="f6515-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="f6515-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f6515-131">maxBufferPoolSize</span></span>|<span data-ttu-id="f6515-132">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="f6515-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f6515-133">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="f6515-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="f6515-134">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="f6515-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="f6515-135">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="f6515-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f6515-136">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="f6515-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f6515-137">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="f6515-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="f6515-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f6515-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="f6515-139">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f6515-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f6515-140">O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="f6515-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="f6515-141">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f6515-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f6515-142">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="f6515-142">The default is 65536.</span></span>|  
|<span data-ttu-id="f6515-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="f6515-143">messageEncoding</span></span>|<span data-ttu-id="f6515-144">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6515-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="f6515-145">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f6515-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6515-146">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="f6515-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="f6515-147">-Mtom: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="f6515-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="f6515-148">-O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="f6515-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="f6515-149">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="f6515-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="f6515-150">name</span><span class="sxs-lookup"><span data-stu-id="f6515-150">name</span></span>|<span data-ttu-id="f6515-151">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="f6515-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f6515-152">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="f6515-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f6515-153">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="f6515-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f6515-154">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6515-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="f6515-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f6515-155">openTimeout</span></span>|<span data-ttu-id="f6515-156">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="f6515-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f6515-157">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6515-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6515-158">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f6515-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f6515-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="f6515-159">proxyAddress</span></span>|<span data-ttu-id="f6515-160">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6515-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="f6515-161">Se `useSystemWebProxy` está `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f6515-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="f6515-162">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="f6515-162">The default is `null`.</span></span>|  
|<span data-ttu-id="f6515-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f6515-163">receiveTimeout</span></span>|<span data-ttu-id="f6515-164">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f6515-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f6515-165">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6515-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6515-166">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f6515-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f6515-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f6515-167">sendTimeout</span></span>|<span data-ttu-id="f6515-168">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f6515-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f6515-169">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6515-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6515-170">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f6515-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f6515-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="f6515-171">textEncoding</span></span>|<span data-ttu-id="f6515-172">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f6515-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f6515-173">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f6515-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6515-174">-UnicodeFffeTextEncoding: O Unicode BigEndian de codificação.</span><span class="sxs-lookup"><span data-stu-id="f6515-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="f6515-175">-Utf16TextEncoding: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="f6515-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="f6515-176">-Utf8TextEncoding: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="f6515-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="f6515-177">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="f6515-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="f6515-178">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f6515-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="f6515-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="f6515-179">transactionFlow</span></span>|<span data-ttu-id="f6515-180">Um valor booliano que especifica se a associação dá suporte a fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="f6515-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="f6515-181">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f6515-181">The default is `false`.</span></span>|  
|<span data-ttu-id="f6515-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="f6515-182">useDefaultWebProxy</span></span>|<span data-ttu-id="f6515-183">Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="f6515-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="f6515-184">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="f6515-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6515-185">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f6515-185">Child Elements</span></span>  
  
|<span data-ttu-id="f6515-186">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6515-186">Element</span></span>|<span data-ttu-id="f6515-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6515-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6515-188">\<security></span><span class="sxs-lookup"><span data-stu-id="f6515-188">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="f6515-189">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="f6515-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="f6515-190">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f6515-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="f6515-191">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="f6515-191">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f6515-192">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f6515-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f6515-193">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f6515-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="f6515-194">reliableSession</span><span class="sxs-lookup"><span data-stu-id="f6515-194">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="f6515-195">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="f6515-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6515-196">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f6515-196">Parent Elements</span></span>  
  
|<span data-ttu-id="f6515-197">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6515-197">Element</span></span>|<span data-ttu-id="f6515-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6515-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6515-199">\<associações ></span><span class="sxs-lookup"><span data-stu-id="f6515-199">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="f6515-200">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="f6515-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6515-201">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6515-201">Remarks</span></span>  
 <span data-ttu-id="f6515-202">O `WSHttpBinding` é semelhante ao `BasicHttpBinding` , mas fornece mais recursos do serviço Web.</span><span class="sxs-lookup"><span data-stu-id="f6515-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="f6515-203">Ele usa o transporte HTTP e fornece segurança de mensagem, como faz o BasicHttpBinding, mas ele também fornece transações, sistema de mensagens confiável e WS-Addressing, seja habilitado por padrão ou disponíveis por meio de uma configuração de controle único.</span><span class="sxs-lookup"><span data-stu-id="f6515-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6515-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6515-204">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
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
  
## <a name="see-also"></a><span data-ttu-id="f6515-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6515-205">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement>  
 [<span data-ttu-id="f6515-206">Associações</span><span class="sxs-lookup"><span data-stu-id="f6515-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6515-207">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f6515-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f6515-208">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f6515-208">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f6515-209">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f6515-209">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
