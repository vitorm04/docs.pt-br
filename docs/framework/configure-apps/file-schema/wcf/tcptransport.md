---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 6d4302e1840f58e2daad855942493cc96b7d5e34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158663"
---
# \<tcpTransport>

<span data-ttu-id="688b1-101">Define um transporte TCP que pode ser usado por um canal para transferir mensagens para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="688b1-101">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="688b1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="688b1-102">Syntax</span></span>  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
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
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="688b1-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="688b1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="688b1-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="688b1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="688b1-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="688b1-105">Attributes</span></span>  
  
|<span data-ttu-id="688b1-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="688b1-106">Attribute</span></span>|<span data-ttu-id="688b1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="688b1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="688b1-108">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="688b1-108">channelInitializationTimeout</span></span>|<span data-ttu-id="688b1-109">Obtém ou define o limite de tempo para inicializar um canal a ser aceito.</span><span class="sxs-lookup"><span data-stu-id="688b1-109">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="688b1-110">O tempo máximo que um canal pode estar no estado de inicialização antes de ser desconectado em segundos.</span><span class="sxs-lookup"><span data-stu-id="688b1-110">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="688b1-111">Essa cota inclui o tempo que uma conexão TCP pode tomar para se autenticar usando o protocolo de enquadramento de mensagens .NET.</span><span class="sxs-lookup"><span data-stu-id="688b1-111">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="688b1-112">Um cliente precisa enviar alguns dados iniciais antes que o servidor tenha informações suficientes para executar a autenticação.</span><span class="sxs-lookup"><span data-stu-id="688b1-112">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="688b1-113">O padrão é 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="688b1-113">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="688b1-114">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="688b1-114">connectionBufferSize</span></span>|<span data-ttu-id="688b1-115">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="688b1-115">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="688b1-116">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="688b1-116">hostNameComparisonMode</span></span>|<span data-ttu-id="688b1-117">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="688b1-117">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="688b1-118">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="688b1-118">listenBacklog</span></span>|<span data-ttu-id="688b1-119">O número máximo de solicitações de conexão em fila que podem estar pendentes para um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="688b1-119">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="688b1-120">O `connectionLeaseTimeout` atributo limita a duração que o cliente aguardará para ser conectado antes de lançar uma exceção de conexão.</span><span class="sxs-lookup"><span data-stu-id="688b1-120">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="688b1-121">Essa é uma propriedade de nível de soquete que controla o número máximo de solicitações de conexão em fila que podem estar pendentes para um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="688b1-121">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="688b1-122">Quando ListenBacklog for muito baixo, o WCF deixará de aceitar solicitações e, portanto, descartará novas conexões até que o servidor reconheça algumas das conexões em fila existentes.</span><span class="sxs-lookup"><span data-stu-id="688b1-122">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="688b1-123">O padrão é 16 \* número de processadores.</span><span class="sxs-lookup"><span data-stu-id="688b1-123">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="688b1-124">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="688b1-124">manualAddressing</span></span>|<span data-ttu-id="688b1-125">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="688b1-125">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="688b1-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="688b1-126">maxBufferPoolSize</span></span>|<span data-ttu-id="688b1-127">Obtém ou define o tamanho máximo de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="688b1-127">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="688b1-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="688b1-128">maxBufferSize</span></span>|<span data-ttu-id="688b1-129">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="688b1-129">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="688b1-130">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="688b1-130">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="688b1-131">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="688b1-131">maxOutputDelay</span></span>|<span data-ttu-id="688b1-132">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="688b1-132">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="688b1-133">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="688b1-133">maxPendingAccepts</span></span>|<span data-ttu-id="688b1-134">Obtém ou define o número máximo de operações de aceitação assíncrona pendentes que estão disponíveis para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="688b1-134">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="688b1-135">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="688b1-135">maxPendingConnections</span></span>|<span data-ttu-id="688b1-136">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="688b1-136">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="688b1-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="688b1-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="688b1-138">Obtém e define o tamanho máximo de mensagem permitido que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="688b1-138">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="688b1-139">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="688b1-139">portSharingEnabled</span></span>|<span data-ttu-id="688b1-140">Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="688b1-140">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="688b1-141">Se isso for `false` , cada associação usará sua própria porta exclusiva.</span><span class="sxs-lookup"><span data-stu-id="688b1-141">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="688b1-142">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="688b1-142">The default is `false`.</span></span><br /><br /> <span data-ttu-id="688b1-143">Essa configuração é relevante apenas para serviços do.</span><span class="sxs-lookup"><span data-stu-id="688b1-143">This setting is relevant only to services.</span></span> <span data-ttu-id="688b1-144">Os clientes não são afetados.</span><span class="sxs-lookup"><span data-stu-id="688b1-144">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="688b1-145">O uso dessa configuração requer a habilitação do serviço de compartilhamento de porta TCP Windows Communication Foundation (WCF) alterando seu tipo de inicialização para manual ou automático</span><span class="sxs-lookup"><span data-stu-id="688b1-145">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="688b1-146">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="688b1-146">teredoEnabled</span></span>|<span data-ttu-id="688b1-147">Um valor booliano que especifica se Teredo (uma tecnologia para endereçar clientes que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="688b1-147">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="688b1-148">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="688b1-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="688b1-149">Essa propriedade habilita a Teredo para o soquete TCP subjacente.</span><span class="sxs-lookup"><span data-stu-id="688b1-149">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="688b1-150">Para obter mais informações, consulte [visão geral do Teredo](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="688b1-150">For more information, see [Teredo Overview](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span></span><br /><br /> <span data-ttu-id="688b1-151">Essa propriedade é aplicável somente no Windows XP SP2 e no Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="688b1-151">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="688b1-152">O Windows Vista tem uma opção de configuração de todo o computador para Teredo, portanto, ao executar o vista, essa propriedade é ignorada.</span><span class="sxs-lookup"><span data-stu-id="688b1-152">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="688b1-153">O Teredo requer que o cliente e as máquinas de serviço tenham a pilha do Microsoft IPv6 instalada e configurada corretamente para uso de Teredo.</span><span class="sxs-lookup"><span data-stu-id="688b1-153">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span>|  
|<span data-ttu-id="688b1-154">transferMode</span><span class="sxs-lookup"><span data-stu-id="688b1-154">transferMode</span></span>|<span data-ttu-id="688b1-155">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="688b1-155">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="688b1-156">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="688b1-156">connectionPoolSettings</span></span>|<span data-ttu-id="688b1-157">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="688b1-157">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="688b1-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="688b1-158">Child Elements</span></span>  

 <span data-ttu-id="688b1-159">Nenhum</span><span class="sxs-lookup"><span data-stu-id="688b1-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="688b1-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="688b1-160">Parent Elements</span></span>  
  
|<span data-ttu-id="688b1-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="688b1-161">Element</span></span>|<span data-ttu-id="688b1-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="688b1-162">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="688b1-163">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="688b1-163">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="688b1-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="688b1-164">Remarks</span></span>  

 <span data-ttu-id="688b1-165">Esse transporte usa URIs no formato "net. TCP://hostname: port/path".</span><span class="sxs-lookup"><span data-stu-id="688b1-165">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="688b1-166">Outros componentes de URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="688b1-166">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="688b1-167">O `tcpTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="688b1-167">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="688b1-168">Esse transporte é otimizado para comunicação WCF para WCF.</span><span class="sxs-lookup"><span data-stu-id="688b1-168">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688b1-169">Confira também</span><span class="sxs-lookup"><span data-stu-id="688b1-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="688b1-170">Transportes</span><span class="sxs-lookup"><span data-stu-id="688b1-170">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="688b1-171">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="688b1-171">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="688b1-172">Associações</span><span class="sxs-lookup"><span data-stu-id="688b1-172">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="688b1-173">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="688b1-173">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="688b1-174">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="688b1-174">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
