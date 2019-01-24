---
title: '&lt;connectionPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 1e3001f60ae0f18fee88678cae1e9e55d90822c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526750"
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="4317c-102">&lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="4317c-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="4317c-103">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="4317c-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="4317c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4317c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4317c-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4317c-105">\<bindings></span></span>  
<span data-ttu-id="4317c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4317c-106">\<customBinding></span></span>  
<span data-ttu-id="4317c-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="4317c-107">\<binding></span></span>  
<span data-ttu-id="4317c-108">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="4317c-108">\<namePipeTransport></span></span>  
<span data-ttu-id="4317c-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="4317c-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4317c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4317c-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4317c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4317c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4317c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4317c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4317c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="4317c-113">Attributes</span></span>  
  
|<span data-ttu-id="4317c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="4317c-114">Attribute</span></span>|<span data-ttu-id="4317c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4317c-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="4317c-116">Uma cadeia de caracteres que define o nome do pool de conexão usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="4317c-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="4317c-117">No modo de streaming, as conexões não são compartilhadas, o que significa que o pooling de conexão está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="4317c-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="4317c-118">O padrão é uma cadeia de caracteres "default".</span><span class="sxs-lookup"><span data-stu-id="4317c-118">The default is a "default" string.</span></span> <span data-ttu-id="4317c-119">Você pode modificar esse valor para isolar as conexões para um determinado cliente em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="4317c-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="4317c-120">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="4317c-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="4317c-121">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="4317c-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="4317c-122">Um inteiro positivo que especifica o número máximo de conexões para um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="4317c-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="4317c-123">Conexões além do limite são enfileiradas até que um espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="4317c-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="4317c-124">O `idleTimeout` limita a duração em que as conexões permanecem na fila antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="4317c-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="4317c-125">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="4317c-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="4317c-126">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="4317c-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="4317c-127">Se esse valor for excedido, fazendo com que as conexões de cliente mais ativas, o serviço pode parecer não estar respondendo ao cliente.</span><span class="sxs-lookup"><span data-stu-id="4317c-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="4317c-128">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente esperado para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="4317c-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4317c-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4317c-129">Child Elements</span></span>  
 <span data-ttu-id="4317c-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4317c-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4317c-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4317c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="4317c-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="4317c-132">Element</span></span>|<span data-ttu-id="4317c-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="4317c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4317c-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="4317c-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="4317c-135">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="4317c-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4317c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4317c-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4317c-137">Transportes</span><span class="sxs-lookup"><span data-stu-id="4317c-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="4317c-138">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="4317c-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4317c-139">Associações</span><span class="sxs-lookup"><span data-stu-id="4317c-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4317c-140">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="4317c-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4317c-141">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="4317c-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4317c-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4317c-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
