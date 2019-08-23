---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 7d847ffd4c1e3d924b9c45497c1b2ee172887e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933008"
---
# <a name="nettcpbinding"></a><span data-ttu-id="9f9fd-101">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9f9fd-101">\<netTcpBinding></span></span>

<span data-ttu-id="9f9fd-102">Especifica uma associação segura, confiável e otimizada adequada para comunicação entre computadores.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-102">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="9f9fd-103">Por padrão, ele gera uma pilha de comunicação de tempo de execução com segurança do Windows para segurança e autenticação de mensagens, TCP para entrega de mensagens e codificação de mensagens binárias.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-103">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="9f9fd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f9fd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f9fd-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9f9fd-105">\<bindings></span></span>  
<span data-ttu-id="9f9fd-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9f9fd-106">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9fd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f9fd-107">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f9fd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f9fd-108">Attributes and elements</span></span>

<span data-ttu-id="9f9fd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f9fd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f9fd-110">Attributes</span></span>  
  
|<span data-ttu-id="9f9fd-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f9fd-111">Attribute</span></span>|<span data-ttu-id="9f9fd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9fd-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="9f9fd-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9f9fd-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f9fd-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-115">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="9f9fd-116">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9f9fd-117">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-117">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9f9fd-118">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-118">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="9f9fd-119">Um inteiro positivo que especifica o número máximo de canais aguardando para serem aceitos no ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-119">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="9f9fd-120">As conexões que excederem esse limite serão enfileiradas até que o espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-120">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="9f9fd-121">O `connectionTimeout` atributo limita o tempo que um cliente aguardará para ser conectado antes de lançar uma exceção de conexão.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-121">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="9f9fd-122">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-122">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="9f9fd-123">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9f9fd-124">O padrão é 512 \* 1024 bytes.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-124">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="9f9fd-125">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9f9fd-126">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9f9fd-127">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9f9fd-128">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="9f9fd-129">Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="9f9fd-130">Se o `transferMode` atributo for igual `Buffered`a, esse atributo deverá ser igual ao `maxReceivedMessageSize` valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-130">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="9f9fd-131">Se o `transferMode` atributo for igual `Streamed`a, esse atributo não poderá ser maior `maxReceivedMessageSize` que o valor do atributo e deverá ter pelo menos o tamanho dos cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-131">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="9f9fd-132">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-132">The default is 65536.</span></span> <span data-ttu-id="9f9fd-133">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="9f9fd-134">Um inteiro que especifica o número máximo de conexões de entrada e de saída que o serviço criará/aceitará.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-134">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="9f9fd-135">As conexões de entrada e saída são contadas em relação a um limite separado especificado por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-135">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="9f9fd-136">As conexões de entrada excedentes ao limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-136">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="9f9fd-137">As conexões de saída excedentes ao limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-137">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="9f9fd-138">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-138">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="9f9fd-139">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9f9fd-140">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="9f9fd-141">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9f9fd-142">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-142">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="9f9fd-143">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9f9fd-144">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9f9fd-145">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f9fd-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9f9fd-146">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9f9fd-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="9f9fd-147">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9f9fd-148">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f9fd-149">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-149">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="9f9fd-150">Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-150">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="9f9fd-151">Se isso for `false`, cada associação usará sua própria porta exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-151">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="9f9fd-152">Essa configuração é relevante apenas para serviços, pois os clientes não são afetados.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-152">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9f9fd-153">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9f9fd-154">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f9fd-155">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-155">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9f9fd-156">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9f9fd-157">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f9fd-158">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-158">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="9f9fd-159">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="9f9fd-160">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-160">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="9f9fd-161">Especifica o protocolo de transação a ser usado com esta associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-161">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="9f9fd-162">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="9f9fd-162">Valid values are</span></span><br /><br /> <span data-ttu-id="9f9fd-163">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="9f9fd-163">-   OleTransactions</span></span><br /><span data-ttu-id="9f9fd-164">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="9f9fd-164">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="9f9fd-165">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-165">The default is OleTransactions.</span></span> <span data-ttu-id="9f9fd-166">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-166">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="9f9fd-167">Um <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-167">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f9fd-168">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f9fd-168">Child elements</span></span>  
  
|<span data-ttu-id="9f9fd-169">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f9fd-169">Element</span></span>|<span data-ttu-id="9f9fd-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9fd-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f9fd-171">\<security></span><span class="sxs-lookup"><span data-stu-id="9f9fd-171">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="9f9fd-172">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="9f9fd-173">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-173">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|<span data-ttu-id="9f9fd-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9f9fd-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="9f9fd-175">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9f9fd-176">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="9f9fd-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9f9fd-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="9f9fd-178">Especifica se as sessões confiáveis são estabelecidas entre os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-178">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f9fd-179">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f9fd-179">Parent elements</span></span>  
  
|<span data-ttu-id="9f9fd-180">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f9fd-180">Element</span></span>|<span data-ttu-id="9f9fd-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9fd-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f9fd-182">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9f9fd-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="9f9fd-183">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9fd-184">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f9fd-184">Remarks</span></span>

<span data-ttu-id="9f9fd-185">Essa associação gera uma pilha de comunicação de tempo de execução por padrão, que usa segurança de transporte, TCP para entrega de mensagem e uma codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-185">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="9f9fd-186">Essa associação é uma opção apropriada fornecida pelo sistema Windows Communication Foundation (WCF) para comunicação por uma intranet.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-186">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="9f9fd-187">A configuração `netTcpBinding` padrão do é mais rápida do que a configuração fornecida `wsHttpBinding`pelo, mas destina-se apenas à comunicação do WCF.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-187">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="9f9fd-188">O comportamento de segurança é configurável usando o `securityMode` atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="9f9fd-189">O uso de WS-ReliableMessaging pode ser configurado usando o `reliableSessionEnabled` atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-189">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="9f9fd-190">Mas o sistema de mensagens confiável está desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-190">But reliable messaging is off by default.</span></span> <span data-ttu-id="9f9fd-191">Em geral, as associações fornecidas pelo sistema http, como `wsHttpBinding` e `basicHttpBinding` , são configuradas para ativar as coisas por padrão, `netTcpBinding` enquanto a ligação desativa as coisas por padrão, para que você tenha que optar por obter suporte, por exemplo, para um dos as especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-191">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="9f9fd-192">Isso significa que a configuração padrão para TCP é mais rápida na troca de mensagens entre pontos de extremidade do que aquelas configuradas para as associações HTTP por padrão.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-192">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9fd-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f9fd-193">Example</span></span>

<span data-ttu-id="9f9fd-194">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-194">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="9f9fd-195">O tipo de associação é especificado no `binding` atributo `<endpoint>` do elemento.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-195">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="9f9fd-196">Se você quiser configurar a associação netTcpbinding e alterar algumas de suas configurações, será necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-196">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="9f9fd-197">O ponto de extremidade deve referenciar a configuração `bindingConfiguration` de associação com um atributo.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-197">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="9f9fd-198">No exemplo a seguir, uma configuração de associação é definida.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-198">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="9f9fd-199">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f9fd-199">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="9f9fd-200">Associações</span><span class="sxs-lookup"><span data-stu-id="9f9fd-200">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f9fd-201">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="9f9fd-201">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9f9fd-202">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9f9fd-202">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9f9fd-203">\<binding></span><span class="sxs-lookup"><span data-stu-id="9f9fd-203">\<binding></span></span>](../../../misc/binding.md)
