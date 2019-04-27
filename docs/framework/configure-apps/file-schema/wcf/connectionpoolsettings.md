---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: b1ff302a46605cb78fe567a63f66723ed757f147
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704304"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="d0943-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="d0943-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="d0943-102">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="d0943-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="d0943-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0943-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d0943-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d0943-104">\<bindings></span></span>  
<span data-ttu-id="d0943-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d0943-105">\<customBinding></span></span>  
<span data-ttu-id="d0943-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="d0943-106">\<binding></span></span>  
<span data-ttu-id="d0943-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="d0943-107">\<namePipeTransport></span></span>  
<span data-ttu-id="d0943-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="d0943-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0943-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0943-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0943-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0943-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d0943-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0943-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0943-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0943-112">Attributes</span></span>  
  
|<span data-ttu-id="d0943-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0943-113">Attribute</span></span>|<span data-ttu-id="d0943-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0943-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="d0943-115">Uma cadeia de caracteres que define o nome do pool de conexão usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="d0943-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="d0943-116">No modo de streaming, as conexões não são compartilhadas, o que significa que o pooling de conexão está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="d0943-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="d0943-117">O padrão é uma cadeia de caracteres "default".</span><span class="sxs-lookup"><span data-stu-id="d0943-117">The default is a "default" string.</span></span> <span data-ttu-id="d0943-118">Você pode modificar esse valor para isolar as conexões para um determinado cliente em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="d0943-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="d0943-119">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="d0943-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="d0943-120">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="d0943-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="d0943-121">Um inteiro positivo que especifica o número máximo de conexões para um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d0943-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="d0943-122">Conexões além do limite são enfileiradas até que um espaço abaixo do limite fica disponível.</span><span class="sxs-lookup"><span data-stu-id="d0943-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="d0943-123">O `idleTimeout` limita a duração em que as conexões permanecem na fila antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="d0943-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="d0943-124">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="d0943-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="d0943-125">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="d0943-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="d0943-126">Se esse valor for excedido, fazendo com que as conexões de cliente mais ativas, o serviço pode parecer não estar respondendo ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d0943-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="d0943-127">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente esperado para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="d0943-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0943-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0943-128">Child Elements</span></span>  
 <span data-ttu-id="d0943-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d0943-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0943-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0943-130">Parent Elements</span></span>  
  
|<span data-ttu-id="d0943-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0943-131">Element</span></span>|<span data-ttu-id="d0943-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0943-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0943-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="d0943-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="d0943-134">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="d0943-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0943-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0943-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d0943-136">Transportes</span><span class="sxs-lookup"><span data-stu-id="d0943-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="d0943-137">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="d0943-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d0943-138">Associações</span><span class="sxs-lookup"><span data-stu-id="d0943-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d0943-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d0943-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d0943-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d0943-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d0943-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d0943-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
