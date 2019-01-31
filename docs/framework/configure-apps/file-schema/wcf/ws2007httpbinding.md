---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 9638d808c7d5b8c6f058df629991fb10cd354b97
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272000"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="a6c5f-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="a6c5f-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="a6c5f-102">Define uma associação interoperável que fornece suporte para as versões corretas dos <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, e <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="a6c5f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a6c5f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a6c5f-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a6c5f-104">\<bindings></span></span>  
<span data-ttu-id="a6c5f-105">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="a6c5f-105">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c5f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6c5f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6c5f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6c5f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a6c5f-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6c5f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6c5f-109">Attributes</span></span>  
  
|<span data-ttu-id="a6c5f-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6c5f-110">Attribute</span></span>|<span data-ttu-id="a6c5f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6c5f-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="a6c5f-112">Um valor que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="a6c5f-113">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a6c5f-114">Você pode usar essa propriedade quando você interage com serviços Web do ASP.NET (ASMX) que usam cookies.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-114">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="a6c5f-115">Isso garante que os cookies que o servidor retorna são copiados automaticamente para todas as solicitações futuras de cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-115">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="a6c5f-116">Um valor que indica se deve ignorar o servidor proxy para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-116">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="a6c5f-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-117">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="a6c5f-118">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo para concluir uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-118">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="a6c5f-119">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6c5f-120">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-120">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="a6c5f-121">Especifica o modo de comparação de nome de host HTTP usado para analisar os identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-121">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="a6c5f-122">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a6c5f-123">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="a6c5f-124">O tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-124">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a6c5f-125">O padrão é 524.288 bytes (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-125">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="a6c5f-126">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a6c5f-127">Criação e destruição de buffers de cada vez que elas são usadas é caro, assim como a coleta de lixo para buffers.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-127">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="a6c5f-128">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="a6c5f-129">Isso evita a sobrecarga na criação e destruição de buffers.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-129">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="a6c5f-130">O tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que pode ser receber um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-130">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="a6c5f-131">O remetente de uma mensagem exceder esse limite recebe uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-131">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="a6c5f-132">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-132">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a6c5f-133">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-133">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="a6c5f-134">Define o codificador usado para codificar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-134">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="a6c5f-135">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6c5f-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a6c5f-136">-   `Text`: Use um codificador de mensagem de texto.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-136">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="a6c5f-137">-   `Mtom`: Use um codificador de organização mecanismo 1.0 MTOM (Message Transmission).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-137">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="a6c5f-138">O padrão é `Text`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-138">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="a6c5f-139">Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-139">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="a6c5f-140">O nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-140">The configuration name of the binding.</span></span> <span data-ttu-id="a6c5f-141">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a6c5f-142">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-142">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a6c5f-143">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a6c5f-144">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a6c5f-145">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6c5f-146">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-146">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="a6c5f-147">Um URI que especifica o endereço do proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-147">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="a6c5f-148">Se `useSystemWebProxy` está `true`, essa configuração deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-148">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="a6c5f-149">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-149">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a6c5f-150">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a6c5f-151">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6c5f-152">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-152">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a6c5f-153">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a6c5f-154">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6c5f-155">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-155">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="a6c5f-156">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-156">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="a6c5f-157">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6c5f-157">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a6c5f-158">-   `UnicodeFffeTextEncoding`: Big Endian codificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-158">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="a6c5f-159">-   `Utf16TextEncoding`: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-159">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="a6c5f-160">-   `Utf8TextEncoding`: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-160">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="a6c5f-161">O padrão é `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-161">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="a6c5f-162">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-162">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="a6c5f-163">Um valor que especifica se a associação dá suporte a fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-163">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a6c5f-164">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-164">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="a6c5f-165">Um valor que especifica se o proxy HTTP configurado automaticamente do sistema é usado.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-165">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="a6c5f-166">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6c5f-167">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6c5f-167">Child Elements</span></span>  
  
|<span data-ttu-id="a6c5f-168">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6c5f-168">Element</span></span>|<span data-ttu-id="a6c5f-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6c5f-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6c5f-170">\<security></span><span class="sxs-lookup"><span data-stu-id="a6c5f-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="a6c5f-171">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-171">Defines the security settings for the binding.</span></span> <span data-ttu-id="a6c5f-172">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-172">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="a6c5f-173">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="a6c5f-173">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="a6c5f-174">Define as restrições na complexidade das mensagens SOAP que pontos de extremidade configurados com essa associação podem processar.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-174">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="a6c5f-175">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="a6c5f-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="a6c5f-176">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="a6c5f-177">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6c5f-178">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6c5f-178">Parent Elements</span></span>  
  
|<span data-ttu-id="a6c5f-179">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6c5f-179">Element</span></span>|<span data-ttu-id="a6c5f-180">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6c5f-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6c5f-181">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a6c5f-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="a6c5f-182">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6c5f-183">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6c5f-183">Remarks</span></span>  
 <span data-ttu-id="a6c5f-184">O `WS2007HttpBinding` adiciona uma associação fornecida pelo sistema semelhante ao `WSHttpBinding` mas utiliza a organização para as versões padrão do avanço dos Structured Information Standards (OASIS) dos protocolos TransactionFlow, ReliableSession e segurança.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-184">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="a6c5f-185">Nenhuma alteração para as configurações padrão ou de modelo de objeto é necessária ao usar essa associação.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-185">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6c5f-186">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6c5f-186">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6c5f-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6c5f-187">See also</span></span>
- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="a6c5f-188">Associações</span><span class="sxs-lookup"><span data-stu-id="a6c5f-188">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a6c5f-189">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a6c5f-189">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a6c5f-190">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a6c5f-190">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a6c5f-191">\<binding></span><span class="sxs-lookup"><span data-stu-id="a6c5f-191">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
