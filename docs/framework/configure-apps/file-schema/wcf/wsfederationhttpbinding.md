---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 0f4a0c03d0bb69eeb61efacdd2b1e9fe64d2adce
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262735"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="f634e-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f634e-101">\<wsFederationHttpBinding></span></span>
<span data-ttu-id="f634e-102">Define uma associação que dá suporte a WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f634e-102">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="f634e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f634e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f634e-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f634e-104">\<bindings></span></span>  
<span data-ttu-id="f634e-105">elemento FederationBinding</span><span class="sxs-lookup"><span data-stu-id="f634e-105">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f634e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f634e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f634e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f634e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f634e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f634e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f634e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f634e-109">Attributes</span></span>  
  
|<span data-ttu-id="f634e-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="f634e-110">Attribute</span></span>|<span data-ttu-id="f634e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f634e-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f634e-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="f634e-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="f634e-113">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="f634e-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="f634e-114">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f634e-114">The default is `false`.</span></span>|  
|<span data-ttu-id="f634e-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f634e-115">closeTimeout</span></span>|<span data-ttu-id="f634e-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="f634e-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f634e-117">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f634e-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f634e-118">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f634e-118">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f634e-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f634e-119">hostnameComparisonMode</span></span>|<span data-ttu-id="f634e-120">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="f634e-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f634e-121">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="f634e-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f634e-122">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="f634e-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="f634e-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f634e-123">maxBufferPoolSize</span></span>|<span data-ttu-id="f634e-124">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="f634e-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f634e-125">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="f634e-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="f634e-126">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="f634e-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="f634e-127">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="f634e-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f634e-128">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="f634e-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f634e-129">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="f634e-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="f634e-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f634e-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="f634e-131">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f634e-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f634e-132">O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="f634e-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="f634e-133">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f634e-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f634e-134">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="f634e-134">The default is 65536.</span></span>|  
|<span data-ttu-id="f634e-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="f634e-135">messageEncoding</span></span>|<span data-ttu-id="f634e-136">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f634e-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="f634e-137">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f634e-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f634e-138">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="f634e-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="f634e-139">-Mtom: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="f634e-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="f634e-140">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="f634e-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="f634e-141">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="f634e-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="f634e-142">name</span><span class="sxs-lookup"><span data-stu-id="f634e-142">name</span></span>|<span data-ttu-id="f634e-143">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="f634e-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f634e-144">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="f634e-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f634e-145">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="f634e-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f634e-146">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f634e-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="f634e-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f634e-147">openTimeout</span></span>|<span data-ttu-id="f634e-148">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="f634e-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f634e-149">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f634e-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f634e-150">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f634e-150">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f634e-151">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="f634e-151">privactyNoticeAt</span></span>|<span data-ttu-id="f634e-152">Uma cadeia de caracteres que especifica um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="f634e-152">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="f634e-153">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="f634e-153">privactyNoticeVersion</span></span>|<span data-ttu-id="f634e-154">Um inteiro que especifica a versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="f634e-154">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="f634e-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="f634e-155">proxyAddress</span></span>|<span data-ttu-id="f634e-156">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="f634e-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="f634e-157">Se `useDefaultWebProxy` está `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f634e-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="f634e-158">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="f634e-158">The default is `null`.</span></span>|  
|<span data-ttu-id="f634e-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f634e-159">receiveTimeout</span></span>|<span data-ttu-id="f634e-160">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f634e-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f634e-161">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f634e-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f634e-162">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="f634e-162">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="f634e-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f634e-163">sendTimeout</span></span>|<span data-ttu-id="f634e-164">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f634e-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f634e-165">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f634e-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f634e-166">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="f634e-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f634e-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="f634e-167">textEncoding</span></span>|<span data-ttu-id="f634e-168">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f634e-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f634e-169">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f634e-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f634e-170">-   BigEndianUnicode: Unicode BigEndian de codificação.</span><span class="sxs-lookup"><span data-stu-id="f634e-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="f634e-171">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="f634e-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="f634e-172">-   UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="f634e-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="f634e-173">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="f634e-173">The default is UTF8.</span></span> <span data-ttu-id="f634e-174">Esse atributo é do tipo <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="f634e-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="f634e-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="f634e-175">transactionFlow</span></span>|<span data-ttu-id="f634e-176">Um valor booliano que especifica se a associação dá suporte a fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="f634e-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="f634e-177">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f634e-177">The default is `false`.</span></span>|  
|<span data-ttu-id="f634e-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="f634e-178">useDefaultWebProxy</span></span>|<span data-ttu-id="f634e-179">Um valor booliano que indica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="f634e-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="f634e-180">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`.</span><span class="sxs-lookup"><span data-stu-id="f634e-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="f634e-181">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="f634e-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f634e-182">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f634e-182">Child Elements</span></span>  
  
|<span data-ttu-id="f634e-183">Elemento</span><span class="sxs-lookup"><span data-stu-id="f634e-183">Element</span></span>|<span data-ttu-id="f634e-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="f634e-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f634e-185">\<security></span><span class="sxs-lookup"><span data-stu-id="f634e-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="f634e-186">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f634e-186">Defines the security settings for the message.</span></span> <span data-ttu-id="f634e-187">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f634e-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="f634e-188">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="f634e-188">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f634e-189">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f634e-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f634e-190">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f634e-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="f634e-191">reliableSession</span><span class="sxs-lookup"><span data-stu-id="f634e-191">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="f634e-192">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="f634e-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f634e-193">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f634e-193">Parent Elements</span></span>  
  
|<span data-ttu-id="f634e-194">Elemento</span><span class="sxs-lookup"><span data-stu-id="f634e-194">Element</span></span>|<span data-ttu-id="f634e-195">Descrição</span><span class="sxs-lookup"><span data-stu-id="f634e-195">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f634e-196">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f634e-196">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="f634e-197">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="f634e-197">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f634e-198">Comentários</span><span class="sxs-lookup"><span data-stu-id="f634e-198">Remarks</span></span>  
 <span data-ttu-id="f634e-199">Federação é a capacidade de compartilhar identidades em vários sistemas para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="f634e-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="f634e-200">Essas identidades podem fazer referência aos usuários ou computadores.</span><span class="sxs-lookup"><span data-stu-id="f634e-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="f634e-201">Dá suporte a HTTP federado a segurança SOAP, bem como a segurança de modo misto, mas ele não oferece suporte ao uso exclusivamente a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="f634e-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="f634e-202">Essa associação fornece suporte do Windows Communication Foundation (WCF) para o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f634e-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="f634e-203">Serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="f634e-203">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="f634e-204">Associações consistem em uma pilha de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="f634e-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="f634e-205">A pilha de elementos de associação</span><span class="sxs-lookup"><span data-stu-id="f634e-205">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="f634e-206">`wsFederationHttpBinding` é o mesmo que contido em `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="f634e-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="f634e-207">Quando [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) é definido como o valor padrão de <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="f634e-207">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="f634e-208">O `wsFederationHttpBinding` controla os detalhes das configurações de segurança de mensagem no [ \<mensagem >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f634e-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="f634e-209">Observe que o [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) elemento fornece obter acesso somente à medida que o usado pela associação de segurança não pode ser alterada depois que a associação é criada.</span><span class="sxs-lookup"><span data-stu-id="f634e-209">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="f634e-210">O `wsFederationHttpBinding` também fornece um atributo privactyNoticeAt para definir e recuperar o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="f634e-210">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="f634e-211">Manter a política de segurança é especialmente importante em cenários de Federação.</span><span class="sxs-lookup"><span data-stu-id="f634e-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="f634e-212">A recomendação é usar alguma forma de segurança, como HTTPS, para proteger a política de usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="f634e-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="f634e-213">Em cenários de Federação usando essa associação, a política de serviço potencialmente tem informações importantes, como a chave a ser usada para criptografar o token emitido (SAML), o tipo de declarações para colocar no token e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f634e-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="f634e-214">Se essa política for violada, um invasor poderia descobrir a chave do token emitido, levando a mais de violação, divulgação de informações e outros comportamentos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="f634e-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="f634e-215">Para evitar isso, a política deve ser obtida com segurança (por exemplo usando HTTPS) do serviço.</span><span class="sxs-lookup"><span data-stu-id="f634e-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="f634e-216">Para obter mais informações sobre essa associação, consulte [como: Criar um WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f634e-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f634e-217">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f634e-217">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f634e-218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f634e-218">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="f634e-219">Como: Criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f634e-219">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="f634e-220">Associações</span><span class="sxs-lookup"><span data-stu-id="f634e-220">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f634e-221">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f634e-221">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f634e-222">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f634e-222">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f634e-223">\<binding></span><span class="sxs-lookup"><span data-stu-id="f634e-223">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
