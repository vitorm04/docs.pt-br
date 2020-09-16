---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: fe9ab2e19706a5d295b5916aeb818621d1132c11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558765"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="562e1-101">Uma associação segura e interoperável que deriva de [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) e dá suporte à segurança federada.</span><span class="sxs-lookup"><span data-stu-id="562e1-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="562e1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="562e1-102">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
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
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="562e1-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="562e1-103">Attributes and Elements</span></span>

<span data-ttu-id="562e1-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="562e1-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="562e1-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="562e1-105">Attributes</span></span>

|<span data-ttu-id="562e1-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="562e1-106">Attribute</span></span>|<span data-ttu-id="562e1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="562e1-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="562e1-108">Um valor que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="562e1-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="562e1-109">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="562e1-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="562e1-110">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="562e1-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="562e1-111">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="562e1-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="562e1-112">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="562e1-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="562e1-113">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="562e1-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="562e1-114">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode> , que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="562e1-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="562e1-115">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="562e1-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="562e1-116">O tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="562e1-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="562e1-117">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="562e1-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="562e1-118">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="562e1-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="562e1-119">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="562e1-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="562e1-120">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="562e1-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="562e1-121">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="562e1-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="562e1-122">O tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="562e1-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="562e1-123">O remetente de uma mensagem que excede esse limite recebe uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="562e1-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="562e1-124">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="562e1-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="562e1-125">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="562e1-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="562e1-126">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="562e1-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="562e1-127">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="562e1-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="562e1-128">-Text: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="562e1-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="562e1-129">-MTOM: usar um codificador MTOM (mecanismo de organização de transmissão de mensagens) 1,0.</span><span class="sxs-lookup"><span data-stu-id="562e1-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="562e1-130">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="562e1-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="562e1-131">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="562e1-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="562e1-132">O nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="562e1-132">The configuration name of the binding.</span></span> <span data-ttu-id="562e1-133">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="562e1-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="562e1-134">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="562e1-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="562e1-135">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="562e1-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="562e1-136">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="562e1-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="562e1-137">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="562e1-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="562e1-138">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="562e1-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="562e1-139">Um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="562e1-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="562e1-140">A versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="562e1-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="562e1-141">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="562e1-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="562e1-142">Se `useDefaultWebProxy` for `true` , essa configuração deverá ser `null` .</span><span class="sxs-lookup"><span data-stu-id="562e1-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="562e1-143">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="562e1-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="562e1-144">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="562e1-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="562e1-145">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="562e1-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="562e1-146">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="562e1-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="562e1-147">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="562e1-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="562e1-148">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="562e1-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="562e1-149">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="562e1-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="562e1-150">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="562e1-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="562e1-151">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="562e1-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="562e1-152">-BigEndianUnicode: codificação Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="562e1-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="562e1-153">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="562e1-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="562e1-154">-UTF8: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="562e1-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="562e1-155">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="562e1-155">The default is UTF8.</span></span> <span data-ttu-id="562e1-156">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="562e1-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="562e1-157">Um valor que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="562e1-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="562e1-158">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="562e1-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="562e1-159">Um valor que indica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="562e1-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="562e1-160">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true` .</span><span class="sxs-lookup"><span data-stu-id="562e1-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="562e1-161">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="562e1-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="562e1-162">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="562e1-162">Child Elements</span></span>

|<span data-ttu-id="562e1-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="562e1-163">Element</span></span>|<span data-ttu-id="562e1-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="562e1-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="562e1-165">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="562e1-165">Defines the security settings for the message.</span></span> <span data-ttu-id="562e1-166">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="562e1-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="562e1-167">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="562e1-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="562e1-168">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="562e1-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="562e1-169">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="562e1-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="562e1-170">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="562e1-170">Parent Elements</span></span>

|<span data-ttu-id="562e1-171">Elemento</span><span class="sxs-lookup"><span data-stu-id="562e1-171">Element</span></span>|<span data-ttu-id="562e1-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="562e1-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="562e1-173">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="562e1-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="562e1-174">Comentários</span><span class="sxs-lookup"><span data-stu-id="562e1-174">Remarks</span></span>

<span data-ttu-id="562e1-175">A Federação é a capacidade de compartilhar identidades em várias empresas ou domínios de confiança para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="562e1-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="562e1-176">Ele usa o protocolo WS-Trust para mapear a representação de identidade de um domínio de confiança para outro.</span><span class="sxs-lookup"><span data-stu-id="562e1-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="562e1-177">A associação HTTP federada dá suporte à segurança SOAP, bem como à segurança de modo misto, mas não dá suporte à segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="562e1-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="562e1-178">Os serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="562e1-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="562e1-179">Para obter mais informações, consulte [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="562e1-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="562e1-180">Exemplo</span><span class="sxs-lookup"><span data-stu-id="562e1-180">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
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

## <a name="see-also"></a><span data-ttu-id="562e1-181">Confira também</span><span class="sxs-lookup"><span data-stu-id="562e1-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="562e1-182">Associações</span><span class="sxs-lookup"><span data-stu-id="562e1-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="562e1-183">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="562e1-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="562e1-184">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="562e1-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
