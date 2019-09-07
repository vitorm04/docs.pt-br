---
title: <connectionPoolSettings> de <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: f9b0fff741c32c1a3d6f9461f478e89acc18114e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398090"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="dcfe5-102">\<connectionPoolSettings > de \<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="dcfe5-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="dcfe5-103">Especifica configurações de pool de conexões adicionais para um transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
<span data-ttu-id="dcfe5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dcfe5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dcfe5-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dcfe5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dcfe5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="dcfe5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dcfe5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="dcfe5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="dcfe5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="dcfe5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="dcfe5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tcpTransport**](tcptransport.md)</span><span class="sxs-lookup"><span data-stu-id="dcfe5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)</span></span>\
<span data-ttu-id="dcfe5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> connectionPoolSettings**</span><span class="sxs-lookup"><span data-stu-id="dcfe5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcfe5-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcfe5-111">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcfe5-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dcfe5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dcfe5-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcfe5-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="dcfe5-114">Attributes</span></span>  
  
|<span data-ttu-id="dcfe5-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="dcfe5-115">Attribute</span></span>|<span data-ttu-id="dcfe5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcfe5-116">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="dcfe5-117">Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-117">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="dcfe5-118">No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-118">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="dcfe5-119">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="dcfe5-119">The default is a "default" string.</span></span> <span data-ttu-id="dcfe5-120">Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-120">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="dcfe5-121">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-121">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="dcfe5-122">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-122">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="dcfe5-123">Um <xref:System.TimeSpan> que especifica o tempo após o qual uma conexão ativa é fechada.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-123">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="dcfe5-124">O padrão é 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-124">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="dcfe5-125">Uma conexão é fechada depois de ser retornada ao cache de conexão e não durante a transmissão ativa.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-125">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="dcfe5-126">O cache de conexão usado pelo transporte TCP cria novas conexões conforme necessário para cada ponto de extremidade, até o limite de cache definido por`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="dcfe5-126">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="dcfe5-127">Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-127">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="dcfe5-128">As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-128">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="dcfe5-129">O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-129">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="dcfe5-130">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-130">The default is 10.</span></span><br /><br /> <span data-ttu-id="dcfe5-131">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-131">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="dcfe5-132">Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-132">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="dcfe5-133">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-133">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcfe5-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dcfe5-134">Child Elements</span></span>  
 <span data-ttu-id="dcfe5-135">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcfe5-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dcfe5-136">Parent Elements</span></span>  
  
|<span data-ttu-id="dcfe5-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="dcfe5-137">Element</span></span>|<span data-ttu-id="dcfe5-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcfe5-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcfe5-139">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="dcfe5-139">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="dcfe5-140">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-140">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcfe5-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcfe5-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="dcfe5-142">Transportes</span><span class="sxs-lookup"><span data-stu-id="dcfe5-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="dcfe5-143">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="dcfe5-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="dcfe5-144">Associações</span><span class="sxs-lookup"><span data-stu-id="dcfe5-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dcfe5-145">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="dcfe5-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="dcfe5-146">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="dcfe5-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="dcfe5-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="dcfe5-147">\<customBinding></span></span>](custombinding.md)
