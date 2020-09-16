---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 102e220ad01410568a18ce4ea6fac06ca8c15230
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558726"
---
# \<ws2007HttpBinding>
<span data-ttu-id="899b7-101">Define uma associação interoperável que fornece suporte para as versões corretas <xref:System.ServiceModel.WSHttpBinding.Security%2A> dos <xref:System.ServiceModel.ReliableSession> elementos de <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> associação, e.</span><span class="sxs-lookup"><span data-stu-id="899b7-101">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="899b7-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="899b7-102">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="899b7-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="899b7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="899b7-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="899b7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="899b7-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="899b7-105">Attributes</span></span>  
  
|<span data-ttu-id="899b7-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="899b7-106">Attribute</span></span>|<span data-ttu-id="899b7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="899b7-107">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="899b7-108">Um valor que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="899b7-108">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="899b7-109">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="899b7-109">The default is `false`.</span></span><br /><br /> <span data-ttu-id="899b7-110">Você pode usar essa propriedade ao interagir com os serviços Web do ASP.NET (ASMX) que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="899b7-110">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="899b7-111">Isso garante que os cookies que o servidor retorna sejam copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="899b7-111">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="899b7-112">Um valor que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="899b7-112">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="899b7-113">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="899b7-113">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="899b7-114">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="899b7-114">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="899b7-115">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="899b7-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="899b7-116">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="899b7-116">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="899b7-117">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs (identificadores de recurso uniforme).</span><span class="sxs-lookup"><span data-stu-id="899b7-117">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="899b7-118">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode> , que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="899b7-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="899b7-119">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="899b7-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="899b7-120">O tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="899b7-120">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="899b7-121">O padrão é 524.288 bytes (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="899b7-121">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="899b7-122">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="899b7-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="899b7-123">Criar e destruir buffers cada vez que eles são usados é caro, assim como a coleta de lixo para buffers.</span><span class="sxs-lookup"><span data-stu-id="899b7-123">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="899b7-124">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="899b7-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="899b7-125">Isso evita a sobrecarga na criação e destruição de buffers.</span><span class="sxs-lookup"><span data-stu-id="899b7-125">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="899b7-126">O tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que um canal configurado com essa associação, pode receber.</span><span class="sxs-lookup"><span data-stu-id="899b7-126">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="899b7-127">O remetente de uma mensagem que excede esse limite recebe uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="899b7-127">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="899b7-128">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="899b7-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="899b7-129">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="899b7-129">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="899b7-130">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="899b7-130">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="899b7-131">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="899b7-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="899b7-132">-   `Text`: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="899b7-132">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="899b7-133">-   `Mtom`: Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).</span><span class="sxs-lookup"><span data-stu-id="899b7-133">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="899b7-134">O padrão é `Text`.</span><span class="sxs-lookup"><span data-stu-id="899b7-134">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="899b7-135">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="899b7-135">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="899b7-136">O nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="899b7-136">The configuration name of the binding.</span></span> <span data-ttu-id="899b7-137">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="899b7-137">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="899b7-138">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="899b7-138">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="899b7-139">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="899b7-139">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="899b7-140">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="899b7-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="899b7-141">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="899b7-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="899b7-142">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="899b7-142">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="899b7-143">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="899b7-143">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="899b7-144">Se `useSystemWebProxy` for `true` , essa configuração deverá ser `null` .</span><span class="sxs-lookup"><span data-stu-id="899b7-144">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="899b7-145">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="899b7-145">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="899b7-146">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="899b7-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="899b7-147">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="899b7-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="899b7-148">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="899b7-148">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="899b7-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="899b7-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="899b7-150">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="899b7-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="899b7-151">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="899b7-151">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="899b7-152">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="899b7-152">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="899b7-153">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="899b7-153">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="899b7-154">-   `UnicodeFffeTextEncoding`: Codificação Big Endian Unicode.</span><span class="sxs-lookup"><span data-stu-id="899b7-154">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="899b7-155">-   `Utf16TextEncoding`: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="899b7-155">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="899b7-156">-   `Utf8TextEncoding`: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="899b7-156">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="899b7-157">O padrão é `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="899b7-157">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="899b7-158">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="899b7-158">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="899b7-159">Um valor que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="899b7-159">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="899b7-160">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="899b7-160">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="899b7-161">Um valor que especifica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="899b7-161">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="899b7-162">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="899b7-162">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="899b7-163">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="899b7-163">Child Elements</span></span>  
  
|<span data-ttu-id="899b7-164">Elemento</span><span class="sxs-lookup"><span data-stu-id="899b7-164">Element</span></span>|<span data-ttu-id="899b7-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="899b7-165">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="899b7-166">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="899b7-166">Defines the security settings for the binding.</span></span> <span data-ttu-id="899b7-167">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="899b7-167">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="899b7-168">Define as restrições sobre a complexidade das mensagens SOAP que os pontos de extremidade configurados com essa associação podem processar.</span><span class="sxs-lookup"><span data-stu-id="899b7-168">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="899b7-169">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="899b7-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="899b7-170">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="899b7-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="899b7-171">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="899b7-171">Parent Elements</span></span>  
  
|<span data-ttu-id="899b7-172">Elemento</span><span class="sxs-lookup"><span data-stu-id="899b7-172">Element</span></span>|<span data-ttu-id="899b7-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="899b7-173">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="899b7-174">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="899b7-174">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="899b7-175">Comentários</span><span class="sxs-lookup"><span data-stu-id="899b7-175">Remarks</span></span>  
 <span data-ttu-id="899b7-176">O `WS2007HttpBinding` adiciona uma associação fornecida pelo sistema semelhante a `WSHttpBinding` , mas usa a organização para o avanço das versões padrão do Oasis (padrões de informações estruturadas) dos protocolos ReliableSession, Security e TransactionFlow.</span><span class="sxs-lookup"><span data-stu-id="899b7-176">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="899b7-177">Nenhuma alteração no modelo de objeto ou nas configurações padrão é necessária ao usar essa associação.</span><span class="sxs-lookup"><span data-stu-id="899b7-177">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="899b7-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="899b7-178">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="899b7-179">Confira também</span><span class="sxs-lookup"><span data-stu-id="899b7-179">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="899b7-180">Associações</span><span class="sxs-lookup"><span data-stu-id="899b7-180">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="899b7-181">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="899b7-181">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="899b7-182">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="899b7-182">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
