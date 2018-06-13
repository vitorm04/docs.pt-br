---
title: '&lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: a3d264207a07e9ccc121f697522ffadcf0123038
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751822"
---
# <a name="ltnetnamedpipebindinggt"></a><span data-ttu-id="fc808-102">&lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="fc808-102">&lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="fc808-103">Define uma associação que é segura, confiável e otimizada para máquina cruzada comunicação de processo.</span><span class="sxs-lookup"><span data-stu-id="fc808-103">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="fc808-104">Por padrão, ele gera uma pilha de comunicação em tempo de execução com o WS-ReliableMessaging de confiabilidade, segurança de transporte para segurança de transferência, pipes nomeada para entrega de mensagens e a codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="fc808-104">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="fc808-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fc808-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fc808-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="fc808-106">\<bindings></span></span>  
<span data-ttu-id="fc808-107">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="fc808-107">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc808-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc808-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc808-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc808-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fc808-110">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc808-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc808-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc808-111">Attributes</span></span>  
  
|<span data-ttu-id="fc808-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="fc808-112">Attribute</span></span>|<span data-ttu-id="fc808-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc808-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc808-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="fc808-114">closeTimeout</span></span>|<span data-ttu-id="fc808-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="fc808-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fc808-116">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc808-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc808-117">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fc808-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fc808-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="fc808-118">hostnameComparisonMode</span></span>|<span data-ttu-id="fc808-119">Especifica o modo de comparação de nome de host HTTP usado para analisar URIs.</span><span class="sxs-lookup"><span data-stu-id="fc808-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="fc808-120">Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="fc808-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="fc808-121">O valor padrão é `StrongWildcard`, que ignora o nome do host na correspondência.</span><span class="sxs-lookup"><span data-stu-id="fc808-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="fc808-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="fc808-122">maxBufferPoolSize</span></span>|<span data-ttu-id="fc808-123">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="fc808-124">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="fc808-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="fc808-125">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="fc808-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="fc808-126">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="fc808-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="fc808-127">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="fc808-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="fc808-128">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="fc808-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="fc808-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="fc808-129">maxBufferSize</span></span>|<span data-ttu-id="fc808-130">Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.</span><span class="sxs-lookup"><span data-stu-id="fc808-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="fc808-131">Se o buffer estiver cheio, o excesso de dados permanece no soquete subjacente até que o buffer tem espaço novamente.</span><span class="sxs-lookup"><span data-stu-id="fc808-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="fc808-132">Esse valor não pode ser menor que `maxReceivedMessageSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="fc808-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="fc808-133">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="fc808-133">The default is 65536.</span></span> <span data-ttu-id="fc808-134">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc808-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="fc808-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="fc808-135">maxConnections</span></span>|<span data-ttu-id="fc808-136">Um inteiro que especifica o número máximo de conexões de entrada e saídas de serviço cria/aceitará.</span><span class="sxs-lookup"><span data-stu-id="fc808-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="fc808-137">Conexões de entrada e saídas são contados em relação a um limite separado especificado por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="fc808-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="fc808-138">Excedendo o limite de conexões de entrada são enfileiradas até que um espaço abaixo do limite se torne disponível.</span><span class="sxs-lookup"><span data-stu-id="fc808-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="fc808-139">Conexões de saída além do limite são enfileiradas até que um espaço abaixo do limite se torne disponível.</span><span class="sxs-lookup"><span data-stu-id="fc808-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="fc808-140">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="fc808-140">The default is 10.</span></span>|  
|<span data-ttu-id="fc808-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="fc808-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="fc808-142">Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="fc808-143">O remetente de uma mensagem exceder esse limite recebem uma falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="fc808-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="fc808-144">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="fc808-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="fc808-145">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="fc808-145">The default is 65536.</span></span>|  
|<span data-ttu-id="fc808-146">name</span><span class="sxs-lookup"><span data-stu-id="fc808-146">name</span></span>|<span data-ttu-id="fc808-147">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fc808-148">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fc808-149">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="fc808-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fc808-150">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc808-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="fc808-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="fc808-151">openTimeout</span></span>|<span data-ttu-id="fc808-152">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="fc808-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fc808-153">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc808-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc808-154">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fc808-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fc808-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fc808-155">receiveTimeout</span></span>|<span data-ttu-id="fc808-156">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="fc808-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fc808-157">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc808-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc808-158">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fc808-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="fc808-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="fc808-159">sendTimeout</span></span>|<span data-ttu-id="fc808-160">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="fc808-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fc808-161">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc808-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc808-162">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fc808-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fc808-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="fc808-163">transactionFlow</span></span>|<span data-ttu-id="fc808-164">Um valor booleano que especifica se a associação oferece suporte a fluxo de transações de WS.</span><span class="sxs-lookup"><span data-stu-id="fc808-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="fc808-165">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="fc808-165">The default is `false`.</span></span>|  
|<span data-ttu-id="fc808-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="fc808-166">transactionProtocol</span></span>|<span data-ttu-id="fc808-167">Especifica o protocolo de transação a ser usado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="fc808-168">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="fc808-168">Valid values are</span></span><br /><br /> <span data-ttu-id="fc808-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="fc808-169">-   OleTransactions</span></span><br /><span data-ttu-id="fc808-170">-   WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="fc808-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="fc808-171">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="fc808-171">The default is OleTransactions.</span></span> <span data-ttu-id="fc808-172">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="fc808-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="fc808-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="fc808-173">transferMode</span></span>|<span data-ttu-id="fc808-174">Um <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenados em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="fc808-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc808-175">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc808-175">Child Elements</span></span>  
  
|<span data-ttu-id="fc808-176">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc808-176">Element</span></span>|<span data-ttu-id="fc808-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc808-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc808-178">\<security></span><span class="sxs-lookup"><span data-stu-id="fc808-178">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="fc808-179">Define as configurações de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="fc808-180">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="fc808-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="fc808-181">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="fc808-181">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="fc808-182">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fc808-183">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fc808-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc808-184">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fc808-184">Parent Elements</span></span>  
  
|<span data-ttu-id="fc808-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc808-185">Element</span></span>|<span data-ttu-id="fc808-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc808-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc808-187">\<associações ></span><span class="sxs-lookup"><span data-stu-id="fc808-187">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="fc808-188">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="fc808-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc808-189">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc808-189">Remarks</span></span>  
 <span data-ttu-id="fc808-190">O `NetNamedPipeBinding` gera uma pilha de comunicação de tempo de execução por padrão, que usa a segurança de transporte, pipes nomeada para entrega de mensagens e uma codificação de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="fc808-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="fc808-191">Essa associação é uma Windows Communication Foundation (WCF) fornecida pelo sistema opção apropriada para a comunicação na máquina.</span><span class="sxs-lookup"><span data-stu-id="fc808-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="fc808-192">Ele também dá suporte a transações.</span><span class="sxs-lookup"><span data-stu-id="fc808-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="fc808-193">A configuração padrão para o `NetNamedPipeBinding` é semelhante à configuração fornecida pelo `NetTcpBinding`, mas é mais simples porque a implementação de WCF destina-se apenas para uso na máquina e, consequentemente, há menos recursos expostos.</span><span class="sxs-lookup"><span data-stu-id="fc808-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="fc808-194">A diferença mais notável é que o `securityMode` configuração oferece apenas o `None` e `Transport` opções.</span><span class="sxs-lookup"><span data-stu-id="fc808-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="fc808-195">Suporte de segurança SOAP não é uma opção incluída.</span><span class="sxs-lookup"><span data-stu-id="fc808-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="fc808-196">O comportamento de segurança é configurável usando opcional `securityMode` atributo.</span><span class="sxs-lookup"><span data-stu-id="fc808-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc808-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc808-197">Example</span></span>  
 <span data-ttu-id="fc808-198">O exemplo a seguir demonstra a associação netNamedPipeBinding, que fornece comunicação entre processos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="fc808-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="fc808-199">Pipes nomeados não funcionam em computadores.</span><span class="sxs-lookup"><span data-stu-id="fc808-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="fc808-200">A associação é especificada nos arquivos de configuração do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="fc808-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="fc808-201">O tipo de associação é especificado no `binding` atributo o `<endpoint>` elemento.</span><span class="sxs-lookup"><span data-stu-id="fc808-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="fc808-202">Se você quiser configurar a associação de netNamedPipeBinding e alterar algumas de suas configurações, você deve definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="fc808-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="fc808-203">O ponto de extremidade deve fazer referência a configuração de associação por nome com um `bindingConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="fc808-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="fc808-204">Neste exemplo, a configuração de associação é denominada Binding1.</span><span class="sxs-lookup"><span data-stu-id="fc808-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
        <binding   
                 closeTimeout="00:01:00"  
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
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc808-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc808-205">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [<span data-ttu-id="fc808-206">\<associação ></span><span class="sxs-lookup"><span data-stu-id="fc808-206">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="fc808-207">Associações</span><span class="sxs-lookup"><span data-stu-id="fc808-207">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fc808-208">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="fc808-208">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fc808-209">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fc808-209">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)
