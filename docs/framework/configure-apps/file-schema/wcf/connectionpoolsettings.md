---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925969"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="82c50-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="82c50-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="82c50-102">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="82c50-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="82c50-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="82c50-103">\<system.serviceModel></span></span>  
<span data-ttu-id="82c50-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="82c50-104">\<bindings></span></span>  
<span data-ttu-id="82c50-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="82c50-105">\<customBinding></span></span>  
<span data-ttu-id="82c50-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="82c50-106">\<binding></span></span>  
<span data-ttu-id="82c50-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="82c50-107">\<namePipeTransport></span></span>  
<span data-ttu-id="82c50-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="82c50-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c50-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82c50-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82c50-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="82c50-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82c50-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="82c50-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82c50-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="82c50-112">Attributes</span></span>  
  
|<span data-ttu-id="82c50-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="82c50-113">Attribute</span></span>|<span data-ttu-id="82c50-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="82c50-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="82c50-115">Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="82c50-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="82c50-116">No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="82c50-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="82c50-117">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="82c50-117">The default is a "default" string.</span></span> <span data-ttu-id="82c50-118">Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="82c50-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="82c50-119">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="82c50-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="82c50-120">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="82c50-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="82c50-121">Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="82c50-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="82c50-122">As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="82c50-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="82c50-123">O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="82c50-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="82c50-124">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="82c50-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="82c50-125">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="82c50-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="82c50-126">Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="82c50-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="82c50-127">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="82c50-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82c50-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="82c50-128">Child Elements</span></span>  
 <span data-ttu-id="82c50-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="82c50-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82c50-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="82c50-130">Parent Elements</span></span>  
  
|<span data-ttu-id="82c50-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="82c50-131">Element</span></span>|<span data-ttu-id="82c50-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="82c50-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82c50-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="82c50-133">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="82c50-134">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="82c50-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82c50-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82c50-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="82c50-136">Transportes</span><span class="sxs-lookup"><span data-stu-id="82c50-136">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="82c50-137">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="82c50-137">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="82c50-138">Associações</span><span class="sxs-lookup"><span data-stu-id="82c50-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="82c50-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="82c50-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="82c50-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="82c50-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="82c50-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="82c50-141">\<customBinding></span></span>](custombinding.md)
