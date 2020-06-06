---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400475"
---
# \<connectionPoolSettings>
<span data-ttu-id="5cf83-101">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="5cf83-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="5cf83-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cf83-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cf83-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5cf83-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5cf83-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5cf83-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cf83-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="5cf83-105">Attributes</span></span>  
  
|<span data-ttu-id="5cf83-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="5cf83-106">Attribute</span></span>|<span data-ttu-id="5cf83-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cf83-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="5cf83-108">Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="5cf83-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="5cf83-109">No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="5cf83-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="5cf83-110">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="5cf83-110">The default is a "default" string.</span></span> <span data-ttu-id="5cf83-111">Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="5cf83-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="5cf83-112">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="5cf83-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="5cf83-113">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="5cf83-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="5cf83-114">Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="5cf83-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="5cf83-115">As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="5cf83-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="5cf83-116">O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="5cf83-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="5cf83-117">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="5cf83-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="5cf83-118">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="5cf83-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="5cf83-119">Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5cf83-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="5cf83-120">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="5cf83-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cf83-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5cf83-121">Child Elements</span></span>  
 <span data-ttu-id="5cf83-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5cf83-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cf83-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5cf83-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5cf83-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5cf83-124">Element</span></span>|<span data-ttu-id="5cf83-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cf83-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="5cf83-126">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="5cf83-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5cf83-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="5cf83-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5cf83-128">Transportes</span><span class="sxs-lookup"><span data-stu-id="5cf83-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="5cf83-129">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="5cf83-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="5cf83-130">Associações</span><span class="sxs-lookup"><span data-stu-id="5cf83-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5cf83-131">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5cf83-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5cf83-132">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5cf83-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
