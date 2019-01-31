---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: d7203aa5695690bfc46c22e87b59f7dfcbd281fa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275802"
---
# <a name="custombinding"></a><span data-ttu-id="f9243-101">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f9243-101">\<customBinding></span></span>
<span data-ttu-id="f9243-102">Fornece controle total sobre a pilha de mensagens para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f9243-102">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="f9243-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f9243-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f9243-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f9243-104">\<bindings></span></span>  
<span data-ttu-id="f9243-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f9243-105">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9243-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9243-106">Syntax</span></span>  
  
```xml  
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9243-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f9243-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f9243-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="f9243-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9243-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f9243-109">Attributes</span></span>  
  
|<span data-ttu-id="f9243-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="f9243-110">Attribute</span></span>|<span data-ttu-id="f9243-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9243-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9243-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f9243-112">closeTimeout</span></span>|<span data-ttu-id="f9243-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="f9243-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f9243-114">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9243-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9243-115">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f9243-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f9243-116">name</span><span class="sxs-lookup"><span data-stu-id="f9243-116">name</span></span>|<span data-ttu-id="f9243-117">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="f9243-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f9243-118">Esse valor é uma cadeia de caracteres definida pelo usuário que atua como a cadeia de caracteres de identificação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f9243-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="f9243-119">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="f9243-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f9243-120">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f9243-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="f9243-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f9243-121">openTimeout</span></span>|<span data-ttu-id="f9243-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="f9243-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f9243-123">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9243-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9243-124">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f9243-124">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f9243-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f9243-125">receiveTimeout</span></span>|<span data-ttu-id="f9243-126">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f9243-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f9243-127">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9243-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9243-128">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f9243-128">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f9243-129">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f9243-129">sendTimeout</span></span>|<span data-ttu-id="f9243-130">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f9243-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f9243-131">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9243-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9243-132">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f9243-132">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9243-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f9243-133">Child Elements</span></span>  
  
|<span data-ttu-id="f9243-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9243-134">Element</span></span>|<span data-ttu-id="f9243-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9243-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9243-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="f9243-136">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="f9243-137">Especifica o sistema de mensagens bidirecional para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f9243-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="f9243-138">Ele é usado com os transportes que não permitem comunicações duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9243-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f9243-139">TCP, por outro lado, permite que as comunicações duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.</span><span class="sxs-lookup"><span data-stu-id="f9243-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="f9243-140">O cliente deve expor um endereço para o serviço para que entre em contato com e estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="f9243-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f9243-141">Esse endereço de cliente é fornecido pelo `ClientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="f9243-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="f9243-142">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="f9243-143">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="f9243-143">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="f9243-144">Especifica um resolvedor de nome de pares de protocolo de resolução de nome de ponto a ponto (PNRP).</span><span class="sxs-lookup"><span data-stu-id="f9243-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="f9243-145">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="f9243-146">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="f9243-146">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="f9243-147">Especifica a configuração para mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f9243-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="f9243-148">Quando esse elemento é adicionado a uma ligação personalizada, o canal resultante pode dar suporte a exatamente-uma vez as garantias de entrega.</span><span class="sxs-lookup"><span data-stu-id="f9243-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="f9243-149">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="f9243-150">\<security></span><span class="sxs-lookup"><span data-stu-id="f9243-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="f9243-151">Especifica as opções de segurança da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f9243-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="f9243-152">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="f9243-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="f9243-153">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="f9243-154">Especifica as configurações de segurança para uma associação de fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="f9243-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="f9243-155">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="f9243-156">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="f9243-156">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="f9243-157">Especifica que a associação dá suporte ao fluxo de transações e o protocolo a ser usado pelo `transactionProtocol` atributo.</span><span class="sxs-lookup"><span data-stu-id="f9243-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="f9243-158">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="f9243-159">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="f9243-159">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="f9243-160">Especifica as opções de segurança da associação personalizada de fluxo.</span><span class="sxs-lookup"><span data-stu-id="f9243-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="f9243-161">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f9243-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9243-162">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f9243-162">Parent Elements</span></span>  
  
|<span data-ttu-id="f9243-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9243-163">Element</span></span>|<span data-ttu-id="f9243-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9243-164">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9243-165">associações</span><span class="sxs-lookup"><span data-stu-id="f9243-165">bindings</span></span>|<span data-ttu-id="f9243-166">Contém todas as associações de aplicativos do Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="f9243-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9243-167">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9243-167">Remarks</span></span>  
 <span data-ttu-id="f9243-168">Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="f9243-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="f9243-169">Associações personalizadas especiais podem ser criadas com o meu adicionando os elementos de configuração para entidades específicas.</span><span class="sxs-lookup"><span data-stu-id="f9243-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="f9243-170">Por exemplo, o usuário pode combinar as `httpsTransport` seção, `reliableSession` seção e o `security` associação baseado em seção para criar um https seguro e confiável.</span><span class="sxs-lookup"><span data-stu-id="f9243-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="f9243-171">Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="f9243-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="f9243-172">Cada elemento define e configura um elemento da pilha.</span><span class="sxs-lookup"><span data-stu-id="f9243-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="f9243-173">Deve haver apenas um elemento de transporte em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f9243-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="f9243-174">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="f9243-174">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="f9243-175">A ordem na qual os elementos aparecem na pilha é importante, porque ele é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="f9243-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="f9243-176">A ordem recomendada de elementos da pilha é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f9243-176">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="f9243-177">Transações (opcionais)</span><span class="sxs-lookup"><span data-stu-id="f9243-177">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="f9243-178">(Opcional) de mensagens confiáveis</span><span class="sxs-lookup"><span data-stu-id="f9243-178">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="f9243-179">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="f9243-179">Security (optional)</span></span>  
  
4.  <span data-ttu-id="f9243-180">Transporte</span><span class="sxs-lookup"><span data-stu-id="f9243-180">Transport</span></span>  
  
5.  <span data-ttu-id="f9243-181">Codificador (opcional)</span><span class="sxs-lookup"><span data-stu-id="f9243-181">Encoder (optional)</span></span>  
  
 <span data-ttu-id="f9243-182">Use uma ligação personalizada quando uma das associações fornecidas pelo sistema não atende aos requisitos do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="f9243-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="f9243-183">Uma associação personalizada pode ser usada, por exemplo, para habilitar o uso de um novo transporte ou de um codificador de novo em um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9243-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="f9243-184">Uma associação personalizada é construída usando uma da <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> de uma coleção de elementos de associação que são "empilhados" em uma ordem específica:</span><span class="sxs-lookup"><span data-stu-id="f9243-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="f9243-185">Na parte superior é um recurso opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> que permite a fluir transações.</span><span class="sxs-lookup"><span data-stu-id="f9243-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="f9243-186">Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> que fornece uma sessão e mecanismo de ordenação, conforme definido na especificação WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f9243-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="f9243-187">Essa noção de uma sessão pode cruzar intermediários SOAP e transporte.</span><span class="sxs-lookup"><span data-stu-id="f9243-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="f9243-188">Em seguida, é um elemento de associação de segurança opcional que fornece recursos de segurança como autenticação, autorização, proteção e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="f9243-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="f9243-189">Os seguintes elementos de associação de segurança são fornecidos pelo Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="f9243-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="f9243-190">Em seguida os padrões de mensagem opcionais são especificados pelos elementos de associação:</span><span class="sxs-lookup"><span data-stu-id="f9243-190">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="f9243-191">Em seguida, estão os upgrades/auxiliares de transporte opcional elementos de associação:</span><span class="sxs-lookup"><span data-stu-id="f9243-191">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="f9243-192">Em seguida, é um elemento de associação de codificação de mensagem necessário.</span><span class="sxs-lookup"><span data-stu-id="f9243-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="f9243-193">Você pode usar seu próprio transporte ou use um da seguinte mensagem de codificação associações:</span><span class="sxs-lookup"><span data-stu-id="f9243-193">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="f9243-194">Na parte inferior é um elemento de transporte obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f9243-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="f9243-195">Você pode usar seu próprio transporte ou use um dos elementos fornecidos pelo Windows Communication Foundation (WCF) de associação de transporte:</span><span class="sxs-lookup"><span data-stu-id="f9243-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="f9243-196">A tabela a seguir resume as opções para cada camada.</span><span class="sxs-lookup"><span data-stu-id="f9243-196">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="f9243-197">Camada</span><span class="sxs-lookup"><span data-stu-id="f9243-197">Layer</span></span>|<span data-ttu-id="f9243-198">Opções</span><span class="sxs-lookup"><span data-stu-id="f9243-198">Options</span></span>|<span data-ttu-id="f9243-199">Necessária</span><span class="sxs-lookup"><span data-stu-id="f9243-199">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="f9243-200">Fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="f9243-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="f9243-201">Não</span><span class="sxs-lookup"><span data-stu-id="f9243-201">No</span></span>|  
|<span data-ttu-id="f9243-202">Confiabilidade</span><span class="sxs-lookup"><span data-stu-id="f9243-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="f9243-203">Não</span><span class="sxs-lookup"><span data-stu-id="f9243-203">No</span></span>|  
|<span data-ttu-id="f9243-204">Segurança</span><span class="sxs-lookup"><span data-stu-id="f9243-204">Security</span></span>|<span data-ttu-id="f9243-205">Simétrica, assimétrica, nível de transporte</span><span class="sxs-lookup"><span data-stu-id="f9243-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="f9243-206">Não</span><span class="sxs-lookup"><span data-stu-id="f9243-206">No</span></span>|  
|<span data-ttu-id="f9243-207">Alteração de forma</span><span class="sxs-lookup"><span data-stu-id="f9243-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="f9243-208">Não</span><span class="sxs-lookup"><span data-stu-id="f9243-208">No</span></span>|  
|<span data-ttu-id="f9243-209">Upgrades de transporte</span><span class="sxs-lookup"><span data-stu-id="f9243-209">Transport Upgrades</span></span>|<span data-ttu-id="f9243-210">Fluxo de SSL, fluxo do Windows, resolvedor de pares</span><span class="sxs-lookup"><span data-stu-id="f9243-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="f9243-211">Não</span><span class="sxs-lookup"><span data-stu-id="f9243-211">No</span></span>|  
|<span data-ttu-id="f9243-212">Codificando</span><span class="sxs-lookup"><span data-stu-id="f9243-212">Encoding</span></span>|<span data-ttu-id="f9243-213">Texto, binário, MTOM, personalizado</span><span class="sxs-lookup"><span data-stu-id="f9243-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="f9243-214">Sim</span><span class="sxs-lookup"><span data-stu-id="f9243-214">Yes</span></span>|  
|<span data-ttu-id="f9243-215">Transporte</span><span class="sxs-lookup"><span data-stu-id="f9243-215">Transport</span></span>|<span data-ttu-id="f9243-216">Tipos HTTP, HTTPS, TCP, Pipes nomeados, MSMQ, personalizado</span><span class="sxs-lookup"><span data-stu-id="f9243-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="f9243-217">Sim</span><span class="sxs-lookup"><span data-stu-id="f9243-217">Yes</span></span>|  
  
 <span data-ttu-id="f9243-218">Além disso, você pode definir seus próprios elementos de associação e inseri-los entre qualquer uma das camadas anteriores definidas.</span><span class="sxs-lookup"><span data-stu-id="f9243-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="f9243-219">Para obter uma discussão sobre como usar uma associação para modificar uma associação fornecida pelo sistema personalizada, consulte [como: Personalizar uma associação fornecida pelo sistema](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="f9243-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
    
  
## <a name="see-also"></a><span data-ttu-id="f9243-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9243-220">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f9243-221">\<binding></span><span class="sxs-lookup"><span data-stu-id="f9243-221">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="f9243-222">Associações</span><span class="sxs-lookup"><span data-stu-id="f9243-222">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f9243-223">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="f9243-223">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f9243-224">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f9243-224">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f9243-225">customBinding elemento</span><span class="sxs-lookup"><span data-stu-id="f9243-225">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="f9243-226">Associações</span><span class="sxs-lookup"><span data-stu-id="f9243-226">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f9243-227">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f9243-227">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f9243-228">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f9243-228">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
