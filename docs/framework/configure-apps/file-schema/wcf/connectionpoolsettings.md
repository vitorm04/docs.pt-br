---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400475"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="02139-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="02139-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="02139-102">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="02139-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
<span data-ttu-id="02139-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="02139-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="02139-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="02139-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="02139-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="02139-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="02139-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="02139-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="02139-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="02139-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="02139-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedPipeTransport**](namedpipetransport.md)</span><span class="sxs-lookup"><span data-stu-id="02139-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)</span></span>\
<span data-ttu-id="02139-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> connectionPoolSettings**</span><span class="sxs-lookup"><span data-stu-id="02139-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02139-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02139-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02139-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="02139-111">Attributes and Elements</span></span>  
 <span data-ttu-id="02139-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="02139-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02139-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="02139-113">Attributes</span></span>  
  
|<span data-ttu-id="02139-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="02139-114">Attribute</span></span>|<span data-ttu-id="02139-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="02139-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="02139-116">Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="02139-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="02139-117">No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="02139-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="02139-118">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="02139-118">The default is a "default" string.</span></span> <span data-ttu-id="02139-119">Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="02139-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="02139-120">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="02139-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="02139-121">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="02139-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="02139-122">Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="02139-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="02139-123">As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="02139-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="02139-124">O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="02139-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="02139-125">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="02139-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="02139-126">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="02139-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="02139-127">Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="02139-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="02139-128">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="02139-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02139-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="02139-129">Child Elements</span></span>  
 <span data-ttu-id="02139-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="02139-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02139-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="02139-131">Parent Elements</span></span>  
  
|<span data-ttu-id="02139-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="02139-132">Element</span></span>|<span data-ttu-id="02139-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="02139-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02139-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="02139-134">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="02139-135">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="02139-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02139-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02139-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="02139-137">Transportes</span><span class="sxs-lookup"><span data-stu-id="02139-137">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="02139-138">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="02139-138">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="02139-139">Associações</span><span class="sxs-lookup"><span data-stu-id="02139-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="02139-140">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="02139-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="02139-141">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="02139-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="02139-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="02139-142">\<customBinding></span></span>](custombinding.md)
