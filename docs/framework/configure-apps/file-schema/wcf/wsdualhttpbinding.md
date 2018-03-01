---
title: '&lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a49b534ba22f4ac422eb26885388e24594b49afd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltwsdualhttpbindinggt"></a><span data-ttu-id="ba815-102">&lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ba815-102">&lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="ba815-103">Define uma associação segura, confiável e interoperável adequada para contratos de serviço duplex ou comunicação através de intermediários SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba815-103">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="ba815-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba815-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba815-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ba815-105">\<bindings></span></span>  
<span data-ttu-id="ba815-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ba815-106">\<wsDualHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba815-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba815-107">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba815-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ba815-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ba815-109">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="ba815-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba815-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba815-110">Attributes</span></span>  
  
|<span data-ttu-id="ba815-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ba815-111">Attribute</span></span>|<span data-ttu-id="ba815-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba815-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba815-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="ba815-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="ba815-114">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="ba815-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="ba815-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ba815-115">The default is `false`.</span></span>|  
|<span data-ttu-id="ba815-116">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="ba815-116">clientBaseAddress</span></span>|<span data-ttu-id="ba815-117">Um URI que define o endereço base que o cliente aguarda para mensagens de resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="ba815-117">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="ba815-118">Se especificado, esse endereço (mais por channelGUID) é usado para escuta.</span><span class="sxs-lookup"><span data-stu-id="ba815-118">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="ba815-119">Se o valor não for especificado, o endereço base do cliente é gerado de forma específica de transporte.</span><span class="sxs-lookup"><span data-stu-id="ba815-119">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="ba815-120">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="ba815-120">The default is `null`.</span></span>|  
|<span data-ttu-id="ba815-121">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="ba815-121">closeTimeout</span></span>|<span data-ttu-id="ba815-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="ba815-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ba815-123">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ba815-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ba815-124">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ba815-124">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="ba815-125">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="ba815-125">hostnameComparisonMode</span></span>|<span data-ttu-id="ba815-126">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="ba815-126">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="ba815-127">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="ba815-127">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="ba815-128">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="ba815-128">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="ba815-129">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="ba815-129">maxBufferPoolSize</span></span>|<span data-ttu-id="ba815-130">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="ba815-130">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="ba815-131">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="ba815-131">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="ba815-132">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="ba815-132">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="ba815-133">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="ba815-133">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="ba815-134">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="ba815-134">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="ba815-135">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="ba815-135">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="ba815-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="ba815-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="ba815-137">Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="ba815-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="ba815-138">O remetente de uma mensagem exceder esse limite recebem uma falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba815-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="ba815-139">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ba815-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="ba815-140">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="ba815-140">The default is 65536.</span></span>|  
|<span data-ttu-id="ba815-141">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="ba815-141">messageEncoding</span></span>|<span data-ttu-id="ba815-142">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ba815-142">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="ba815-143">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba815-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ba815-144">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="ba815-144">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="ba815-145">-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ba815-145">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="ba815-146">-O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="ba815-146">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="ba815-147">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="ba815-147">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="ba815-148">name</span><span class="sxs-lookup"><span data-stu-id="ba815-148">name</span></span>|<span data-ttu-id="ba815-149">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="ba815-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ba815-150">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="ba815-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ba815-151">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="ba815-151">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ba815-152">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ba815-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="ba815-153">openTimeout</span><span class="sxs-lookup"><span data-stu-id="ba815-153">openTimeout</span></span>|<span data-ttu-id="ba815-154">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="ba815-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ba815-155">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ba815-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ba815-156">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ba815-156">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="ba815-157">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="ba815-157">proxyAddress</span></span>|<span data-ttu-id="ba815-158">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="ba815-158">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="ba815-159">Se `useDefaultWebProxy` é `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="ba815-159">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="ba815-160">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="ba815-160">The default is `null`.</span></span>|  
|<span data-ttu-id="ba815-161">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="ba815-161">receiveTimeout</span></span>|<span data-ttu-id="ba815-162">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="ba815-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ba815-163">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ba815-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ba815-164">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ba815-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="ba815-165">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="ba815-165">sendTimeout</span></span>|<span data-ttu-id="ba815-166">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="ba815-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ba815-167">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ba815-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ba815-168">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ba815-168">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="ba815-169">textEncoding</span><span class="sxs-lookup"><span data-stu-id="ba815-169">textEncoding</span></span>|<span data-ttu-id="ba815-170">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ba815-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ba815-171">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba815-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ba815-172">-BigEndianUnicode: O Unicode BigEndian codificação.</span><span class="sxs-lookup"><span data-stu-id="ba815-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="ba815-173">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="ba815-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="ba815-174">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="ba815-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="ba815-175">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="ba815-175">The default is UTF8.</span></span> <span data-ttu-id="ba815-176">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ba815-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="ba815-177">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="ba815-177">transactionFlow</span></span>|<span data-ttu-id="ba815-178">Um valor booleano que especifica se a associação oferece suporte a fluxo de transações de WS.</span><span class="sxs-lookup"><span data-stu-id="ba815-178">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="ba815-179">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ba815-179">The default is `false`.</span></span>|  
|<span data-ttu-id="ba815-180">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="ba815-180">useDefaultWebProxy</span></span>|<span data-ttu-id="ba815-181">Um valor booliano que indica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="ba815-181">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="ba815-182">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`.</span><span class="sxs-lookup"><span data-stu-id="ba815-182">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="ba815-183">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="ba815-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba815-184">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ba815-184">Child Elements</span></span>  
  
|<span data-ttu-id="ba815-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba815-185">Element</span></span>|<span data-ttu-id="ba815-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba815-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba815-187">\<security></span><span class="sxs-lookup"><span data-stu-id="ba815-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="ba815-188">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="ba815-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="ba815-189">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ba815-189">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="ba815-190">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="ba815-190">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="ba815-191">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="ba815-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ba815-192">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ba815-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="ba815-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="ba815-193">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="ba815-194">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="ba815-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba815-195">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ba815-195">Parent Elements</span></span>  
  
|<span data-ttu-id="ba815-196">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba815-196">Element</span></span>|<span data-ttu-id="ba815-197">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba815-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba815-198">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ba815-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="ba815-199">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ba815-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba815-200">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba815-200">Remarks</span></span>  
 <span data-ttu-id="ba815-201">O `WSDualHttpBinding` fornece o mesmo suporte para protocolos de serviço da Web como o `WSHttpBinding`, mas para uso com contratos duplex.</span><span class="sxs-lookup"><span data-stu-id="ba815-201">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="ba815-202">`WSDualHttpBinding`só dá suporte à segurança SOAP e requer o sistema de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="ba815-202">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="ba815-203">Essa associação requer que o cliente tem um URI público que fornece um ponto de extremidade de retorno de chamada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ba815-203">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="ba815-204">Isso é fornecido pelo `clientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="ba815-204">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="ba815-205">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ba815-205">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="ba815-206">O cliente deve usar a segurança para garantir que ele só se conecta aos serviços-relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="ba815-206">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="ba815-207">Essa associação pode ser usada para se comunicar com segurança por meio de um ou mais intermediários SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba815-207">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="ba815-208">Por padrão, essa associação gera uma pilha de tempo de execução com o WS-ReliableMessaging de confiabilidade, WS-Security para segurança de mensagem e autenticação de HTTP para entrega de mensagens e uma codificação de mensagem de texto/XML.</span><span class="sxs-lookup"><span data-stu-id="ba815-208">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba815-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba815-209">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba815-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba815-210">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [<span data-ttu-id="ba815-211">Associações</span><span class="sxs-lookup"><span data-stu-id="ba815-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ba815-212">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ba815-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ba815-213">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ba815-213">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ba815-214">\<binding></span><span class="sxs-lookup"><span data-stu-id="ba815-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
