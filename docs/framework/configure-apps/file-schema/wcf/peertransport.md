---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736515"
---
# \<peerTransport>
<span data-ttu-id="6c923-101">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6c923-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="6c923-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c923-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c923-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c923-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6c923-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c923-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c923-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c923-105">Attributes</span></span>  
  
|<span data-ttu-id="6c923-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="6c923-106">Attribute</span></span>|<span data-ttu-id="6c923-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c923-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c923-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="6c923-108">listenIpAddress</span></span>|<span data-ttu-id="6c923-109">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="6c923-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="6c923-110">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="6c923-110">The default is `null`.</span></span>|  
|<span data-ttu-id="6c923-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6c923-111">maxBufferPoolSize</span></span>|<span data-ttu-id="6c923-112">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="6c923-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="6c923-113">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="6c923-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="6c923-114">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="6c923-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="6c923-115">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="6c923-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6c923-116">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="6c923-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6c923-117">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="6c923-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6c923-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6c923-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="6c923-119">Um inteiro positivo que define o tamanho máximo da mensagem em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="6c923-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="6c923-120">O remetente de uma mensagem recebe uma falha de SOAP quando a mensagem é muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="6c923-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="6c923-121">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c923-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6c923-122">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="6c923-122">The default is 65536.</span></span>|  
|<span data-ttu-id="6c923-123">porta</span><span class="sxs-lookup"><span data-stu-id="6c923-123">port</span></span>|<span data-ttu-id="6c923-124">Um inteiro que especifica a porta da interface de rede na qual essa associação processará as mensagens TCP do canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="6c923-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="6c923-125">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="6c923-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="6c923-126">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="6c923-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c923-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c923-127">Child Elements</span></span>  
  
|<span data-ttu-id="6c923-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c923-128">Element</span></span>|<span data-ttu-id="6c923-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c923-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="6c923-130">Define as configurações de segurança para esse transporte.</span><span class="sxs-lookup"><span data-stu-id="6c923-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="6c923-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="6c923-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c923-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c923-132">Parent Elements</span></span>  
  
|<span data-ttu-id="6c923-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c923-133">Element</span></span>|<span data-ttu-id="6c923-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c923-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="6c923-135">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6c923-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c923-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c923-136">Remarks</span></span>  
 <span data-ttu-id="6c923-137">Esse transporte não pode ser usado com contratos que têm operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="6c923-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c923-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c923-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6c923-139">Transportes</span><span class="sxs-lookup"><span data-stu-id="6c923-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="6c923-140">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="6c923-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="6c923-141">Associações</span><span class="sxs-lookup"><span data-stu-id="6c923-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6c923-142">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="6c923-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6c923-143">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="6c923-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
