---
title: '&lt;wsFederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 694b904587795823ae2f730b8182f404eba93a58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsfederationhttpbindinggt"></a><span data-ttu-id="dfc5d-102">&lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="dfc5d-102">&lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="dfc5d-103">Define uma associação que dá suporte ao WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-103">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="dfc5d-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dfc5d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dfc5d-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="dfc5d-105">\<bindings></span></span>  
<span data-ttu-id="dfc5d-106">elemento FederationBinding</span><span class="sxs-lookup"><span data-stu-id="dfc5d-106">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc5d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfc5d-107">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>  
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
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfc5d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dfc5d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dfc5d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfc5d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="dfc5d-110">Attributes</span></span>  
  
|<span data-ttu-id="dfc5d-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="dfc5d-111">Attribute</span></span>|<span data-ttu-id="dfc5d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfc5d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfc5d-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="dfc5d-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="dfc5d-114">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="dfc5d-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-115">The default is `false`.</span></span>|  
|<span data-ttu-id="dfc5d-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="dfc5d-116">closeTimeout</span></span>|<span data-ttu-id="dfc5d-117">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dfc5d-118">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dfc5d-119">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dfc5d-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="dfc5d-120">hostnameComparisonMode</span></span>|<span data-ttu-id="dfc5d-121">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="dfc5d-122">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="dfc5d-123">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="dfc5d-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="dfc5d-124">maxBufferPoolSize</span></span>|<span data-ttu-id="dfc5d-125">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="dfc5d-126">O padrão é 524.288 bytes (512 * 1024).</span><span class="sxs-lookup"><span data-stu-id="dfc5d-126">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="dfc5d-127">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="dfc5d-128">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="dfc5d-129">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="dfc5d-130">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="dfc5d-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="dfc5d-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="dfc5d-132">Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="dfc5d-133">O remetente de uma mensagem exceder esse limite recebem uma falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="dfc5d-134">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="dfc5d-135">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-135">The default is 65536.</span></span>|  
|<span data-ttu-id="dfc5d-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="dfc5d-136">messageEncoding</span></span>|<span data-ttu-id="dfc5d-137">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="dfc5d-138">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dfc5d-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dfc5d-139">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="dfc5d-140">-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="dfc5d-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="dfc5d-141">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="dfc5d-142">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="dfc5d-143">name</span><span class="sxs-lookup"><span data-stu-id="dfc5d-143">name</span></span>|<span data-ttu-id="dfc5d-144">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dfc5d-145">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="dfc5d-146">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dfc5d-147">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dfc5d-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="dfc5d-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="dfc5d-148">openTimeout</span></span>|<span data-ttu-id="dfc5d-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dfc5d-150">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dfc5d-151">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dfc5d-152">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="dfc5d-152">privactyNoticeAt</span></span>|<span data-ttu-id="dfc5d-153">Uma cadeia de caracteres que especifica um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-153">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="dfc5d-154">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="dfc5d-154">privactyNoticeVersion</span></span>|<span data-ttu-id="dfc5d-155">Um inteiro que especifica a versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-155">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="dfc5d-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="dfc5d-156">proxyAddress</span></span>|<span data-ttu-id="dfc5d-157">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="dfc5d-158">Se `useDefaultWebProxy` é `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="dfc5d-159">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-159">The default is `null`.</span></span>|  
|<span data-ttu-id="dfc5d-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="dfc5d-160">receiveTimeout</span></span>|<span data-ttu-id="dfc5d-161">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dfc5d-162">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dfc5d-163">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-163">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="dfc5d-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="dfc5d-164">sendTimeout</span></span>|<span data-ttu-id="dfc5d-165">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dfc5d-166">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dfc5d-167">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dfc5d-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="dfc5d-168">textEncoding</span></span>|<span data-ttu-id="dfc5d-169">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="dfc5d-170">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dfc5d-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dfc5d-171">-BigEndianUnicode: O Unicode BigEndian codificação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="dfc5d-172">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="dfc5d-173">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="dfc5d-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="dfc5d-174">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-174">The default is UTF8.</span></span> <span data-ttu-id="dfc5d-175">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="dfc5d-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="dfc5d-176">transactionFlow</span></span>|<span data-ttu-id="dfc5d-177">Um valor booleano que especifica se a associação oferece suporte a fluxo de transações de WS.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="dfc5d-178">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-178">The default is `false`.</span></span>|  
|<span data-ttu-id="dfc5d-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="dfc5d-179">useDefaultWebProxy</span></span>|<span data-ttu-id="dfc5d-180">Um valor booliano que indica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="dfc5d-181">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="dfc5d-182">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfc5d-183">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dfc5d-183">Child Elements</span></span>  
  
|<span data-ttu-id="dfc5d-184">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfc5d-184">Element</span></span>|<span data-ttu-id="dfc5d-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfc5d-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfc5d-186">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="dfc5d-186">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="dfc5d-187">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-187">Defines the security settings for the message.</span></span> <span data-ttu-id="dfc5d-188">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="dfc5d-189">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="dfc5d-189">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="dfc5d-190">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dfc5d-191">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="dfc5d-192">reliableSession</span><span class="sxs-lookup"><span data-stu-id="dfc5d-192">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="dfc5d-193">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dfc5d-194">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dfc5d-194">Parent Elements</span></span>  
  
|<span data-ttu-id="dfc5d-195">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfc5d-195">Element</span></span>|<span data-ttu-id="dfc5d-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfc5d-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfc5d-197">\<associações ></span><span class="sxs-lookup"><span data-stu-id="dfc5d-197">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="dfc5d-198">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc5d-199">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfc5d-199">Remarks</span></span>  
 <span data-ttu-id="dfc5d-200">Federação é a capacidade de compartilhar identidades entre vários sistemas de autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="dfc5d-201">Essas identidades podem referir-se a usuários ou computadores.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="dfc5d-202">HTTP federado dá suporte à segurança SOAP, bem como a segurança de modo misto, mas ele não oferece suporte ao uso exclusivamente a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="dfc5d-203">Essa associação fornece [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] suporte para o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-203">This binding provides [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] support for the WS-Federation protocol.</span></span> <span data-ttu-id="dfc5d-204">Serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-204">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="dfc5d-205">Associações consistem em uma pilha de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="dfc5d-206">A pilha de elementos de associação</span><span class="sxs-lookup"><span data-stu-id="dfc5d-206">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="dfc5d-207">`wsFederationHttpBinding`é o mesmo que contidos em`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="dfc5d-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="dfc5d-208">Quando [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) é definido como o valor padrão de <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-208">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="dfc5d-209">O `wsFederationHttpBinding` controla os detalhes das configurações de segurança de mensagem em [ \<mensagem >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="dfc5d-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="dfc5d-210">Observe que o [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) elemento fornece obter acesso somente à medida que a segurança usada por meio da associação não pode ser alterada depois que a associação é criada.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-210">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="dfc5d-211">O `wsFederationHttpBinding` também fornece um atributo privactyNoticeAt para definir e recuperar o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-211">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="dfc5d-212">Manter a política de segurança é especialmente importante em cenários de Federação.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="dfc5d-213">A recomendação é usar alguma forma de segurança, como HTTPS, para proteger a política contra usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="dfc5d-214">Em cenários de Federação usando essa associação, possivelmente, a política de serviço tem informações importantes, como a chave usada para criptografar o token emitido (SAML), o tipo de declaração para colocar no token e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="dfc5d-215">Se essa política for violada, um invasor pode descobrir a chave do token emitido resultando em violação adicional, divulgação de informações e outros comportamentos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="dfc5d-216">Para evitar isso, a política deve ser obtida com segurança (por exemplo usando HTTPS) do serviço.</span><span class="sxs-lookup"><span data-stu-id="dfc5d-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="dfc5d-217">Para obter mais informações sobre essa associação, consulte [como: criar uma WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="dfc5d-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfc5d-218">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfc5d-218">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="saml"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</wsFederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfc5d-219">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfc5d-219">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [<span data-ttu-id="dfc5d-220">Como: criar uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="dfc5d-220">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="dfc5d-221">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="dfc5d-221">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="dfc5d-222">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="dfc5d-222">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="dfc5d-223">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="dfc5d-223">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="dfc5d-224">\<associação ></span><span class="sxs-lookup"><span data-stu-id="dfc5d-224">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
