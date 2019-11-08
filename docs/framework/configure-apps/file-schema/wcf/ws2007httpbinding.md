---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2f8cff87280f08af0c426b7a726949b9a9c40197
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732518"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="086cb-101">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="086cb-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="086cb-102">Define uma associação interoperável que fornece suporte para as versões corretas dos elementos de associação <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>e <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.</span><span class="sxs-lookup"><span data-stu-id="086cb-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
<span data-ttu-id="086cb-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="086cb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="086cb-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="086cb-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="086cb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="086cb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="086cb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="086cb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="086cb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="086cb-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="086cb-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="086cb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="086cb-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="086cb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="086cb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="086cb-110">Attributes</span></span>  
  
|<span data-ttu-id="086cb-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="086cb-111">Attribute</span></span>|<span data-ttu-id="086cb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="086cb-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="086cb-113">Um valor que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="086cb-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="086cb-114">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="086cb-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="086cb-115">Você pode usar essa propriedade ao interagir com os serviços Web do ASP.NET (ASMX) que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="086cb-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="086cb-116">Isso garante que os cookies que o servidor retorna sejam copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="086cb-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="086cb-117">Um valor que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="086cb-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="086cb-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="086cb-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="086cb-119">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="086cb-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="086cb-120">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="086cb-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="086cb-121">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="086cb-121">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="086cb-122">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs (identificadores de recurso uniforme).</span><span class="sxs-lookup"><span data-stu-id="086cb-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="086cb-123">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="086cb-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="086cb-124">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="086cb-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="086cb-125">O tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="086cb-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="086cb-126">O padrão é 524.288 bytes (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="086cb-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="086cb-127">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="086cb-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="086cb-128">Criar e destruir buffers cada vez que eles são usados é caro, assim como a coleta de lixo para buffers.</span><span class="sxs-lookup"><span data-stu-id="086cb-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="086cb-129">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="086cb-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="086cb-130">Isso evita a sobrecarga na criação e destruição de buffers.</span><span class="sxs-lookup"><span data-stu-id="086cb-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="086cb-131">O tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que um canal configurado com essa associação, pode receber.</span><span class="sxs-lookup"><span data-stu-id="086cb-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="086cb-132">O remetente de uma mensagem que excede esse limite recebe uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="086cb-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="086cb-133">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="086cb-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="086cb-134">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="086cb-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="086cb-135">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="086cb-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="086cb-136">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="086cb-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="086cb-137">-   `Text`: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="086cb-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="086cb-138">-   `Mtom`: Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).</span><span class="sxs-lookup"><span data-stu-id="086cb-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="086cb-139">O padrão é `Text`.</span><span class="sxs-lookup"><span data-stu-id="086cb-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="086cb-140">Este atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="086cb-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="086cb-141">O nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="086cb-141">The configuration name of the binding.</span></span> <span data-ttu-id="086cb-142">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="086cb-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="086cb-143">A partir do [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="086cb-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="086cb-144">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="086cb-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="086cb-145">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="086cb-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="086cb-146">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="086cb-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="086cb-147">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="086cb-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="086cb-148">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="086cb-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="086cb-149">Se `useSystemWebProxy` for `true`, essa configuração deverá ser `null`.</span><span class="sxs-lookup"><span data-stu-id="086cb-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="086cb-150">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="086cb-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="086cb-151">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="086cb-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="086cb-152">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="086cb-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="086cb-153">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="086cb-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="086cb-154">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="086cb-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="086cb-155">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="086cb-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="086cb-156">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="086cb-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="086cb-157">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="086cb-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="086cb-158">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="086cb-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="086cb-159">-   `UnicodeFffeTextEncoding`: codificação Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="086cb-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="086cb-160">-   `Utf16TextEncoding`: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="086cb-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="086cb-161">-   `Utf8TextEncoding`: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="086cb-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="086cb-162">O padrão é `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="086cb-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="086cb-163">Este atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="086cb-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="086cb-164">Um valor que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="086cb-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="086cb-165">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="086cb-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="086cb-166">Um valor que especifica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="086cb-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="086cb-167">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="086cb-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="086cb-168">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="086cb-168">Child Elements</span></span>  
  
|<span data-ttu-id="086cb-169">Elemento</span><span class="sxs-lookup"><span data-stu-id="086cb-169">Element</span></span>|<span data-ttu-id="086cb-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="086cb-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="086cb-171">\<Security ></span><span class="sxs-lookup"><span data-stu-id="086cb-171">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="086cb-172">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="086cb-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="086cb-173">Este elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="086cb-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="086cb-174">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="086cb-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="086cb-175">Define as restrições sobre a complexidade das mensagens SOAP que os pontos de extremidade configurados com essa associação podem processar.</span><span class="sxs-lookup"><span data-stu-id="086cb-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="086cb-176">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="086cb-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="086cb-177">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="086cb-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="086cb-178">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="086cb-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="086cb-179">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="086cb-179">Parent Elements</span></span>  
  
|<span data-ttu-id="086cb-180">Elemento</span><span class="sxs-lookup"><span data-stu-id="086cb-180">Element</span></span>|<span data-ttu-id="086cb-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="086cb-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="086cb-182">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="086cb-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="086cb-183">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="086cb-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="086cb-184">Comentários</span><span class="sxs-lookup"><span data-stu-id="086cb-184">Remarks</span></span>  
 <span data-ttu-id="086cb-185">O `WS2007HttpBinding` adiciona uma associação fornecida pelo sistema semelhante a `WSHttpBinding` mas usa a organização para o avanço das versões padrão do OASIS (padrões de informações estruturadas) dos protocolos ReliableSession, Security e TransactionFlow.</span><span class="sxs-lookup"><span data-stu-id="086cb-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="086cb-186">Nenhuma alteração no modelo de objeto ou nas configurações padrão é necessária ao usar essa associação.</span><span class="sxs-lookup"><span data-stu-id="086cb-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="086cb-187">Exemplo</span><span class="sxs-lookup"><span data-stu-id="086cb-187">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="086cb-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="086cb-188">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="086cb-189">Associações</span><span class="sxs-lookup"><span data-stu-id="086cb-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="086cb-190">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="086cb-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="086cb-191">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="086cb-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="086cb-192">\<binding ></span><span class="sxs-lookup"><span data-stu-id="086cb-192">\<binding></span></span>](bindings.md)
