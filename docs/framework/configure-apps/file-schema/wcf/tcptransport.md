---
title: '&lt;tcpTransport&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f534bab962e83f76dab7e411cc3c2ca14779df9
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="lttcptransportgt"></a><span data-ttu-id="36ed1-102">&lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="36ed1-102">&lt;tcpTransport&gt;</span></span>
<span data-ttu-id="36ed1-103">Define um transporte TCP que pode ser usado por um canal transferir mensagens para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="36ed1-103">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
 <span data-ttu-id="36ed1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="36ed1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="36ed1-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="36ed1-105">\<bindings></span></span>  
<span data-ttu-id="36ed1-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="36ed1-106">\<customBinding></span></span>  
<span data-ttu-id="36ed1-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="36ed1-107">\<binding></span></span>  
<span data-ttu-id="36ed1-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="36ed1-108">\<tcpTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ed1-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36ed1-109">Syntax</span></span>  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36ed1-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="36ed1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="36ed1-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="36ed1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36ed1-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="36ed1-112">Attributes</span></span>  
  
|<span data-ttu-id="36ed1-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="36ed1-113">Attribute</span></span>|<span data-ttu-id="36ed1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="36ed1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36ed1-115">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="36ed1-115">channelInitializationTimeout</span></span>|<span data-ttu-id="36ed1-116">Obtém ou define o limite de tempo de inicialização de um canal para serem aceitos.</span><span class="sxs-lookup"><span data-stu-id="36ed1-116">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="36ed1-117">O tempo máximo de um canal pode estar no estado de inicialização antes de ser desconectada em segundos.</span><span class="sxs-lookup"><span data-stu-id="36ed1-117">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="36ed1-118">Essa cota inclui o tempo que uma conexão TCP pode tomar para autenticar usando o .net Message Framing protocolo.</span><span class="sxs-lookup"><span data-stu-id="36ed1-118">This quota includes the time a TCP connection can take to authenticate itself using the .Net Message Framing protocol.</span></span> <span data-ttu-id="36ed1-119">Um cliente precisa enviar alguns dados iniciais antes que o servidor tenha informações suficientes para executar a autenticação.</span><span class="sxs-lookup"><span data-stu-id="36ed1-119">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="36ed1-120">O padrão é 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="36ed1-120">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="36ed1-121">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="36ed1-121">connectionBufferSize</span></span>|<span data-ttu-id="36ed1-122">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="36ed1-122">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="36ed1-123">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="36ed1-123">hostNameComparisonMode</span></span>|<span data-ttu-id="36ed1-124">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="36ed1-124">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="36ed1-125">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="36ed1-125">listenBacklog</span></span>|<span data-ttu-id="36ed1-126">O número máximo de solicitações de conexão em fila que podem estar pendentes para um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="36ed1-126">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="36ed1-127">O `connectionLeaseTimeout` atributo limita a duração em que o cliente aguardará para ser conectado antes de gerar uma exceção de conexão.</span><span class="sxs-lookup"><span data-stu-id="36ed1-127">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="36ed1-128">Esta é uma propriedade de nível de soquete que controla o número máximo de solicitações de conexão em fila que podem estar pendentes para um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="36ed1-128">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="36ed1-129">Quando ListenBacklog é muito baixo, o WCF parar de aceitar solicitações e descartar, portanto, novas conexões até que o servidor confirma a algumas das conexões existentes na fila. O padrão é 16 \* número de processadores.</span><span class="sxs-lookup"><span data-stu-id="36ed1-129">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections .The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="36ed1-130">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="36ed1-130">manualAddressing</span></span>|<span data-ttu-id="36ed1-131">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="36ed1-131">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="36ed1-132">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="36ed1-132">maxBufferPoolSize</span></span>|<span data-ttu-id="36ed1-133">Obtém ou define o tamanho máximo de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="36ed1-133">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="36ed1-134">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="36ed1-134">maxBufferSize</span></span>|<span data-ttu-id="36ed1-135">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="36ed1-135">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="36ed1-136">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="36ed1-136">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="36ed1-137">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="36ed1-137">maxOutputDelay</span></span>|<span data-ttu-id="36ed1-138">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="36ed1-138">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="36ed1-139">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="36ed1-139">maxPendingAccepts</span></span>|<span data-ttu-id="36ed1-140">Obtém ou define o número máximo de operações de aceitação assíncrona pendentes que estão disponíveis para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="36ed1-140">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="36ed1-141">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="36ed1-141">maxPendingConnections</span></span>|<span data-ttu-id="36ed1-142">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="36ed1-142">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="36ed1-143">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="36ed1-143">maxReceivedMessageSize</span></span>|<span data-ttu-id="36ed1-144">Obtém e define o tamanho máximo de mensagem permitido que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="36ed1-144">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="36ed1-145">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="36ed1-145">portSharingEnabled</span></span>|<span data-ttu-id="36ed1-146">Um valor booleano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="36ed1-146">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="36ed1-147">Se isso for `false`, cada associação usará sua própria porta exclusiva.</span><span class="sxs-lookup"><span data-stu-id="36ed1-147">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="36ed1-148">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="36ed1-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="36ed1-149">Essa configuração é relevante apenas para serviços.</span><span class="sxs-lookup"><span data-stu-id="36ed1-149">This setting is relevant only to services.</span></span> <span data-ttu-id="36ed1-150">Os clientes não são afetados.</span><span class="sxs-lookup"><span data-stu-id="36ed1-150">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="36ed1-151">Usar essa configuração exige a habilitação de serviço de compartilhamento de porta de TCP do Windows Communication Foundation (WCF), alterando o tipo de inicialização para Manual ou automático</span><span class="sxs-lookup"><span data-stu-id="36ed1-151">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="36ed1-152">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="36ed1-152">teredoEnabled</span></span>|<span data-ttu-id="36ed1-153">Um valor booleano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="36ed1-153">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="36ed1-154">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="36ed1-154">The default is `false`.</span></span><br /><br /> <span data-ttu-id="36ed1-155">Essa propriedade permite que o Teredo para o soquete TCP subjacente.</span><span class="sxs-lookup"><span data-stu-id="36ed1-155">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="36ed1-156">Para obter mais informações, consulte [visão geral de Teredo](http://go.microsoft.com/fwlink/?LinkId=95339).</span><span class="sxs-lookup"><span data-stu-id="36ed1-156">For more information, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span><br /><br /> <span data-ttu-id="36ed1-157">Essa propriedade é aplicável apenas em [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] e [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36ed1-157">This property is applicable only on [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] and [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span></span> [!INCLUDE[wv](../../../../../includes/wv-md.md)]<span data-ttu-id="36ed1-158"> tem uma opção de configuração de máquina para o Teredo, portanto ao executar o Vista, essa propriedade será ignorada.</span><span class="sxs-lookup"><span data-stu-id="36ed1-158"> has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="36ed1-159">Teredo exige que as máquinas cliente e de serviço tem a pilha do IPv6 Microsoft instalado e configurado corretamente para o uso de Teredo.</span><span class="sxs-lookup"><span data-stu-id="36ed1-159">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span> <span data-ttu-id="36ed1-160">Para obter mais informações sobre como configurar o Teredo, consulte [visão geral de Teredo](http://go.microsoft.com/fwlink/?LinkId=95339).</span><span class="sxs-lookup"><span data-stu-id="36ed1-160">For more information about configuring Teredo, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span> <span data-ttu-id="36ed1-161">Para obter mais informações, consulte [centros de tecnologia do Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=49888).</span><span class="sxs-lookup"><span data-stu-id="36ed1-161">For more information, see [Windows Server 2003 Technology Centers](http://go.microsoft.com/fwlink/?LinkId=49888).</span></span>|  
|<span data-ttu-id="36ed1-162">transferMode</span><span class="sxs-lookup"><span data-stu-id="36ed1-162">transferMode</span></span>|<span data-ttu-id="36ed1-163">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="36ed1-163">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="36ed1-164">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="36ed1-164">connectionPoolSettings</span></span>|<span data-ttu-id="36ed1-165">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="36ed1-165">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36ed1-166">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="36ed1-166">Child Elements</span></span>  
 <span data-ttu-id="36ed1-167">Nenhum</span><span class="sxs-lookup"><span data-stu-id="36ed1-167">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36ed1-168">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="36ed1-168">Parent Elements</span></span>  
  
|<span data-ttu-id="36ed1-169">Elemento</span><span class="sxs-lookup"><span data-stu-id="36ed1-169">Element</span></span>|<span data-ttu-id="36ed1-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="36ed1-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36ed1-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="36ed1-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="36ed1-172">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="36ed1-172">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36ed1-173">Comentários</span><span class="sxs-lookup"><span data-stu-id="36ed1-173">Remarks</span></span>  
 <span data-ttu-id="36ed1-174">Esse transporte usa URIs no formato "net.tcp://hostname: porta/caminho".</span><span class="sxs-lookup"><span data-stu-id="36ed1-174">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="36ed1-175">Outros componentes do URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="36ed1-175">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="36ed1-176">O `tcpTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="36ed1-176">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="36ed1-177">Esse transporte é otimizado para comunicação WCF-WCF.</span><span class="sxs-lookup"><span data-stu-id="36ed1-177">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ed1-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36ed1-178">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="36ed1-179">Transportes</span><span class="sxs-lookup"><span data-stu-id="36ed1-179">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="36ed1-180">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="36ed1-180">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="36ed1-181">Associações</span><span class="sxs-lookup"><span data-stu-id="36ed1-181">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="36ed1-182">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="36ed1-182">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="36ed1-183">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="36ed1-183">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="36ed1-184">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="36ed1-184">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
