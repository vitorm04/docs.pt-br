---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 0a77c791d55c6009cf59d5a4b15f3b2a63b7ccf9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140465"
---
# \<wsFederationHttpBinding>

<span data-ttu-id="19a01-101">Define uma associação que oferece suporte ao WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="19a01-101">Defines a binding that supports WS-Federation.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a><span data-ttu-id="19a01-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19a01-102">Syntax</span></span>

```xml
<wsFederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
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
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
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
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
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
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19a01-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="19a01-103">Attributes and Elements</span></span>

<span data-ttu-id="19a01-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="19a01-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="19a01-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="19a01-105">Attributes</span></span>

|<span data-ttu-id="19a01-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="19a01-106">Attribute</span></span>|<span data-ttu-id="19a01-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="19a01-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="19a01-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="19a01-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="19a01-109">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="19a01-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="19a01-110">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="19a01-110">The default is `false`.</span></span>|
|<span data-ttu-id="19a01-111">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="19a01-111">closeTimeout</span></span>|<span data-ttu-id="19a01-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="19a01-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="19a01-113">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="19a01-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19a01-114">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19a01-114">The default is 00:01:00.</span></span>|
|<span data-ttu-id="19a01-115">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="19a01-115">hostnameComparisonMode</span></span>|<span data-ttu-id="19a01-116">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="19a01-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="19a01-117">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode> , que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="19a01-117">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="19a01-118">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="19a01-118">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="19a01-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="19a01-119">maxBufferPoolSize</span></span>|<span data-ttu-id="19a01-120">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="19a01-121">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="19a01-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="19a01-122">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="19a01-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="19a01-123">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="19a01-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="19a01-124">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="19a01-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="19a01-125">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="19a01-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="19a01-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="19a01-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="19a01-127">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="19a01-128">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="19a01-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="19a01-129">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="19a01-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="19a01-130">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="19a01-130">The default is 65536.</span></span>|
|<span data-ttu-id="19a01-131">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="19a01-131">messageEncoding</span></span>|<span data-ttu-id="19a01-132">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="19a01-132">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="19a01-133">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="19a01-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="19a01-134">-Text: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="19a01-134">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="19a01-135">-MTOM: usar um codificador MTOM (mecanismo de organização de transmissão de mensagens) 1,0.</span><span class="sxs-lookup"><span data-stu-id="19a01-135">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="19a01-136">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="19a01-136">The default is Text.</span></span><br /><br /> <span data-ttu-id="19a01-137">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="19a01-137">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="19a01-138">name</span><span class="sxs-lookup"><span data-stu-id="19a01-138">name</span></span>|<span data-ttu-id="19a01-139">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="19a01-140">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="19a01-141">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="19a01-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="19a01-142">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="19a01-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="19a01-143">openTimeout</span><span class="sxs-lookup"><span data-stu-id="19a01-143">openTimeout</span></span>|<span data-ttu-id="19a01-144">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="19a01-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="19a01-145">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="19a01-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19a01-146">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19a01-146">The default is 00:01:00.</span></span>|
|<span data-ttu-id="19a01-147">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="19a01-147">privacyNoticeAt</span></span>|<span data-ttu-id="19a01-148">Uma cadeia de caracteres que especifica um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="19a01-148">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="19a01-149">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="19a01-149">privacyNoticeVersion</span></span>|<span data-ttu-id="19a01-150">Um inteiro que especifica a versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="19a01-150">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="19a01-151">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="19a01-151">proxyAddress</span></span>|<span data-ttu-id="19a01-152">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="19a01-152">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="19a01-153">Se `useDefaultWebProxy` for `true` , essa configuração deverá ser `null` .</span><span class="sxs-lookup"><span data-stu-id="19a01-153">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="19a01-154">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="19a01-154">The default is `null`.</span></span>|
|<span data-ttu-id="19a01-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="19a01-155">receiveTimeout</span></span>|<span data-ttu-id="19a01-156">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="19a01-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="19a01-157">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="19a01-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19a01-158">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="19a01-158">The default is 00:10:00.</span></span>|
|<span data-ttu-id="19a01-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="19a01-159">sendTimeout</span></span>|<span data-ttu-id="19a01-160">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="19a01-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="19a01-161">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="19a01-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19a01-162">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19a01-162">The default is 00:01:00.</span></span>|
|<span data-ttu-id="19a01-163">codificação de</span><span class="sxs-lookup"><span data-stu-id="19a01-163">textEncoding</span></span>|<span data-ttu-id="19a01-164">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-164">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="19a01-165">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="19a01-165">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="19a01-166">-BigEndianUnicode: codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="19a01-166">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="19a01-167">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="19a01-167">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="19a01-168">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="19a01-168">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="19a01-169">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="19a01-169">The default is UTF8.</span></span> <span data-ttu-id="19a01-170">Este atributo é do tipo <xref:System.Text.Encoding> ..</span><span class="sxs-lookup"><span data-stu-id="19a01-170">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="19a01-171">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="19a01-171">transactionFlow</span></span>|<span data-ttu-id="19a01-172">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="19a01-172">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="19a01-173">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="19a01-173">The default is `false`.</span></span>|
|<span data-ttu-id="19a01-174">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="19a01-174">useDefaultWebProxy</span></span>|<span data-ttu-id="19a01-175">Um valor booliano que indica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="19a01-175">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="19a01-176">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true` .</span><span class="sxs-lookup"><span data-stu-id="19a01-176">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="19a01-177">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="19a01-177">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="19a01-178">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="19a01-178">Child Elements</span></span>

|<span data-ttu-id="19a01-179">Elemento</span><span class="sxs-lookup"><span data-stu-id="19a01-179">Element</span></span>|<span data-ttu-id="19a01-180">Descrição</span><span class="sxs-lookup"><span data-stu-id="19a01-180">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="19a01-181">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="19a01-181">Defines the security settings for the message.</span></span> <span data-ttu-id="19a01-182">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="19a01-182">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="19a01-183">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-183">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="19a01-184">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="19a01-184">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="19a01-185">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="19a01-185">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="19a01-186">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="19a01-186">Parent Elements</span></span>

|<span data-ttu-id="19a01-187">Elemento</span><span class="sxs-lookup"><span data-stu-id="19a01-187">Element</span></span>|<span data-ttu-id="19a01-188">Descrição</span><span class="sxs-lookup"><span data-stu-id="19a01-188">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="19a01-189">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="19a01-189">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="19a01-190">Comentários</span><span class="sxs-lookup"><span data-stu-id="19a01-190">Remarks</span></span>

<span data-ttu-id="19a01-191">A Federação é a capacidade de compartilhar identidades em vários sistemas para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="19a01-191">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="19a01-192">Essas identidades podem se referir a usuários ou a computadores.</span><span class="sxs-lookup"><span data-stu-id="19a01-192">These identities can refer to users or to machines.</span></span> <span data-ttu-id="19a01-193">O HTTP federado dá suporte à segurança SOAP, bem como à segurança de modo misto, mas não dá suporte exclusivamente ao uso da segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="19a01-193">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="19a01-194">Essa associação fornece suporte de Windows Communication Foundation (WCF) para o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="19a01-194">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="19a01-195">Os serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="19a01-195">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="19a01-196">Associações consistem em uma pilha de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="19a01-196">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="19a01-197">A pilha de elementos de associação em</span><span class="sxs-lookup"><span data-stu-id="19a01-197">The stack of binding elements in</span></span>

<span data-ttu-id="19a01-198">`wsFederationHttpBinding`é o mesmo que o contido em`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="19a01-198">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="19a01-199">Quando [\<security>](security-of-wsfederationhttpbinding.md) é definido como o valor padrão de <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="19a01-199">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="19a01-200">O `wsFederationHttpBinding` controla os detalhes das configurações de segurança da mensagem no [\<message>](message-element-of-wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="19a01-200">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="19a01-201">Observe que o [\<security>](security-of-wsfederationhttpbinding.md) elemento fornece acesso Get somente quando a segurança usada pela associação não pode ser alterada depois que a associação é criada.</span><span class="sxs-lookup"><span data-stu-id="19a01-201">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="19a01-202">O `wsFederationHttpBinding` também fornece um atributo privacyNoticeAt para definir e recuperar o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="19a01-202">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="19a01-203">Manter a política segura é especialmente importante em cenários de Federação.</span><span class="sxs-lookup"><span data-stu-id="19a01-203">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="19a01-204">A recomendação é usar alguma forma de segurança, como HTTPS, para proteger a política contra usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="19a01-204">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="19a01-205">Em cenários de Federação que usam essa associação, a política de serviço potencialmente tem informações importantes, como a chave a ser usada para criptografar o token emitido (SAML), o tipo de declarações a serem colocadas no token e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="19a01-205">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="19a01-206">Se essa política for violada, um invasor poderá descobrir a chave do token emitido que leva à violação adicional, à divulgação de informações e a outros comportamentos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="19a01-206">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="19a01-207">Para ajudar a evitar isso, a política deve ser obtida com segurança (por exemplo, usando HTTPS) do serviço.</span><span class="sxs-lookup"><span data-stu-id="19a01-207">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="19a01-208">Para obter mais informações sobre essa ligação, consulte [como: criar um WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="19a01-208">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="19a01-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19a01-209">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
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

## <a name="see-also"></a><span data-ttu-id="19a01-210">Confira também</span><span class="sxs-lookup"><span data-stu-id="19a01-210">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="19a01-211">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="19a01-211">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="19a01-212">Associações</span><span class="sxs-lookup"><span data-stu-id="19a01-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="19a01-213">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="19a01-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="19a01-214">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="19a01-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
