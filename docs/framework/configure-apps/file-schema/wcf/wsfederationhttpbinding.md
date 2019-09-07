---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: a605d3241ec62f5648e3439b327153f3fb4590df
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399028"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="c0e2e-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c0e2e-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="c0e2e-102">Define uma associação que oferece suporte ao WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="c0e2e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0e2e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0e2e-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0e2e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0e2e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c0e2e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c0e2e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> wsFederationHttpBinding**</span><span class="sxs-lookup"><span data-stu-id="c0e2e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="c0e2e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0e2e-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c0e2e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0e2e-108">Attributes and Elements</span></span>

<span data-ttu-id="c0e2e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0e2e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0e2e-110">Attributes</span></span>

|<span data-ttu-id="c0e2e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c0e2e-111">Attribute</span></span>|<span data-ttu-id="c0e2e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e2e-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c0e2e-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c0e2e-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="c0e2e-114">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="c0e2e-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-115">The default is `false`.</span></span>|
|<span data-ttu-id="c0e2e-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="c0e2e-116">closeTimeout</span></span>|<span data-ttu-id="c0e2e-117">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c0e2e-118">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0e2e-119">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-119">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c0e2e-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c0e2e-120">hostnameComparisonMode</span></span>|<span data-ttu-id="c0e2e-121">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="c0e2e-122">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="c0e2e-123">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="c0e2e-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c0e2e-124">maxBufferPoolSize</span></span>|<span data-ttu-id="c0e2e-125">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c0e2e-126">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="c0e2e-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c0e2e-127">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="c0e2e-128">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c0e2e-129">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c0e2e-130">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="c0e2e-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c0e2e-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="c0e2e-132">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c0e2e-133">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="c0e2e-134">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c0e2e-135">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-135">The default is 65536.</span></span>|
|<span data-ttu-id="c0e2e-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="c0e2e-136">messageEncoding</span></span>|<span data-ttu-id="c0e2e-137">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="c0e2e-138">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0e2e-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c0e2e-139">Texto Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="c0e2e-140">MTOM Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).</span><span class="sxs-lookup"><span data-stu-id="c0e2e-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="c0e2e-141">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="c0e2e-142">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="c0e2e-143">name</span><span class="sxs-lookup"><span data-stu-id="c0e2e-143">name</span></span>|<span data-ttu-id="c0e2e-144">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c0e2e-145">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c0e2e-146">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0e2e-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c0e2e-147">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c0e2e-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="c0e2e-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c0e2e-148">openTimeout</span></span>|<span data-ttu-id="c0e2e-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c0e2e-150">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0e2e-151">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-151">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c0e2e-152">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="c0e2e-152">privacyNoticeAt</span></span>|<span data-ttu-id="c0e2e-153">Uma cadeia de caracteres que especifica um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-153">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="c0e2e-154">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="c0e2e-154">privacyNoticeVersion</span></span>|<span data-ttu-id="c0e2e-155">Um inteiro que especifica a versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-155">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="c0e2e-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="c0e2e-156">proxyAddress</span></span>|<span data-ttu-id="c0e2e-157">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="c0e2e-158">Se `useDefaultWebProxy` `null`for `true`, essa configuração deverá ser.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="c0e2e-159">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-159">The default is `null`.</span></span>|
|<span data-ttu-id="c0e2e-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c0e2e-160">receiveTimeout</span></span>|<span data-ttu-id="c0e2e-161">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c0e2e-162">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0e2e-163">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-163">The default is 00:10:00.</span></span>|
|<span data-ttu-id="c0e2e-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c0e2e-164">sendTimeout</span></span>|<span data-ttu-id="c0e2e-165">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c0e2e-166">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0e2e-167">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-167">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c0e2e-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="c0e2e-168">textEncoding</span></span>|<span data-ttu-id="c0e2e-169">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c0e2e-170">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0e2e-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c0e2e-171">BigEndianUnicode Codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="c0e2e-172">Unicode codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="c0e2e-173">UTF8 codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="c0e2e-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="c0e2e-174">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-174">The default is UTF8.</span></span> <span data-ttu-id="c0e2e-175">Este atributo é do tipo <xref:System.Text.Encoding>..</span><span class="sxs-lookup"><span data-stu-id="c0e2e-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="c0e2e-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="c0e2e-176">transactionFlow</span></span>|<span data-ttu-id="c0e2e-177">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="c0e2e-178">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-178">The default is `false`.</span></span>|
|<span data-ttu-id="c0e2e-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c0e2e-179">useDefaultWebProxy</span></span>|<span data-ttu-id="c0e2e-180">Um valor booliano que indica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="c0e2e-181">O endereço de proxy deve `null` ser (ou seja, não definido) se esse atributo `true`for.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="c0e2e-182">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-182">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c0e2e-183">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0e2e-183">Child Elements</span></span>

|<span data-ttu-id="c0e2e-184">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0e2e-184">Element</span></span>|<span data-ttu-id="c0e2e-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e2e-185">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0e2e-186">\<security></span><span class="sxs-lookup"><span data-stu-id="c0e2e-186">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="c0e2e-187">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-187">Defines the security settings for the message.</span></span> <span data-ttu-id="c0e2e-188">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="c0e2e-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c0e2e-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="c0e2e-190">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c0e2e-191">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="c0e2e-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c0e2e-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="c0e2e-193">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0e2e-194">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0e2e-194">Parent Elements</span></span>

|<span data-ttu-id="c0e2e-195">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0e2e-195">Element</span></span>|<span data-ttu-id="c0e2e-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e2e-196">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0e2e-197">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c0e2e-197">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c0e2e-198">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-198">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0e2e-199">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0e2e-199">Remarks</span></span>

<span data-ttu-id="c0e2e-200">A Federação é a capacidade de compartilhar identidades em vários sistemas para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="c0e2e-201">Essas identidades podem se referir a usuários ou a computadores.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="c0e2e-202">O HTTP federado dá suporte à segurança SOAP, bem como à segurança de modo misto, mas não dá suporte exclusivamente ao uso da segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="c0e2e-203">Essa associação fornece suporte de Windows Communication Foundation (WCF) para o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="c0e2e-204">Os serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-204">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="c0e2e-205">Associações consistem em uma pilha de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="c0e2e-206">A pilha de elementos de associação em</span><span class="sxs-lookup"><span data-stu-id="c0e2e-206">The stack of binding elements in</span></span>

<span data-ttu-id="c0e2e-207">`wsFederationHttpBinding`é o mesmo que o contido em`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="c0e2e-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="c0e2e-208"><xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> [ quando\<> de segurança](security-of-wsfederationhttpbinding.md) é definido como o valor padrão de.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-208">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="c0e2e-209">O `wsFederationHttpBinding` controla os detalhes das configurações de segurança da mensagem na [ \<> de mensagens](message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c0e2e-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="c0e2e-210">Observe que o elemento de [ \<> de segurança](security-of-wsfederationhttpbinding.md) fornece acesso Get somente quando a segurança usada pela associação não pode ser alterada depois que a associação é criada.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-210">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="c0e2e-211">O `wsFederationHttpBinding` também fornece um atributo privacyNoticeAt para definir e recuperar o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-211">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="c0e2e-212">Manter a política segura é especialmente importante em cenários de Federação.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="c0e2e-213">A recomendação é usar alguma forma de segurança, como HTTPS, para proteger a política contra usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="c0e2e-214">Em cenários de Federação que usam essa associação, a política de serviço potencialmente tem informações importantes, como a chave a ser usada para criptografar o token emitido (SAML), o tipo de declarações a serem colocadas no token e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="c0e2e-215">Se essa política for violada, um invasor poderá descobrir a chave do token emitido que leva à violação adicional, à divulgação de informações e a outros comportamentos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="c0e2e-216">Para ajudar a evitar isso, a política deve ser obtida com segurança (por exemplo, usando HTTPS) do serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e2e-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="c0e2e-217">Para obter mais informações sobre essa ligação, [consulte Como: Crie um WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c0e2e-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0e2e-218">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0e2e-218">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c0e2e-219">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0e2e-219">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="c0e2e-220">Como: Criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c0e2e-220">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c0e2e-221">Associações</span><span class="sxs-lookup"><span data-stu-id="c0e2e-221">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c0e2e-222">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c0e2e-222">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c0e2e-223">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c0e2e-223">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c0e2e-224">\<binding></span><span class="sxs-lookup"><span data-stu-id="c0e2e-224">\<binding></span></span>](../../../misc/binding.md)
