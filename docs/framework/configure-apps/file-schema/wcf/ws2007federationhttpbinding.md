---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3025eec9c01d325d7d00a7355ff908eb1e19e410
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="c65f0-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="c65f0-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="c65f0-103">Uma associação segura e interoperável que deriva de [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e suporta segurança federada.</span><span class="sxs-lookup"><span data-stu-id="c65f0-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="c65f0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c65f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c65f0-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c65f0-105">\<bindings></span></span>  
<span data-ttu-id="c65f0-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c65f0-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65f0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c65f0-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c65f0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c65f0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c65f0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c65f0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c65f0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c65f0-110">Attributes</span></span>  
  
|<span data-ttu-id="c65f0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c65f0-111">Attribute</span></span>|<span data-ttu-id="c65f0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c65f0-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="c65f0-113">Um valor que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="c65f0-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="c65f0-114">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c65f0-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="c65f0-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="c65f0-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c65f0-116">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c65f0-117">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c65f0-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="c65f0-118">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="c65f0-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="c65f0-119">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="c65f0-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="c65f0-120">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="c65f0-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="c65f0-121">O tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="c65f0-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c65f0-122">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="c65f0-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c65f0-123">Muitas partes do [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usar buffers.</span><span class="sxs-lookup"><span data-stu-id="c65f0-123">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="c65f0-124">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="c65f0-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c65f0-125">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c65f0-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c65f0-126">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="c65f0-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="c65f0-127">O tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c65f0-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c65f0-128">O remetente de uma mensagem que exceda esse limite recebe uma falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="c65f0-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="c65f0-129">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c65f0-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c65f0-130">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="c65f0-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="c65f0-131">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c65f0-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="c65f0-132">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c65f0-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c65f0-133">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="c65f0-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="c65f0-134">-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c65f0-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="c65f0-135">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="c65f0-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="c65f0-136">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="c65f0-137">O nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="c65f0-137">The configuration name of the binding.</span></span> <span data-ttu-id="c65f0-138">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="c65f0-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c65f0-139">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="c65f0-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c65f0-140">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c65f0-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="c65f0-141">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="c65f0-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c65f0-142">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c65f0-143">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c65f0-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="c65f0-144">Um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="c65f0-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="c65f0-145">A versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="c65f0-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="c65f0-146">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="c65f0-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="c65f0-147">Se `useDefaultWebProxy` é `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="c65f0-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="c65f0-148">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="c65f0-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="c65f0-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="c65f0-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c65f0-150">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c65f0-151">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c65f0-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="c65f0-152">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="c65f0-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c65f0-153">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c65f0-154">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c65f0-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="c65f0-155">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c65f0-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c65f0-156">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c65f0-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c65f0-157">-BigEndianUnicode: Big Endian codificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="c65f0-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="c65f0-158">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="c65f0-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="c65f0-159">-UTF8: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="c65f0-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="c65f0-160">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="c65f0-160">The default is UTF8.</span></span> <span data-ttu-id="c65f0-161">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="c65f0-162">Um valor que especifica se a associação oferece suporte a fluxo de transações de WS.</span><span class="sxs-lookup"><span data-stu-id="c65f0-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="c65f0-163">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c65f0-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="c65f0-164">Um valor que indica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="c65f0-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="c65f0-165">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`.</span><span class="sxs-lookup"><span data-stu-id="c65f0-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="c65f0-166">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="c65f0-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c65f0-167">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c65f0-167">Child Elements</span></span>  
  
|<span data-ttu-id="c65f0-168">Elemento</span><span class="sxs-lookup"><span data-stu-id="c65f0-168">Element</span></span>|<span data-ttu-id="c65f0-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="c65f0-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65f0-170">\<security></span><span class="sxs-lookup"><span data-stu-id="c65f0-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="c65f0-171">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c65f0-171">Defines the security settings for the message.</span></span> <span data-ttu-id="c65f0-172">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="c65f0-173">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="c65f0-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="c65f0-174">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c65f0-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c65f0-175">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c65f0-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="c65f0-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="c65f0-176">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="c65f0-177">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="c65f0-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c65f0-178">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c65f0-178">Parent Elements</span></span>  
  
|<span data-ttu-id="c65f0-179">Elemento</span><span class="sxs-lookup"><span data-stu-id="c65f0-179">Element</span></span>|<span data-ttu-id="c65f0-180">Descrição</span><span class="sxs-lookup"><span data-stu-id="c65f0-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65f0-181">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c65f0-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="c65f0-182">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c65f0-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c65f0-183">Comentários</span><span class="sxs-lookup"><span data-stu-id="c65f0-183">Remarks</span></span>  
 <span data-ttu-id="c65f0-184">Federação é a capacidade de compartilhar identidades entre várias empresas ou domínios confiáveis para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="c65f0-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="c65f0-185">Ele usa o protocolo WS-Trust para mapear a representação da identidade de domínio de uma relação de confiança para outro.</span><span class="sxs-lookup"><span data-stu-id="c65f0-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="c65f0-186">Associação HTTP federada dá suporte à segurança SOAP, bem como a segurança de modo misto, mas não dá suporte a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="c65f0-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="c65f0-187">Serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="c65f0-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="c65f0-188">Para obter mais informações, consulte [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c65f0-188">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c65f0-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c65f0-189">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c65f0-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c65f0-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="c65f0-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c65f0-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="c65f0-192">Associações</span><span class="sxs-lookup"><span data-stu-id="c65f0-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c65f0-193">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c65f0-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c65f0-194">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c65f0-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c65f0-195">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c65f0-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
