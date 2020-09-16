---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: 2364eb9d82fd17bd0b80b01070a0f1d789be3d90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556148"
---
# \<netNamedPipeBinding>
<span data-ttu-id="73385-101">Define uma associação que é segura, confiável e otimizada para comunicação entre processos no computador.</span><span class="sxs-lookup"><span data-stu-id="73385-101">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="73385-102">Por padrão, ele gera uma pilha de comunicação de tempo de execução com WS-ReliableMessaging para confiabilidade, segurança de transporte para segurança de transferência, pipes nomeados para entrega de mensagem e codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="73385-102">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="73385-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="73385-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73385-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73385-104">Attributes and Elements</span></span>  
 <span data-ttu-id="73385-105">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="73385-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73385-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="73385-106">Attributes</span></span>  
  
|<span data-ttu-id="73385-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="73385-107">Attribute</span></span>|<span data-ttu-id="73385-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="73385-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73385-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="73385-109">closeTimeout</span></span>|<span data-ttu-id="73385-110">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="73385-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="73385-111">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="73385-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73385-112">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="73385-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="73385-113">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="73385-113">hostNameComparisonMode</span></span>|<span data-ttu-id="73385-114">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="73385-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="73385-115">Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode> , que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI.</span><span class="sxs-lookup"><span data-stu-id="73385-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="73385-116">O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="73385-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="73385-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="73385-117">maxBufferPoolSize</span></span>|<span data-ttu-id="73385-118">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="73385-118">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="73385-119">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="73385-119">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="73385-120">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="73385-120">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="73385-121">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="73385-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="73385-122">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="73385-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="73385-123">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="73385-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="73385-124">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="73385-124">maxBufferSize</span></span>|<span data-ttu-id="73385-125">Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.</span><span class="sxs-lookup"><span data-stu-id="73385-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="73385-126">Se o buffer estiver cheio, os dados em excesso permanecerão no soquete subjacente até que o buffer tenha espaço novamente.</span><span class="sxs-lookup"><span data-stu-id="73385-126">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="73385-127">Este valor não pode ser menor que o `maxReceivedMessageSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="73385-127">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="73385-128">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="73385-128">The default is 65536.</span></span> <span data-ttu-id="73385-129">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="73385-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="73385-130">maxConnections</span><span class="sxs-lookup"><span data-stu-id="73385-130">maxConnections</span></span>|<span data-ttu-id="73385-131">Um inteiro que especifica o número máximo de conexões de entrada e de saída que o serviço criará/aceitará.</span><span class="sxs-lookup"><span data-stu-id="73385-131">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="73385-132">As conexões de entrada e saída são contadas em relação a um limite separado especificado por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="73385-132">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="73385-133">As conexões de entrada excedentes ao limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="73385-133">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="73385-134">As conexões de saída excedentes ao limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="73385-134">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="73385-135">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="73385-135">The default is 10.</span></span>|  
|<span data-ttu-id="73385-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="73385-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="73385-137">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="73385-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="73385-138">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="73385-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="73385-139">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="73385-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="73385-140">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="73385-140">The default is 65536.</span></span>|  
|<span data-ttu-id="73385-141">name</span><span class="sxs-lookup"><span data-stu-id="73385-141">name</span></span>|<span data-ttu-id="73385-142">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="73385-142">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="73385-143">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="73385-143">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="73385-144">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="73385-144">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="73385-145">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="73385-145">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="73385-146">openTimeout</span><span class="sxs-lookup"><span data-stu-id="73385-146">openTimeout</span></span>|<span data-ttu-id="73385-147">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="73385-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="73385-148">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="73385-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73385-149">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="73385-149">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="73385-150">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="73385-150">receiveTimeout</span></span>|<span data-ttu-id="73385-151">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="73385-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="73385-152">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="73385-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73385-153">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="73385-153">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="73385-154">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="73385-154">sendTimeout</span></span>|<span data-ttu-id="73385-155">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="73385-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="73385-156">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="73385-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73385-157">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="73385-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="73385-158">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="73385-158">transactionFlow</span></span>|<span data-ttu-id="73385-159">Um valor booliano que especifica se a associação dá suporte ao fluxo de WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="73385-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="73385-160">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="73385-160">The default is `false`.</span></span>|  
|<span data-ttu-id="73385-161">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="73385-161">transactionProtocol</span></span>|<span data-ttu-id="73385-162">Especifica o protocolo de transação a ser usado com esta associação.</span><span class="sxs-lookup"><span data-stu-id="73385-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="73385-163">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="73385-163">Valid values are</span></span><br /><br /> <span data-ttu-id="73385-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="73385-164">-   OleTransactions</span></span><br /><span data-ttu-id="73385-165">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="73385-165">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="73385-166">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="73385-166">The default is OleTransactions.</span></span> <span data-ttu-id="73385-167">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="73385-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="73385-168">transferMode</span><span class="sxs-lookup"><span data-stu-id="73385-168">transferMode</span></span>|<span data-ttu-id="73385-169">Um <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="73385-169">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73385-170">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73385-170">Child Elements</span></span>  
  
|<span data-ttu-id="73385-171">Elemento</span><span class="sxs-lookup"><span data-stu-id="73385-171">Element</span></span>|<span data-ttu-id="73385-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="73385-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="73385-173">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="73385-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="73385-174">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="73385-174">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="73385-175">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="73385-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="73385-176">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="73385-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73385-177">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="73385-177">Parent Elements</span></span>  
  
|<span data-ttu-id="73385-178">Elemento</span><span class="sxs-lookup"><span data-stu-id="73385-178">Element</span></span>|<span data-ttu-id="73385-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="73385-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="73385-180">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="73385-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73385-181">Comentários</span><span class="sxs-lookup"><span data-stu-id="73385-181">Remarks</span></span>  
 <span data-ttu-id="73385-182">O `NetNamedPipeBinding` gera uma pilha de comunicação de tempo de execução por padrão, que usa segurança de transporte, pipes nomeados para entrega de mensagem e uma codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="73385-182">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="73385-183">Essa associação é uma opção apropriada fornecida pelo sistema Windows Communication Foundation (WCF) para comunicação no computador.</span><span class="sxs-lookup"><span data-stu-id="73385-183">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="73385-184">Ele também dá suporte a transações.</span><span class="sxs-lookup"><span data-stu-id="73385-184">It also supports transactions.</span></span>  
  
 <span data-ttu-id="73385-185">A configuração padrão do `NetNamedPipeBinding` é semelhante à configuração fornecida pelo `NetTcpBinding` , mas é mais simples porque a implementação do WCF destina-se apenas ao uso no computador e, consequentemente, há menos recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="73385-185">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="73385-186">A diferença mais notável é que a `securityMode` configuração só oferece as `None` `Transport` Opções e.</span><span class="sxs-lookup"><span data-stu-id="73385-186">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="73385-187">O suporte à segurança SOAP não é uma opção incluída.</span><span class="sxs-lookup"><span data-stu-id="73385-187">SOAP security support is not an included option.</span></span> <span data-ttu-id="73385-188">O comportamento de segurança é configurável usando o `securityMode` atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="73385-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73385-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73385-189">Example</span></span>  
 <span data-ttu-id="73385-190">O exemplo a seguir demonstra a associação netNamedPipeBinding, que fornece comunicação entre processos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="73385-190">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="73385-191">Pipes nomeados não funcionam entre computadores.</span><span class="sxs-lookup"><span data-stu-id="73385-191">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="73385-192">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="73385-192">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="73385-193">O tipo de associação é especificado no `binding` atributo do `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="73385-193">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="73385-194">Se você quiser configurar a associação netNamedPipeBinding e alterar algumas de suas configurações, deverá definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="73385-194">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="73385-195">O ponto de extremidade deve referenciar a configuração de associação por nome com um `bindingConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="73385-195">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="73385-196">Neste exemplo, a configuração de associação é denominada Binding1.</span><span class="sxs-lookup"><span data-stu-id="73385-196">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73385-197">Confira também</span><span class="sxs-lookup"><span data-stu-id="73385-197">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="73385-198">Associações</span><span class="sxs-lookup"><span data-stu-id="73385-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="73385-199">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="73385-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="73385-200">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="73385-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
