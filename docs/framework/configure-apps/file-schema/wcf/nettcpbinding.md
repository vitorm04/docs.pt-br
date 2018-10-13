---
title: '&lt;netTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: d8e001e6c39549b35eee332d0874e6f347b53509
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49314891"
---
# <a name="ltnettcpbindinggt"></a><span data-ttu-id="e338e-102">&lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e338e-102">&lt;netTcpBinding&gt;</span></span>

<span data-ttu-id="e338e-103">Especifica uma associação segura, confiável e otimizada adequada para comunicação entre computadores.</span><span class="sxs-lookup"><span data-stu-id="e338e-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="e338e-104">Por padrão, ele gera uma pilha de comunicação em tempo de execução com a segurança do Windows para autenticação, TCP para entrega de mensagens e codificação de mensagem binária e de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e338e-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="e338e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e338e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e338e-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="e338e-106">\<bindings></span></span>  
<span data-ttu-id="e338e-107">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e338e-107">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e338e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e338e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e338e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e338e-109">Attributes and elements</span></span>

<span data-ttu-id="e338e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e338e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e338e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e338e-111">Attributes</span></span>  
  
|<span data-ttu-id="e338e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e338e-112">Attribute</span></span>|<span data-ttu-id="e338e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e338e-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e338e-114">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="e338e-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e338e-115">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e338e-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e338e-116">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="e338e-116">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="e338e-117">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="e338e-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="e338e-118">Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="e338e-118">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e338e-119">O valor padrão é `StrongWildcard`, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="e338e-119">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="e338e-120">Um inteiro positivo que especifica o número máximo de canais esperando para serem aceitos no ouvinte.</span><span class="sxs-lookup"><span data-stu-id="e338e-120">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="e338e-121">As conexões que excede esse limite são enfileiradas até que o espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="e338e-121">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="e338e-122">O `connectionTimeout` atributo limita o tempo que um cliente irá esperar para ser conectado antes de lançar uma exceção de conexão.</span><span class="sxs-lookup"><span data-stu-id="e338e-122">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="e338e-123">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="e338e-123">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e338e-124">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e338e-125">O padrão é 512 \* 1024 bytes.</span><span class="sxs-lookup"><span data-stu-id="e338e-125">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="e338e-126">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="e338e-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e338e-127">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="e338e-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e338e-128">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="e338e-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e338e-129">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="e338e-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="e338e-130">Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.</span><span class="sxs-lookup"><span data-stu-id="e338e-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="e338e-131">Se o `transferMode` atributo é igual a `Buffered`, esse atributo deve ser igual ao `maxReceivedMessageSize` valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="e338e-131">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="e338e-132">Se o `transferMode` atributo é igual a `Streamed`, esse atributo não pode ser mais do que o `maxReceivedMessageSize` valor do atributo, e deve ser pelo menos o tamanho dos cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="e338e-132">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="e338e-133">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="e338e-133">The default is 65536.</span></span> <span data-ttu-id="e338e-134">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="e338e-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="e338e-135">Um inteiro que especifica o número máximo de conexões de entrada e saídas de serviço cria/aceitará.</span><span class="sxs-lookup"><span data-stu-id="e338e-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="e338e-136">Conexões de entrada e saídas são contadas em relação a um limite separado especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="e338e-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="e338e-137">Conexões de entrada que excede o limite são enfileiradas até que um espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="e338e-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="e338e-138">Conexões de saída que excede o limite são enfileiradas até que um espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="e338e-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="e338e-139">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="e338e-139">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e338e-140">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-140">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e338e-141">O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="e338e-141">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="e338e-142">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e338e-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e338e-143">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="e338e-143">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="e338e-144">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e338e-145">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e338e-146">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="e338e-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e338e-147">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e338e-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e338e-148">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="e338e-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e338e-149">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e338e-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e338e-150">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="e338e-150">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="e338e-151">Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="e338e-151">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="e338e-152">Quando se trata de `false`, cada associação usa sua própria porta exclusiva.</span><span class="sxs-lookup"><span data-stu-id="e338e-152">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="e338e-153">Essa configuração é relevante apenas para serviços, porque os clientes não são afetados.</span><span class="sxs-lookup"><span data-stu-id="e338e-153">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e338e-154">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="e338e-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e338e-155">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e338e-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e338e-156">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="e338e-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e338e-157">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="e338e-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e338e-158">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e338e-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e338e-159">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="e338e-159">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="e338e-160">Um valor booliano que especifica se a associação dá suporte a fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="e338e-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="e338e-161">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e338e-161">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="e338e-162">Especifica o protocolo de transação a ser usado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="e338e-163">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="e338e-163">Valid values are</span></span><br /><br /> <span data-ttu-id="e338e-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="e338e-164">-   OleTransactions</span></span><br /><span data-ttu-id="e338e-165">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="e338e-165">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="e338e-166">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="e338e-166">The default is OleTransactions.</span></span> <span data-ttu-id="e338e-167">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="e338e-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="e338e-168">Um <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="e338e-168">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e338e-169">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e338e-169">Child elements</span></span>  
  
|<span data-ttu-id="e338e-170">Elemento</span><span class="sxs-lookup"><span data-stu-id="e338e-170">Element</span></span>|<span data-ttu-id="e338e-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="e338e-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e338e-172">\<security></span><span class="sxs-lookup"><span data-stu-id="e338e-172">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="e338e-173">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="e338e-174">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e338e-174">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[<span data-ttu-id="e338e-175">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="e338e-175">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="e338e-176">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e338e-177">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e338e-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="e338e-178">reliableSession</span><span class="sxs-lookup"><span data-stu-id="e338e-178">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="e338e-179">Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="e338e-179">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e338e-180">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e338e-180">Parent elements</span></span>  
  
|<span data-ttu-id="e338e-181">Elemento</span><span class="sxs-lookup"><span data-stu-id="e338e-181">Element</span></span>|<span data-ttu-id="e338e-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="e338e-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e338e-183">\<associações ></span><span class="sxs-lookup"><span data-stu-id="e338e-183">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e338e-184">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e338e-184">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e338e-185">Comentários</span><span class="sxs-lookup"><span data-stu-id="e338e-185">Remarks</span></span>

<span data-ttu-id="e338e-186">Essa associação gera uma pilha de comunicação de tempo de execução por padrão, que usa segurança de transporte TCP para entrega de mensagens e uma codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="e338e-186">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="e338e-187">Essa associação é uma Windows Communication Foundation (WCF) fornecida pelo sistema opção apropriada para se comunicar através de uma Intranet.</span><span class="sxs-lookup"><span data-stu-id="e338e-187">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="e338e-188">A configuração padrão para o `netTcpBinding` é mais rápido que a configuração fornecida pelo `wsHttpBinding`, mas é destinada apenas para comunicação do WCF.</span><span class="sxs-lookup"><span data-stu-id="e338e-188">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="e338e-189">O comportamento de segurança é configurável usando opcional `securityMode` atributo.</span><span class="sxs-lookup"><span data-stu-id="e338e-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="e338e-190">O uso de WS-ReliableMessaging é configurável usando opcional `reliableSessionEnabled` atributo.</span><span class="sxs-lookup"><span data-stu-id="e338e-190">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="e338e-191">Mas o sistema de mensagens confiável está desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="e338e-191">But reliable messaging is off by default.</span></span> <span data-ttu-id="e338e-192">De modo geral, as HTTP associações fornecidas pelo sistema, como `wsHttpBinding` e `basicHttpBinding` são configurados para ativar as coisas por padrão, enquanto o `netTcpBinding` associação desativa as coisas por padrão para que você precise opt-in para obter suporte, por exemplo, para um dos o WS-\* especificações.</span><span class="sxs-lookup"><span data-stu-id="e338e-192">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="e338e-193">Isso significa que a configuração padrão para TCP mais rápida na troca de mensagens entre pontos de extremidade que aquelas configuradas para as ligações HTTP por padrão.</span><span class="sxs-lookup"><span data-stu-id="e338e-193">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e338e-194">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e338e-194">Example</span></span>

<span data-ttu-id="e338e-195">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="e338e-195">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="e338e-196">O tipo de associação é especificado na `binding` atributo do `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="e338e-196">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="e338e-197">Se você quiser configurar a associação netTcpBinding e alterar algumas de suas configurações, é necessário definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="e338e-197">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="e338e-198">O ponto de extremidade deve fazer referência a configuração de ligação com um `bindingConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="e338e-198">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="e338e-199">No exemplo a seguir, uma configuração de associação é definida.</span><span class="sxs-lookup"><span data-stu-id="e338e-199">In the following example, a binding configuration is defined.</span></span>  
  
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
    <binding   
             closeTimeout="00:01:00"  
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
  
## <a name="see-also"></a><span data-ttu-id="e338e-200">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e338e-200">See also</span></span>  

- <xref:System.ServiceModel.NetTcpBinding>  
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
- [<span data-ttu-id="e338e-201">Associações</span><span class="sxs-lookup"><span data-stu-id="e338e-201">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
- [<span data-ttu-id="e338e-202">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="e338e-202">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
- [<span data-ttu-id="e338e-203">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e338e-203">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
- [<span data-ttu-id="e338e-204">\<associação ></span><span class="sxs-lookup"><span data-stu-id="e338e-204">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
