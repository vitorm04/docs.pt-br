---
title: '&lt;connectionPoolSettings&gt; de &lt;tcpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61e4036ef5fe4731316aabeed2e3208422894194
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="35dd1-102">&lt;connectionPoolSettings&gt; de &lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="35dd1-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="35dd1-103">Especifica as configurações do pool de conexão adicionais para um transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="35dd1-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="35dd1-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="35dd1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="35dd1-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="35dd1-105">\<bindings></span></span>  
<span data-ttu-id="35dd1-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35dd1-106">\<customBinding></span></span>  
<span data-ttu-id="35dd1-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="35dd1-107">\<binding></span></span>  
<span data-ttu-id="35dd1-108">\<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="35dd1-108">\<tcpTransport></span></span>  
<span data-ttu-id="35dd1-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="35dd1-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35dd1-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35dd1-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35dd1-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="35dd1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="35dd1-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="35dd1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35dd1-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="35dd1-113">Attributes</span></span>  
  
|<span data-ttu-id="35dd1-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="35dd1-114">Attribute</span></span>|<span data-ttu-id="35dd1-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="35dd1-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="35dd1-116">Uma cadeia de caracteres que define o nome do pool de conexão usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="35dd1-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="35dd1-117">No modo de fluxo, conexões não são compartilhados, o que significa que o pool de conexão está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="35dd1-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="35dd1-118">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="35dd1-118">The default is a "default" string.</span></span> <span data-ttu-id="35dd1-119">Você pode modificar esse valor para isolar as conexões para um determinado cliente em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="35dd1-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="35dd1-120">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="35dd1-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="35dd1-121">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="35dd1-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="35dd1-122">Um <xref:System.TimeSpan> que especifica o tempo após o qual uma conexão ativa é fechada.</span><span class="sxs-lookup"><span data-stu-id="35dd1-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="35dd1-123">O padrão é 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="35dd1-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="35dd1-124">Uma conexão é fechada depois que ele foi retornado para o cache de conexão e não durante a transmissão de ativo.</span><span class="sxs-lookup"><span data-stu-id="35dd1-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="35dd1-125">O cache de conexão usado pelo transporte TCP cria novas conexões conforme necessário para cada ponto de extremidade, até o limite de cache é definido por`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="35dd1-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="35dd1-126">Um inteiro positivo que especifica o número máximo de conexões para um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="35dd1-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="35dd1-127">Conexões ultrapassem o limite são enfileiradas até que um espaço abaixo do limite se torne disponível.</span><span class="sxs-lookup"><span data-stu-id="35dd1-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="35dd1-128">O `idleTimeout` limita a duração em que conexões permanecem na fila antes de uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="35dd1-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="35dd1-129">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="35dd1-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="35dd1-130">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="35dd1-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="35dd1-131">Se esse valor for excedido fazendo mais ativas conexões de cliente, o serviço pode parecer não estar respondendo ao cliente.</span><span class="sxs-lookup"><span data-stu-id="35dd1-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="35dd1-132">Nesse caso, esse valor deverá ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperado para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="35dd1-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35dd1-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="35dd1-133">Child Elements</span></span>  
 <span data-ttu-id="35dd1-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="35dd1-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35dd1-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="35dd1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="35dd1-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="35dd1-136">Element</span></span>|<span data-ttu-id="35dd1-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="35dd1-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35dd1-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="35dd1-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="35dd1-139">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="35dd1-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35dd1-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35dd1-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="35dd1-141">Transportes</span><span class="sxs-lookup"><span data-stu-id="35dd1-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="35dd1-142">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="35dd1-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="35dd1-143">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="35dd1-143">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="35dd1-144">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="35dd1-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="35dd1-145">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="35dd1-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="35dd1-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35dd1-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
