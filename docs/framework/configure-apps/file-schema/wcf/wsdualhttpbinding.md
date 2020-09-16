---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 3e32539900893297d2bac232138f9940a8ab100b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557639"
---
# \<wsDualHttpBinding>
<span data-ttu-id="a5bdb-101">Define uma associação segura, confiável e interoperável adequada para contratos de serviço duplex ou comunicação por meio de intermediários SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-101">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="a5bdb-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5bdb-102">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5bdb-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a5bdb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a5bdb-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5bdb-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5bdb-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="a5bdb-105">Attributes</span></span>  
  
|<span data-ttu-id="a5bdb-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="a5bdb-106">Attribute</span></span>|<span data-ttu-id="a5bdb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5bdb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5bdb-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="a5bdb-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="a5bdb-109">Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="a5bdb-110">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-110">The default is `false`.</span></span>|  
|<span data-ttu-id="a5bdb-111">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="a5bdb-111">clientBaseAddress</span></span>|<span data-ttu-id="a5bdb-112">Um URI que define o endereço base que o cliente ouve para as mensagens de resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-112">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="a5bdb-113">Se especificado, esse endereço (mais um por channelGUID) será usado para escutar.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-113">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="a5bdb-114">Se o valor não for especificado, o endereço base do cliente será gerado de maneira específica de transporte.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-114">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="a5bdb-115">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-115">The default is `null`.</span></span>|  
|<span data-ttu-id="a5bdb-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a5bdb-116">closeTimeout</span></span>|<span data-ttu-id="a5bdb-117">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a5bdb-118">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5bdb-119">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a5bdb-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a5bdb-120">hostnameComparisonMode</span></span>|<span data-ttu-id="a5bdb-121">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a5bdb-122">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode> , que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a5bdb-123">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="a5bdb-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a5bdb-124">maxBufferPoolSize</span></span>|<span data-ttu-id="a5bdb-125">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a5bdb-126">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="a5bdb-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="a5bdb-127">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a5bdb-128">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a5bdb-129">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a5bdb-130">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="a5bdb-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a5bdb-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="a5bdb-132">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a5bdb-133">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="a5bdb-134">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a5bdb-135">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-135">The default is 65536.</span></span>|  
|<span data-ttu-id="a5bdb-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="a5bdb-136">messageEncoding</span></span>|<span data-ttu-id="a5bdb-137">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="a5bdb-138">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="a5bdb-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a5bdb-139">-Text: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="a5bdb-140">-MTOM: usar um codificador MTOM (mecanismo de organização de transmissão de mensagens) 1,0.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="a5bdb-141">-O padrão é texto.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-141">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="a5bdb-142">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="a5bdb-143">name</span><span class="sxs-lookup"><span data-stu-id="a5bdb-143">name</span></span>|<span data-ttu-id="a5bdb-144">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a5bdb-145">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a5bdb-146">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a5bdb-147">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5bdb-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="a5bdb-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a5bdb-148">openTimeout</span></span>|<span data-ttu-id="a5bdb-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a5bdb-150">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5bdb-151">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a5bdb-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="a5bdb-152">proxyAddress</span></span>|<span data-ttu-id="a5bdb-153">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="a5bdb-154">Se `useDefaultWebProxy` for `true` , essa configuração deverá ser `null` .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="a5bdb-155">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-155">The default is `null`.</span></span>|  
|<span data-ttu-id="a5bdb-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a5bdb-156">receiveTimeout</span></span>|<span data-ttu-id="a5bdb-157">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a5bdb-158">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5bdb-159">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a5bdb-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="a5bdb-160">sendTimeout</span></span>|<span data-ttu-id="a5bdb-161">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a5bdb-162">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5bdb-163">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a5bdb-164">codificação de</span><span class="sxs-lookup"><span data-stu-id="a5bdb-164">textEncoding</span></span>|<span data-ttu-id="a5bdb-165">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a5bdb-166">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="a5bdb-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a5bdb-167">-BigEndianUnicode: codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="a5bdb-168">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="a5bdb-169">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="a5bdb-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a5bdb-170">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-170">The default is UTF8.</span></span> <span data-ttu-id="a5bdb-171">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="a5bdb-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="a5bdb-172">transactionFlow</span></span>|<span data-ttu-id="a5bdb-173">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a5bdb-174">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-174">The default is `false`.</span></span>|  
|<span data-ttu-id="a5bdb-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="a5bdb-175">useDefaultWebProxy</span></span>|<span data-ttu-id="a5bdb-176">Um valor booliano que indica se o proxy HTTP autoconfigurado do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="a5bdb-177">O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true` .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="a5bdb-178">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-178">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5bdb-179">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a5bdb-179">Child Elements</span></span>  
  
|<span data-ttu-id="a5bdb-180">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5bdb-180">Element</span></span>|<span data-ttu-id="a5bdb-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5bdb-181">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="a5bdb-182">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-182">Defines the security settings for the binding.</span></span> <span data-ttu-id="a5bdb-183">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-183">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="a5bdb-184">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a5bdb-185">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="a5bdb-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="a5bdb-186">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5bdb-187">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5bdb-187">Parent Elements</span></span>  
  
|<span data-ttu-id="a5bdb-188">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5bdb-188">Element</span></span>|<span data-ttu-id="a5bdb-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5bdb-189">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="a5bdb-190">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5bdb-191">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5bdb-191">Remarks</span></span>  
 <span data-ttu-id="a5bdb-192">O `WSDualHttpBinding` fornece o mesmo suporte para protocolos de serviço Web como o `WSHttpBinding` , mas para uso com contratos duplex.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-192">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="a5bdb-193">`WSDualHttpBinding` dá suporte apenas à segurança SOAP e requer mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-193">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="a5bdb-194">Essa associação requer que o cliente tenha um URI público que forneça um ponto de extremidade de retorno de chamada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-194">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="a5bdb-195">Isso é fornecido pelo `clientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-195">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="a5bdb-196">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-196">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="a5bdb-197">O cliente deve usar a segurança para garantir que ele se conecte apenas aos serviços que confia.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-197">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="a5bdb-198">Essa associação pode ser usada para se comunicar de forma confiável por meio de um ou mais intermediários SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-198">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="a5bdb-199">Por padrão, essa associação gera uma pilha de tempo de execução com WS-ReliableMessaging para confiabilidade, WS-Security para segurança e autenticação de mensagens, HTTP para entrega de mensagens e uma codificação de mensagem de texto/XML.</span><span class="sxs-lookup"><span data-stu-id="a5bdb-199">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5bdb-200">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5bdb-200">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="a5bdb-201">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5bdb-201">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="a5bdb-202">Associações</span><span class="sxs-lookup"><span data-stu-id="a5bdb-202">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a5bdb-203">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a5bdb-203">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a5bdb-204">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a5bdb-204">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
