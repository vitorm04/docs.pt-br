---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139475"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="115d5-101">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="115d5-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="115d5-102">Define uma associação que é segura, confiável e otimizada para comunicação entre processos no computador.</span><span class="sxs-lookup"><span data-stu-id="115d5-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="115d5-103">Por padrão, ele gera uma pilha de comunicação de tempo de execução com WS-ReliableMessaging para confiabilidade, segurança de transporte para segurança de transferência, pipes nomeados para entrega de mensagem e codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="115d5-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="115d5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="115d5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="115d5-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="115d5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="115d5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="115d5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="115d5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="115d5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="115d5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="115d5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="115d5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="115d5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="115d5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="115d5-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="115d5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="115d5-111">Attributes</span></span>  
  
|<span data-ttu-id="115d5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="115d5-112">Attribute</span></span>|<span data-ttu-id="115d5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="115d5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="115d5-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="115d5-114">closeTimeout</span></span>|<span data-ttu-id="115d5-115">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="115d5-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="115d5-116">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="115d5-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="115d5-117">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="115d5-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="115d5-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="115d5-118">hostNameComparisonMode</span></span>|<span data-ttu-id="115d5-119">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="115d5-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="115d5-120">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="115d5-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="115d5-121">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="115d5-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="115d5-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="115d5-122">maxBufferPoolSize</span></span>|<span data-ttu-id="115d5-123">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="115d5-124">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="115d5-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="115d5-125">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="115d5-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="115d5-126">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="115d5-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="115d5-127">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="115d5-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="115d5-128">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="115d5-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="115d5-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="115d5-129">maxBufferSize</span></span>|<span data-ttu-id="115d5-130">Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.</span><span class="sxs-lookup"><span data-stu-id="115d5-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="115d5-131">Se o buffer estiver cheio, os dados em excesso permanecerão no soquete subjacente até que o buffer tenha espaço novamente.</span><span class="sxs-lookup"><span data-stu-id="115d5-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="115d5-132">Este valor não pode ser menor que `maxReceivedMessageSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="115d5-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="115d5-133">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="115d5-133">The default is 65536.</span></span> <span data-ttu-id="115d5-134">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="115d5-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="115d5-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="115d5-135">maxConnections</span></span>|<span data-ttu-id="115d5-136">Um inteiro que especifica o número máximo de conexões de entrada e de saída que o serviço criará/aceitará.</span><span class="sxs-lookup"><span data-stu-id="115d5-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="115d5-137">As conexões de entrada e saída são contadas em relação a um limite separado especificado por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="115d5-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="115d5-138">As conexões de entrada excedentes ao limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="115d5-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="115d5-139">As conexões de saída excedentes ao limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="115d5-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="115d5-140">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="115d5-140">The default is 10.</span></span>|  
|<span data-ttu-id="115d5-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="115d5-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="115d5-142">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="115d5-143">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="115d5-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="115d5-144">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="115d5-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="115d5-145">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="115d5-145">The default is 65536.</span></span>|  
|<span data-ttu-id="115d5-146">name</span><span class="sxs-lookup"><span data-stu-id="115d5-146">name</span></span>|<span data-ttu-id="115d5-147">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="115d5-148">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="115d5-149">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="115d5-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="115d5-150">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="115d5-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="115d5-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="115d5-151">openTimeout</span></span>|<span data-ttu-id="115d5-152">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="115d5-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="115d5-153">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="115d5-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="115d5-154">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="115d5-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="115d5-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="115d5-155">receiveTimeout</span></span>|<span data-ttu-id="115d5-156">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="115d5-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="115d5-157">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="115d5-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="115d5-158">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="115d5-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="115d5-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="115d5-159">sendTimeout</span></span>|<span data-ttu-id="115d5-160">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="115d5-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="115d5-161">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="115d5-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="115d5-162">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="115d5-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="115d5-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="115d5-163">transactionFlow</span></span>|<span data-ttu-id="115d5-164">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="115d5-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="115d5-165">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="115d5-165">The default is `false`.</span></span>|  
|<span data-ttu-id="115d5-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="115d5-166">transactionProtocol</span></span>|<span data-ttu-id="115d5-167">Especifica o protocolo de transação a ser usado com esta associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="115d5-168">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="115d5-168">Valid values are</span></span><br /><br /> <span data-ttu-id="115d5-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="115d5-169">-   OleTransactions</span></span><br /><span data-ttu-id="115d5-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="115d5-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="115d5-171">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="115d5-171">The default is OleTransactions.</span></span> <span data-ttu-id="115d5-172">Este atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="115d5-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="115d5-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="115d5-173">transferMode</span></span>|<span data-ttu-id="115d5-174">Um valor <xref:System.ServiceModel.TransferMode> que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="115d5-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="115d5-175">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="115d5-175">Child Elements</span></span>  
  
|<span data-ttu-id="115d5-176">Elemento</span><span class="sxs-lookup"><span data-stu-id="115d5-176">Element</span></span>|<span data-ttu-id="115d5-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="115d5-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="115d5-178">> \<segurança</span><span class="sxs-lookup"><span data-stu-id="115d5-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="115d5-179">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="115d5-180">Este elemento é do tipo <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="115d5-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="115d5-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="115d5-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="115d5-182">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="115d5-183">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="115d5-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="115d5-184">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="115d5-184">Parent Elements</span></span>  
  
|<span data-ttu-id="115d5-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="115d5-185">Element</span></span>|<span data-ttu-id="115d5-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="115d5-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="115d5-187">associações de \<</span><span class="sxs-lookup"><span data-stu-id="115d5-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="115d5-188">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="115d5-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="115d5-189">Comentários</span><span class="sxs-lookup"><span data-stu-id="115d5-189">Remarks</span></span>  
 <span data-ttu-id="115d5-190">O `NetNamedPipeBinding` gera uma pilha de comunicação de tempo de execução por padrão, que usa segurança de transporte, pipes nomeados para entrega de mensagem e uma codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="115d5-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="115d5-191">Essa associação é uma opção apropriada fornecida pelo sistema Windows Communication Foundation (WCF) para comunicação no computador.</span><span class="sxs-lookup"><span data-stu-id="115d5-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="115d5-192">Ele também dá suporte a transações.</span><span class="sxs-lookup"><span data-stu-id="115d5-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="115d5-193">A configuração padrão para o `NetNamedPipeBinding` é semelhante à configuração fornecida pelo `NetTcpBinding`, mas é mais simples porque a implementação do WCF destina-se apenas ao uso no computador e, consequentemente, há menos recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="115d5-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="115d5-194">A diferença mais notável é que a configuração de `securityMode` oferece apenas as opções `None` e `Transport`.</span><span class="sxs-lookup"><span data-stu-id="115d5-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="115d5-195">O suporte à segurança SOAP não é uma opção incluída.</span><span class="sxs-lookup"><span data-stu-id="115d5-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="115d5-196">O comportamento de segurança é configurável usando o atributo opcional `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="115d5-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="115d5-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="115d5-197">Example</span></span>  
 <span data-ttu-id="115d5-198">O exemplo a seguir demonstra a associação netNamedPipeBinding, que fornece comunicação entre processos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="115d5-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="115d5-199">Pipes nomeados não funcionam entre computadores.</span><span class="sxs-lookup"><span data-stu-id="115d5-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="115d5-200">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="115d5-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="115d5-201">O tipo de associação é especificado no atributo `binding` do elemento `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="115d5-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="115d5-202">Se você quiser configurar a associação netNamedPipeBinding e alterar algumas de suas configurações, deverá definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="115d5-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="115d5-203">O ponto de extremidade deve referenciar a configuração de associação por nome com um atributo `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="115d5-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="115d5-204">Neste exemplo, a configuração de associação é denominada Binding1.</span><span class="sxs-lookup"><span data-stu-id="115d5-204">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="115d5-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="115d5-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="115d5-206">> de associação de \<</span><span class="sxs-lookup"><span data-stu-id="115d5-206">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="115d5-207">Associações</span><span class="sxs-lookup"><span data-stu-id="115d5-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="115d5-208">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="115d5-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="115d5-209">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="115d5-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
