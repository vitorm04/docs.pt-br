---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: e6215465acbf9bb94298d282d15f8735a0e20c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673076"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="8ea77-101">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8ea77-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="8ea77-102">Uma associação segura e interoperável que deriva [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e suporta segurança federada.</span><span class="sxs-lookup"><span data-stu-id="8ea77-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a><span data-ttu-id="8ea77-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ea77-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8ea77-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8ea77-104">Attributes and Elements</span></span>

<span data-ttu-id="8ea77-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8ea77-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ea77-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="8ea77-106">Attributes</span></span>

|<span data-ttu-id="8ea77-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="8ea77-107">Attribute</span></span>|<span data-ttu-id="8ea77-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ea77-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="8ea77-109">Um valor que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="8ea77-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="8ea77-110">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8ea77-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="8ea77-111">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="8ea77-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8ea77-112">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ea77-113">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="8ea77-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="8ea77-114">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="8ea77-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="8ea77-115">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="8ea77-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="8ea77-116">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="8ea77-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="8ea77-117">O tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="8ea77-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="8ea77-118">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="8ea77-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="8ea77-119">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="8ea77-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="8ea77-120">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="8ea77-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="8ea77-121">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="8ea77-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="8ea77-122">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="8ea77-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="8ea77-123">O tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="8ea77-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="8ea77-124">O remetente de uma mensagem que exceda esse limite recebe uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ea77-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="8ea77-125">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ea77-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8ea77-126">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="8ea77-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="8ea77-127">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8ea77-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="8ea77-128">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8ea77-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8ea77-129">-Texto: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="8ea77-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="8ea77-130">-Mtom: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="8ea77-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="8ea77-131">O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="8ea77-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="8ea77-132">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="8ea77-133">O nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="8ea77-133">The configuration name of the binding.</span></span> <span data-ttu-id="8ea77-134">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="8ea77-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8ea77-135">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="8ea77-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8ea77-136">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8ea77-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="8ea77-137">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="8ea77-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8ea77-138">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ea77-139">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="8ea77-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="8ea77-140">Um URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="8ea77-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="8ea77-141">A versão do aviso de privacidade atual.</span><span class="sxs-lookup"><span data-stu-id="8ea77-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="8ea77-142">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ea77-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="8ea77-143">Se `useDefaultWebProxy` está `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="8ea77-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="8ea77-144">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="8ea77-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="8ea77-145">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="8ea77-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8ea77-146">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ea77-147">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="8ea77-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="8ea77-148">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="8ea77-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8ea77-149">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8ea77-150">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="8ea77-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="8ea77-151">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8ea77-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="8ea77-152">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8ea77-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8ea77-153">-   BigEndianUnicode: Big Endian codificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="8ea77-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="8ea77-154">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="8ea77-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="8ea77-155">-   UTF8: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="8ea77-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="8ea77-156">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="8ea77-156">The default is UTF8.</span></span> <span data-ttu-id="8ea77-157">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="8ea77-158">Um valor que especifica se a associação dá suporte a fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="8ea77-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="8ea77-159">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8ea77-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="8ea77-160">Um valor que indica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="8ea77-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="8ea77-161">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`.</span><span class="sxs-lookup"><span data-stu-id="8ea77-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="8ea77-162">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="8ea77-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8ea77-163">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8ea77-163">Child Elements</span></span>

|<span data-ttu-id="8ea77-164">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ea77-164">Element</span></span>|<span data-ttu-id="8ea77-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ea77-165">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ea77-166">\<security></span><span class="sxs-lookup"><span data-stu-id="8ea77-166">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="8ea77-167">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8ea77-167">Defines the security settings for the message.</span></span> <span data-ttu-id="8ea77-168">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-168">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="8ea77-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ea77-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="8ea77-170">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="8ea77-170">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8ea77-171">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8ea77-171">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="8ea77-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8ea77-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="8ea77-173">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="8ea77-173">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8ea77-174">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8ea77-174">Parent Elements</span></span>

|<span data-ttu-id="8ea77-175">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ea77-175">Element</span></span>|<span data-ttu-id="8ea77-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ea77-176">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ea77-177">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8ea77-177">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="8ea77-178">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8ea77-178">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ea77-179">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ea77-179">Remarks</span></span>

<span data-ttu-id="8ea77-180">Federação é a capacidade de compartilhar identidades em várias empresas ou domínios de confiança para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="8ea77-180">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="8ea77-181">Ele usa o protocolo WS-Trust para mapear a representação de identidade de domínio de uma relação de confiança para outro.</span><span class="sxs-lookup"><span data-stu-id="8ea77-181">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="8ea77-182">Associação de HTTP federada dá suporte a segurança SOAP, bem como a segurança de modo misto, mas não oferece suporte a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="8ea77-182">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="8ea77-183">Serviços configurados com essa associação devem usar o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ea77-183">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="8ea77-184">Para obter mais informações, consulte [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8ea77-184">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="8ea77-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ea77-185">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ea77-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ea77-186">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="8ea77-187">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8ea77-187">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [<span data-ttu-id="8ea77-188">Associações</span><span class="sxs-lookup"><span data-stu-id="8ea77-188">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8ea77-189">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8ea77-189">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8ea77-190">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8ea77-190">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8ea77-191">\<binding></span><span class="sxs-lookup"><span data-stu-id="8ea77-191">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
