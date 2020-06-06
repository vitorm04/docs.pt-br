---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140797"
---
# \<customBinding>

<span data-ttu-id="cc609-101">Fornece controle total sobre a pilha de mensagens para o usuário.</span><span class="sxs-lookup"><span data-stu-id="cc609-101">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="cc609-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc609-102">Syntax</span></span>

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
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
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

## <a name="attributes-and-elements"></a><span data-ttu-id="cc609-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cc609-103">Attributes and Elements</span></span>

<span data-ttu-id="cc609-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc609-104">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="cc609-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc609-105">Attributes</span></span>

|<span data-ttu-id="cc609-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="cc609-106">Attribute</span></span>|<span data-ttu-id="cc609-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc609-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="cc609-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="cc609-108">closeTimeout</span></span>|<span data-ttu-id="cc609-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="cc609-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="cc609-110">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="cc609-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc609-111">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc609-111">The default is 00:01:00.</span></span>|
|<span data-ttu-id="cc609-112">name</span><span class="sxs-lookup"><span data-stu-id="cc609-112">name</span></span>|<span data-ttu-id="cc609-113">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="cc609-113">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="cc609-114">Esse valor é uma cadeia de caracteres definida pelo usuário que atua como a cadeia de caracteres de identificação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="cc609-114">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="cc609-115">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="cc609-115">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="cc609-116">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cc609-116">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="cc609-117">openTimeout</span><span class="sxs-lookup"><span data-stu-id="cc609-117">openTimeout</span></span>|<span data-ttu-id="cc609-118">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="cc609-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="cc609-119">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="cc609-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc609-120">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc609-120">The default is 00:01:00.</span></span>|
|<span data-ttu-id="cc609-121">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="cc609-121">receiveTimeout</span></span>|<span data-ttu-id="cc609-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="cc609-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="cc609-123">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="cc609-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc609-124">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc609-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="cc609-125">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="cc609-125">sendTimeout</span></span>|<span data-ttu-id="cc609-126">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="cc609-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="cc609-127">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="cc609-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc609-128">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc609-128">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cc609-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc609-129">Child Elements</span></span>

|<span data-ttu-id="cc609-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc609-130">Element</span></span>|<span data-ttu-id="cc609-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc609-131">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="cc609-132">Especifica a mensagem de duas vias para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="cc609-132">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="cc609-133">Ele é usado com transportes que não permitem comunicações duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="cc609-133">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="cc609-134">O TCP, por outro lado, permite comunicações duplex nativamente e não requer o uso desse elemento de ligação para que o serviço envie mensagens de volta para um cliente.</span><span class="sxs-lookup"><span data-stu-id="cc609-134">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="cc609-135">O cliente deve expor um endereço para que o serviço faça contato e estabeleça uma conexão.</span><span class="sxs-lookup"><span data-stu-id="cc609-135">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="cc609-136">Esse endereço de cliente é fornecido pelo `ClientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="cc609-136">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="cc609-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CompositeDuplexElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-137">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="cc609-138">Especifica um resolvedor de nome de par PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="cc609-138">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="cc609-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-139">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="cc609-140">Especifica a configuração para mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="cc609-140">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="cc609-141">Quando esse elemento é adicionado a uma associação personalizada, o canal resultante pode dar suporte a garantias de entrega exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="cc609-141">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="cc609-142">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.ReliableSessionElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-142">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="cc609-143">Especifica as opções de segurança da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="cc609-143">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="cc609-144">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-144">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="cc609-145">Especifica as configurações de segurança para uma associação de fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="cc609-145">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="cc609-146">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-146">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="cc609-147">Especifica que a associação dá suporte ao fluxo de transações e o protocolo a ser usado pelo `transactionProtocol` atributo.</span><span class="sxs-lookup"><span data-stu-id="cc609-147">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="cc609-148">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TransactionFlowElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-148">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="cc609-149">Especifica as opções de segurança de streaming da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="cc609-149">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="cc609-150">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="cc609-150">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc609-151">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc609-151">Parent Elements</span></span>

|<span data-ttu-id="cc609-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc609-152">Element</span></span>|<span data-ttu-id="cc609-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc609-153">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="cc609-154">associações</span><span class="sxs-lookup"><span data-stu-id="cc609-154">bindings</span></span>|<span data-ttu-id="cc609-155">Contém todas as associações para aplicativos Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="cc609-155">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc609-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc609-156">Remarks</span></span>

<span data-ttu-id="cc609-157">As associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="cc609-157">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="cc609-158">Associações especiais personalizadas podem ser criadas para adicionar os elementos de configuração para entidades específicas.</span><span class="sxs-lookup"><span data-stu-id="cc609-158">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="cc609-159">Por exemplo, o usuário pode combinar a seção `httpsTransport` , `reliableSession` seção e a `security` seção para criar uma associação baseada em https confiável e segura.</span><span class="sxs-lookup"><span data-stu-id="cc609-159">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="cc609-160">Uma associação individual define a pilha de mensagens especificando os elementos de configuração dos elementos de pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="cc609-160">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="cc609-161">Cada elemento define e configura o elemento de um da pilha.</span><span class="sxs-lookup"><span data-stu-id="cc609-161">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="cc609-162">Deve haver apenas um elemento de transporte em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="cc609-162">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="cc609-163">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="cc609-163">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="cc609-164">A ordem na qual os elementos aparecem na pilha é importante, pois é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="cc609-164">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="cc609-165">A ordem recomendada de elementos de pilha é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="cc609-165">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="cc609-166">Transações (opcional)</span><span class="sxs-lookup"><span data-stu-id="cc609-166">Transactions (optional)</span></span>

2. <span data-ttu-id="cc609-167">Mensagens confiáveis (opcional)</span><span class="sxs-lookup"><span data-stu-id="cc609-167">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="cc609-168">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="cc609-168">Security (optional)</span></span>

4. <span data-ttu-id="cc609-169">Transport</span><span class="sxs-lookup"><span data-stu-id="cc609-169">Transport</span></span>

5. <span data-ttu-id="cc609-170">Codificador (opcional)</span><span class="sxs-lookup"><span data-stu-id="cc609-170">Encoder (optional)</span></span>

<span data-ttu-id="cc609-171">Use uma associação personalizada quando uma das associações fornecidas pelo sistema não atender aos requisitos do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="cc609-171">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="cc609-172">Uma associação personalizada poderia ser usada, por exemplo, para habilitar o uso de um novo transporte ou um novo codificador em um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="cc609-172">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="cc609-173">Uma associação personalizada é construída usando uma das <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> coleções de elementos de associação que são "empilhadas" em uma ordem específica:</span><span class="sxs-lookup"><span data-stu-id="cc609-173">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="cc609-174">Na parte superior, há um opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> que permite transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="cc609-174">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="cc609-175">Em seguida, é um opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> que fornece um mecanismo de sessão e ordenação, conforme definido na especificação WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="cc609-175">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="cc609-176">Essa noção de uma sessão pode cruzar os intermediários de transporte e SOAP.</span><span class="sxs-lookup"><span data-stu-id="cc609-176">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="cc609-177">A seguir está um elemento de associação de segurança opcional que fornece recursos de segurança como autorização, autenticação, proteção e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="cc609-177">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="cc609-178">Os seguintes elementos de associação de segurança são fornecidos pelo Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="cc609-178">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="cc609-179">Em seguida, estão os padrões de mensagem opcionais especificados por elementos de associação:</span><span class="sxs-lookup"><span data-stu-id="cc609-179">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="cc609-180">Em seguida, estão os elementos de associação de atualizações/auxiliares de transporte opcionais:</span><span class="sxs-lookup"><span data-stu-id="cc609-180">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="cc609-181">A seguir está um elemento de associação de codificação de mensagem necessário.</span><span class="sxs-lookup"><span data-stu-id="cc609-181">Next is a required message encoding binding element.</span></span> <span data-ttu-id="cc609-182">Você pode usar seu próprio transporte ou usar uma das seguintes associações de codificação de mensagem:</span><span class="sxs-lookup"><span data-stu-id="cc609-182">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="cc609-183">Na parte inferior, há um elemento Transport necessário.</span><span class="sxs-lookup"><span data-stu-id="cc609-183">At the bottom is a required transport element.</span></span> <span data-ttu-id="cc609-184">Você pode usar seu próprio transporte ou usar um dos elementos de associação de transporte fornecidos pelo Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="cc609-184">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="cc609-185">A tabela a seguir resume as opções para cada camada.</span><span class="sxs-lookup"><span data-stu-id="cc609-185">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="cc609-186">Camada</span><span class="sxs-lookup"><span data-stu-id="cc609-186">Layer</span></span>|<span data-ttu-id="cc609-187">Opções</span><span class="sxs-lookup"><span data-stu-id="cc609-187">Options</span></span>|<span data-ttu-id="cc609-188">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="cc609-188">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="cc609-189">Fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="cc609-189">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="cc609-190">Não</span><span class="sxs-lookup"><span data-stu-id="cc609-190">No</span></span>|
|<span data-ttu-id="cc609-191">Confiabilidade</span><span class="sxs-lookup"><span data-stu-id="cc609-191">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="cc609-192">Não</span><span class="sxs-lookup"><span data-stu-id="cc609-192">No</span></span>|
|<span data-ttu-id="cc609-193">Segurança</span><span class="sxs-lookup"><span data-stu-id="cc609-193">Security</span></span>|<span data-ttu-id="cc609-194">Simétrico, assimétrico, nível de transporte</span><span class="sxs-lookup"><span data-stu-id="cc609-194">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="cc609-195">Não</span><span class="sxs-lookup"><span data-stu-id="cc609-195">No</span></span>|
|<span data-ttu-id="cc609-196">Alteração de forma</span><span class="sxs-lookup"><span data-stu-id="cc609-196">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="cc609-197">Não</span><span class="sxs-lookup"><span data-stu-id="cc609-197">No</span></span>|
|<span data-ttu-id="cc609-198">Atualizações de transporte</span><span class="sxs-lookup"><span data-stu-id="cc609-198">Transport Upgrades</span></span>|<span data-ttu-id="cc609-199">Fluxo SSL, fluxo do Windows, resolvedor de pares</span><span class="sxs-lookup"><span data-stu-id="cc609-199">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="cc609-200">Não</span><span class="sxs-lookup"><span data-stu-id="cc609-200">No</span></span>|
|<span data-ttu-id="cc609-201">Codificação</span><span class="sxs-lookup"><span data-stu-id="cc609-201">Encoding</span></span>|<span data-ttu-id="cc609-202">Texto, binário, MTOM, personalizado</span><span class="sxs-lookup"><span data-stu-id="cc609-202">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="cc609-203">Sim</span><span class="sxs-lookup"><span data-stu-id="cc609-203">Yes</span></span>|
|<span data-ttu-id="cc609-204">Transport</span><span class="sxs-lookup"><span data-stu-id="cc609-204">Transport</span></span>|<span data-ttu-id="cc609-205">TCP, pipes nomeados, HTTP, HTTPS, tipos de MSMQ, personalizado</span><span class="sxs-lookup"><span data-stu-id="cc609-205">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="cc609-206">Sim</span><span class="sxs-lookup"><span data-stu-id="cc609-206">Yes</span></span>|

<span data-ttu-id="cc609-207">Além disso, você pode definir seus próprios elementos de ligação e inseri-los entre as camadas definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cc609-207">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="cc609-208">Para obter uma discussão sobre como usar uma associação personalizada para modificar uma associação fornecida pelo sistema, consulte [como: personalizar uma associação fornecida pelo sistema](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="cc609-208">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc609-209">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc609-209">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="cc609-210">Associações</span><span class="sxs-lookup"><span data-stu-id="cc609-210">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cc609-211">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="cc609-211">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cc609-212">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="cc609-212">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cc609-213">Elemento CustomBinding</span><span class="sxs-lookup"><span data-stu-id="cc609-213">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="cc609-214">Associações</span><span class="sxs-lookup"><span data-stu-id="cc609-214">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cc609-215">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="cc609-215">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cc609-216">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="cc609-216">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
