---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: d896953a7ed31fdaf5f357a8721c7d085d50bc56
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400065"
---
# <a name="peertransport"></a><span data-ttu-id="48ad0-101">\<> peerTransport</span><span class="sxs-lookup"><span data-stu-id="48ad0-101">\<peerTransport></span></span>
<span data-ttu-id="48ad0-102">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="48ad0-102">Defines a peer transport for a custom binding.</span></span>  
  
<span data-ttu-id="48ad0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48ad0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48ad0-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="48ad0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="48ad0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="48ad0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="48ad0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="48ad0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="48ad0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="48ad0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="48ad0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> peerTransport**</span><span class="sxs-lookup"><span data-stu-id="48ad0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ad0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48ad0-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48ad0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48ad0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="48ad0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="48ad0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48ad0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="48ad0-112">Attributes</span></span>  
  
|<span data-ttu-id="48ad0-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="48ad0-113">Attribute</span></span>|<span data-ttu-id="48ad0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="48ad0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48ad0-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="48ad0-115">listenIpAddress</span></span>|<span data-ttu-id="48ad0-116">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="48ad0-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="48ad0-117">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="48ad0-117">The default is `null`.</span></span>|  
|<span data-ttu-id="48ad0-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="48ad0-118">maxBufferPoolSize</span></span>|<span data-ttu-id="48ad0-119">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="48ad0-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="48ad0-120">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="48ad0-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="48ad0-121">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="48ad0-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="48ad0-122">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="48ad0-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="48ad0-123">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="48ad0-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="48ad0-124">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="48ad0-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="48ad0-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="48ad0-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="48ad0-126">Um inteiro positivo que define o tamanho máximo da mensagem em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="48ad0-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="48ad0-127">O remetente de uma mensagem recebe uma falha de SOAP quando a mensagem é muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="48ad0-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="48ad0-128">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="48ad0-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="48ad0-129">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="48ad0-129">The default is 65536.</span></span>|  
|<span data-ttu-id="48ad0-130">porta</span><span class="sxs-lookup"><span data-stu-id="48ad0-130">port</span></span>|<span data-ttu-id="48ad0-131">Um inteiro que especifica a porta da interface de rede na qual essa associação processará as mensagens TCP do canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="48ad0-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="48ad0-132">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="48ad0-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="48ad0-133">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="48ad0-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48ad0-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48ad0-134">Child Elements</span></span>  
  
|<span data-ttu-id="48ad0-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="48ad0-135">Element</span></span>|<span data-ttu-id="48ad0-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="48ad0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48ad0-137">\<security></span><span class="sxs-lookup"><span data-stu-id="48ad0-137">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="48ad0-138">Define as configurações de segurança para esse transporte.</span><span class="sxs-lookup"><span data-stu-id="48ad0-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="48ad0-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="48ad0-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48ad0-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48ad0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="48ad0-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="48ad0-141">Element</span></span>|<span data-ttu-id="48ad0-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="48ad0-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48ad0-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="48ad0-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="48ad0-144">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="48ad0-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48ad0-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="48ad0-145">Remarks</span></span>  
 <span data-ttu-id="48ad0-146">Esse transporte não pode ser usado com contratos que têm operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="48ad0-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ad0-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48ad0-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="48ad0-148">Transportes</span><span class="sxs-lookup"><span data-stu-id="48ad0-148">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="48ad0-149">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="48ad0-149">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="48ad0-150">Associações</span><span class="sxs-lookup"><span data-stu-id="48ad0-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48ad0-151">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="48ad0-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="48ad0-152">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="48ad0-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="48ad0-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="48ad0-153">\<customBinding></span></span>](custombinding.md)
