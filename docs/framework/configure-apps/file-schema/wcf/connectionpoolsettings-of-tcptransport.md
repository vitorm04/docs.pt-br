---
title: <connectionPoolSettings> de <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 787b50296b7ed4f6fdceef244a99dffffae63c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919395"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="3078d-102">\<connectionPoolSettings > de \<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="3078d-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="3078d-103">Especifica configurações de pool de conexões adicionais para um transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="3078d-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="3078d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3078d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3078d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3078d-105">\<bindings></span></span>  
<span data-ttu-id="3078d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3078d-106">\<customBinding></span></span>  
<span data-ttu-id="3078d-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="3078d-107">\<binding></span></span>  
<span data-ttu-id="3078d-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="3078d-108">\<tcpTransport></span></span>  
<span data-ttu-id="3078d-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="3078d-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3078d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3078d-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3078d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3078d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3078d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3078d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3078d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3078d-113">Attributes</span></span>  
  
|<span data-ttu-id="3078d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3078d-114">Attribute</span></span>|<span data-ttu-id="3078d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3078d-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="3078d-116">Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="3078d-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="3078d-117">No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3078d-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="3078d-118">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="3078d-118">The default is a "default" string.</span></span> <span data-ttu-id="3078d-119">Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="3078d-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="3078d-120">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="3078d-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="3078d-121">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="3078d-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="3078d-122">Um <xref:System.TimeSpan> que especifica o tempo após o qual uma conexão ativa é fechada.</span><span class="sxs-lookup"><span data-stu-id="3078d-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="3078d-123">O padrão é 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="3078d-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="3078d-124">Uma conexão é fechada depois de ser retornada ao cache de conexão e não durante a transmissão ativa.</span><span class="sxs-lookup"><span data-stu-id="3078d-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="3078d-125">O cache de conexão usado pelo transporte TCP cria novas conexões conforme necessário para cada ponto de extremidade, até o limite de cache definido por`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="3078d-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="3078d-126">Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="3078d-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="3078d-127">As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="3078d-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="3078d-128">O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="3078d-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="3078d-129">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="3078d-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="3078d-130">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="3078d-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="3078d-131">Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3078d-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="3078d-132">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="3078d-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3078d-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3078d-133">Child Elements</span></span>  
 <span data-ttu-id="3078d-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3078d-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3078d-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3078d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3078d-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="3078d-136">Element</span></span>|<span data-ttu-id="3078d-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="3078d-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3078d-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="3078d-138">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="3078d-139">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="3078d-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3078d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3078d-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3078d-141">Transportes</span><span class="sxs-lookup"><span data-stu-id="3078d-141">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="3078d-142">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="3078d-142">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3078d-143">Associações</span><span class="sxs-lookup"><span data-stu-id="3078d-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3078d-144">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="3078d-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3078d-145">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3078d-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3078d-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3078d-146">\<customBinding></span></span>](custombinding.md)
