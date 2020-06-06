---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: a71ad2a2279eabbcf917df58d7bedec0e728f9e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140397"
---
# \<wsHttpBinding>
<span data-ttu-id="99cc8-101">Define uma associação segura, confiável e interoperável adequada para contratos de serviço não duplex.</span><span class="sxs-lookup"><span data-stu-id="99cc8-101">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="99cc8-102">A associação implementa as seguintes especificações: WS-Reliable Messaging for fiabilidade e WS-Security para segurança e autenticação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="99cc8-102">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="99cc8-103">O transporte é HTTP e a codificação de mensagem é codificação de texto/XML.</span><span class="sxs-lookup"><span data-stu-id="99cc8-103">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="99cc8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99cc8-104">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
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
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99cc8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99cc8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="99cc8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="99cc8-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99cc8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="99cc8-107">Attributes</span></span>  
  
|<span data-ttu-id="99cc8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="99cc8-108">Attribute</span></span>|<span data-ttu-id="99cc8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="99cc8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99cc8-110">allowCookies</span><span class="sxs-lookup"><span data-stu-id="99cc8-110">allowCookies</span></span>|<span data-ttu-id="99cc8-111">Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="99cc8-111">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="99cc8-112">O padrão é false.</span><span class="sxs-lookup"><span data-stu-id="99cc8-112">The default is false.</span></span><br /><br /> <span data-ttu-id="99cc8-113">Você pode usar essa propriedade ao interagir com serviços Web ASMX que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="99cc8-113">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="99cc8-114">Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="99cc8-114">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="99cc8-115">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="99cc8-115">bypassProxyOnLocal</span></span>|<span data-ttu-id="99cc8-116">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="99cc8-116">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="99cc8-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="99cc8-117">The default is `false`.</span></span>|  
|<span data-ttu-id="99cc8-118">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="99cc8-118">closeTimeout</span></span>|<span data-ttu-id="99cc8-119">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="99cc8-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="99cc8-120">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99cc8-121">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="99cc8-121">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="99cc8-122">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="99cc8-122">hostnameComparisonMode</span></span>|<span data-ttu-id="99cc8-123">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="99cc8-123">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="99cc8-124">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode> , que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="99cc8-124">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="99cc8-125">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="99cc8-125">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="99cc8-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="99cc8-126">maxBufferPoolSize</span></span>|<span data-ttu-id="99cc8-127">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-127">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="99cc8-128">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="99cc8-128">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="99cc8-129">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="99cc8-129">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="99cc8-130">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="99cc8-130">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="99cc8-131">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="99cc8-131">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="99cc8-132">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="99cc8-132">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="99cc8-133">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="99cc8-133">maxReceivedMessageSize</span></span>|<span data-ttu-id="99cc8-134">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-134">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="99cc8-135">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="99cc8-135">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="99cc8-136">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="99cc8-136">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="99cc8-137">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="99cc8-137">The default is 65536.</span></span>|  
|<span data-ttu-id="99cc8-138">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="99cc8-138">messageEncoding</span></span>|<span data-ttu-id="99cc8-139">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="99cc8-139">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="99cc8-140">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="99cc8-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="99cc8-141">-Text: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="99cc8-141">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="99cc8-142">-MTOM: usar um codificador MTOM (mecanismo de organização de transmissão de mensagens) 1,0.</span><span class="sxs-lookup"><span data-stu-id="99cc8-142">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="99cc8-143">-O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="99cc8-143">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="99cc8-144">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-144">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="99cc8-145">name</span><span class="sxs-lookup"><span data-stu-id="99cc8-145">name</span></span>|<span data-ttu-id="99cc8-146">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="99cc8-147">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="99cc8-148">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="99cc8-148">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="99cc8-149">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="99cc8-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="99cc8-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="99cc8-150">openTimeout</span></span>|<span data-ttu-id="99cc8-151">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="99cc8-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="99cc8-152">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99cc8-153">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="99cc8-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="99cc8-154">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="99cc8-154">proxyAddress</span></span>|<span data-ttu-id="99cc8-155">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="99cc8-155">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="99cc8-156">Se `useSystemWebProxy` for `true` , essa configuração deverá ser `null` .</span><span class="sxs-lookup"><span data-stu-id="99cc8-156">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="99cc8-157">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="99cc8-157">The default is `null`.</span></span>|  
|<span data-ttu-id="99cc8-158">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="99cc8-158">receiveTimeout</span></span>|<span data-ttu-id="99cc8-159">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="99cc8-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="99cc8-160">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99cc8-161">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="99cc8-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="99cc8-162">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="99cc8-162">sendTimeout</span></span>|<span data-ttu-id="99cc8-163">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="99cc8-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="99cc8-164">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99cc8-165">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="99cc8-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="99cc8-166">codificação de</span><span class="sxs-lookup"><span data-stu-id="99cc8-166">textEncoding</span></span>|<span data-ttu-id="99cc8-167">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-167">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="99cc8-168">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="99cc8-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="99cc8-169">-UnicodeFffeTextEncoding: codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="99cc8-169">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="99cc8-170">-Utf16TextEncoding: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="99cc8-170">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="99cc8-171">-Utf8TextEncoding: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="99cc8-171">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="99cc8-172">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="99cc8-172">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="99cc8-173">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="99cc8-174">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="99cc8-174">transactionFlow</span></span>|<span data-ttu-id="99cc8-175">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="99cc8-175">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="99cc8-176">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="99cc8-176">The default is `false`.</span></span>|  
|<span data-ttu-id="99cc8-177">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="99cc8-177">useDefaultWebProxy</span></span>|<span data-ttu-id="99cc8-178">Um valor booliano que especifica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="99cc8-178">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="99cc8-179">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="99cc8-179">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99cc8-180">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="99cc8-180">Child Elements</span></span>  
  
|<span data-ttu-id="99cc8-181">Elemento</span><span class="sxs-lookup"><span data-stu-id="99cc8-181">Element</span></span>|<span data-ttu-id="99cc8-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="99cc8-182">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="99cc8-183">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-183">Defines the security settings for the binding.</span></span> <span data-ttu-id="99cc8-184">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-184">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="99cc8-185">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="99cc8-185">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="99cc8-186">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="99cc8-186">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="99cc8-187">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="99cc8-187">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99cc8-188">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="99cc8-188">Parent Elements</span></span>  
  
|<span data-ttu-id="99cc8-189">Elemento</span><span class="sxs-lookup"><span data-stu-id="99cc8-189">Element</span></span>|<span data-ttu-id="99cc8-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="99cc8-190">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="99cc8-191">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="99cc8-191">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99cc8-192">Comentários</span><span class="sxs-lookup"><span data-stu-id="99cc8-192">Remarks</span></span>  
 <span data-ttu-id="99cc8-193">O `WSHttpBinding` é semelhante ao `BasicHttpBinding` , mas fornece mais recursos de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="99cc8-193">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="99cc8-194">Ele usa o transporte HTTP e fornece segurança de mensagem, como a BasicHttpBinding, mas também fornece transações, mensagens confiáveis e WS-Addressing, habilitado por padrão ou disponível por meio de uma configuração de controle único.</span><span class="sxs-lookup"><span data-stu-id="99cc8-194">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99cc8-195">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99cc8-195">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
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
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="99cc8-196">Confira também</span><span class="sxs-lookup"><span data-stu-id="99cc8-196">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="99cc8-197">Associações</span><span class="sxs-lookup"><span data-stu-id="99cc8-197">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="99cc8-198">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="99cc8-198">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="99cc8-199">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="99cc8-199">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
