---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: 183ce624d22162c2d665b173d8c04e132457a3fb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257246"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="eb012-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="eb012-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="eb012-102">Define uma associação que é segura, confiável, otimizado para máquina comunicação entre processos.</span><span class="sxs-lookup"><span data-stu-id="eb012-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="eb012-103">Por padrão, ele gera uma pilha de comunicação em tempo de execução com WS-ReliableMessaging para confiabilidade, segurança de transporte para segurança de transferência, pipes nomeada para entrega de mensagens e codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="eb012-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="eb012-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb012-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb012-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="eb012-105">\<bindings></span></span>  
<span data-ttu-id="eb012-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="eb012-106">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb012-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb012-107">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb012-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eb012-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eb012-109">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb012-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb012-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb012-110">Attributes</span></span>  
  
|<span data-ttu-id="eb012-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="eb012-111">Attribute</span></span>|<span data-ttu-id="eb012-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb012-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb012-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="eb012-113">closeTimeout</span></span>|<span data-ttu-id="eb012-114">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="eb012-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="eb012-115">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eb012-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eb012-116">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="eb012-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="eb012-117">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="eb012-117">hostnameComparisonMode</span></span>|<span data-ttu-id="eb012-118">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="eb012-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="eb012-119">Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="eb012-119">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="eb012-120">O valor padrão é `StrongWildcard`, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="eb012-120">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="eb012-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="eb012-121">maxBufferPoolSize</span></span>|<span data-ttu-id="eb012-122">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-122">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="eb012-123">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="eb012-123">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="eb012-124">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="eb012-124">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="eb012-125">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="eb012-125">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="eb012-126">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="eb012-126">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="eb012-127">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="eb012-127">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="eb012-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="eb012-128">maxBufferSize</span></span>|<span data-ttu-id="eb012-129">Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.</span><span class="sxs-lookup"><span data-stu-id="eb012-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="eb012-130">Se o buffer estiver cheio, o excesso de dados permanece no soquete subjacente até que o buffer tem espaço novamente.</span><span class="sxs-lookup"><span data-stu-id="eb012-130">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="eb012-131">Esse valor não pode ser menor que `maxReceivedMessageSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="eb012-131">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="eb012-132">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="eb012-132">The default is 65536.</span></span> <span data-ttu-id="eb012-133">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb012-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="eb012-134">maxConnections</span><span class="sxs-lookup"><span data-stu-id="eb012-134">maxConnections</span></span>|<span data-ttu-id="eb012-135">Um inteiro que especifica o número máximo de conexões de entrada e saídas de serviço cria/aceitará.</span><span class="sxs-lookup"><span data-stu-id="eb012-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="eb012-136">Conexões de entrada e saídas são contadas em relação a um limite separado especificado por este atributo.</span><span class="sxs-lookup"><span data-stu-id="eb012-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="eb012-137">Conexões de entrada que excede o limite são enfileiradas até que um espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="eb012-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="eb012-138">Conexões de saída que excede o limite são enfileiradas até que um espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="eb012-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="eb012-139">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="eb012-139">The default is 10.</span></span>|  
|<span data-ttu-id="eb012-140">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="eb012-140">maxReceivedMessageSize</span></span>|<span data-ttu-id="eb012-141">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-141">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="eb012-142">O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="eb012-142">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="eb012-143">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="eb012-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="eb012-144">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="eb012-144">The default is 65536.</span></span>|  
|<span data-ttu-id="eb012-145">name</span><span class="sxs-lookup"><span data-stu-id="eb012-145">name</span></span>|<span data-ttu-id="eb012-146">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="eb012-147">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="eb012-148">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="eb012-148">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="eb012-149">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="eb012-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="eb012-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="eb012-150">openTimeout</span></span>|<span data-ttu-id="eb012-151">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="eb012-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="eb012-152">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eb012-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eb012-153">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="eb012-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="eb012-154">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="eb012-154">receiveTimeout</span></span>|<span data-ttu-id="eb012-155">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="eb012-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="eb012-156">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eb012-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eb012-157">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="eb012-157">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="eb012-158">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="eb012-158">sendTimeout</span></span>|<span data-ttu-id="eb012-159">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="eb012-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="eb012-160">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eb012-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eb012-161">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="eb012-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="eb012-162">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="eb012-162">transactionFlow</span></span>|<span data-ttu-id="eb012-163">Um valor booliano que especifica se a associação dá suporte a fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="eb012-163">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="eb012-164">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="eb012-164">The default is `false`.</span></span>|  
|<span data-ttu-id="eb012-165">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="eb012-165">transactionProtocol</span></span>|<span data-ttu-id="eb012-166">Especifica o protocolo de transação a ser usado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-166">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="eb012-167">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="eb012-167">Valid values are</span></span><br /><br /> <span data-ttu-id="eb012-168">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="eb012-168">-   OleTransactions</span></span><br /><span data-ttu-id="eb012-169">-   WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="eb012-169">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="eb012-170">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="eb012-170">The default is OleTransactions.</span></span> <span data-ttu-id="eb012-171">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="eb012-171">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="eb012-172">transferMode</span><span class="sxs-lookup"><span data-stu-id="eb012-172">transferMode</span></span>|<span data-ttu-id="eb012-173">Um <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="eb012-173">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb012-174">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eb012-174">Child Elements</span></span>  
  
|<span data-ttu-id="eb012-175">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb012-175">Element</span></span>|<span data-ttu-id="eb012-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb012-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb012-177">\<security></span><span class="sxs-lookup"><span data-stu-id="eb012-177">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="eb012-178">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-178">Defines the security settings for the binding.</span></span> <span data-ttu-id="eb012-179">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="eb012-179">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="eb012-180">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="eb012-180">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="eb012-181">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-181">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="eb012-182">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="eb012-182">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb012-183">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb012-183">Parent Elements</span></span>  
  
|<span data-ttu-id="eb012-184">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb012-184">Element</span></span>|<span data-ttu-id="eb012-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb012-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb012-186">\<bindings></span><span class="sxs-lookup"><span data-stu-id="eb012-186">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="eb012-187">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="eb012-187">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb012-188">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb012-188">Remarks</span></span>  
 <span data-ttu-id="eb012-189">O `NetNamedPipeBinding` gera uma pilha de comunicação de tempo de execução por padrão, que usa a segurança de transporte, pipes nomeada para entrega de mensagens e uma codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="eb012-189">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="eb012-190">Essa associação é uma Windows Communication Foundation (WCF) fornecida pelo sistema opção apropriada para a comunicação na máquina.</span><span class="sxs-lookup"><span data-stu-id="eb012-190">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="eb012-191">Ele também oferece suporte a transações.</span><span class="sxs-lookup"><span data-stu-id="eb012-191">It also supports transactions.</span></span>  
  
 <span data-ttu-id="eb012-192">A configuração padrão para o `NetNamedPipeBinding` é semelhante para a configuração fornecida pelo `NetTcpBinding`, mas é mais simples porque a implementação de WCF destina-se somente para uso em computadores e, consequentemente, há menos recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="eb012-192">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="eb012-193">A diferença mais notável é que o `securityMode` definir ofertas somente o `None` e `Transport` opções.</span><span class="sxs-lookup"><span data-stu-id="eb012-193">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="eb012-194">Suporte de segurança SOAP não é uma opção incluída.</span><span class="sxs-lookup"><span data-stu-id="eb012-194">SOAP security support is not an included option.</span></span> <span data-ttu-id="eb012-195">O comportamento de segurança é configurável usando opcional `securityMode` atributo.</span><span class="sxs-lookup"><span data-stu-id="eb012-195">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb012-196">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb012-196">Example</span></span>  
 <span data-ttu-id="eb012-197">O exemplo a seguir demonstra a associação de netNamedPipeBinding, que fornece comunicação entre processos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="eb012-197">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="eb012-198">Pipes nomeados não funcionam em computadores.</span><span class="sxs-lookup"><span data-stu-id="eb012-198">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="eb012-199">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="eb012-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="eb012-200">O tipo de associação é especificado na `binding` atributo do `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="eb012-200">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="eb012-201">Se você quiser configurar a associação de netNamedPipeBinding e alterar algumas de suas configurações, você deve definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="eb012-201">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="eb012-202">O ponto de extremidade deve fazer referência a configuração de associação por nome com um `bindingConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="eb012-202">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="eb012-203">Neste exemplo, a configuração de associação é denominada Binding1.</span><span class="sxs-lookup"><span data-stu-id="eb012-203">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="eb012-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb012-204">See also</span></span>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="eb012-205">\<binding></span><span class="sxs-lookup"><span data-stu-id="eb012-205">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="eb012-206">Associações</span><span class="sxs-lookup"><span data-stu-id="eb012-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="eb012-207">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="eb012-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="eb012-208">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="eb012-208">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
