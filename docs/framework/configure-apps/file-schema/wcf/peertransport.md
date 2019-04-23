---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 6765259f290047a4199a422b4ad0cced2ffee9ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179823"
---
# <a name="peertransport"></a><span data-ttu-id="d286f-101">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="d286f-101">\<peerTransport></span></span>
<span data-ttu-id="d286f-102">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d286f-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="d286f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d286f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d286f-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d286f-104">\<bindings></span></span>  
<span data-ttu-id="d286f-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d286f-105">\<customBinding></span></span>  
<span data-ttu-id="d286f-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="d286f-106">\<binding></span></span>  
<span data-ttu-id="d286f-107">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="d286f-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d286f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d286f-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d286f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d286f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d286f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d286f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d286f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d286f-111">Attributes</span></span>  
  
|<span data-ttu-id="d286f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="d286f-112">Attribute</span></span>|<span data-ttu-id="d286f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d286f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d286f-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="d286f-114">listenIpAddress</span></span>|<span data-ttu-id="d286f-115">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="d286f-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="d286f-116">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="d286f-116">The default is `null`.</span></span>|  
|<span data-ttu-id="d286f-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d286f-117">maxBufferPoolSize</span></span>|<span data-ttu-id="d286f-118">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="d286f-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="d286f-119">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="d286f-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="d286f-120">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="d286f-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="d286f-121">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="d286f-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d286f-122">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="d286f-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d286f-123">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="d286f-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="d286f-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d286f-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="d286f-125">Um inteiro positivo que define o tamanho máximo em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="d286f-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="d286f-126">O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="d286f-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="d286f-127">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d286f-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d286f-128">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="d286f-128">The default is 65536.</span></span>|  
|<span data-ttu-id="d286f-129">porta</span><span class="sxs-lookup"><span data-stu-id="d286f-129">port</span></span>|<span data-ttu-id="d286f-130">Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens do TCP de canal par.</span><span class="sxs-lookup"><span data-stu-id="d286f-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="d286f-131">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="d286f-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="d286f-132">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="d286f-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d286f-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d286f-133">Child Elements</span></span>  
  
|<span data-ttu-id="d286f-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="d286f-134">Element</span></span>|<span data-ttu-id="d286f-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="d286f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d286f-136">\<security></span><span class="sxs-lookup"><span data-stu-id="d286f-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="d286f-137">Define as configurações de segurança para esse transporte.</span><span class="sxs-lookup"><span data-stu-id="d286f-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="d286f-138">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d286f-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d286f-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d286f-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d286f-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="d286f-140">Element</span></span>|<span data-ttu-id="d286f-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="d286f-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d286f-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="d286f-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d286f-143">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d286f-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d286f-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="d286f-144">Remarks</span></span>  
 <span data-ttu-id="d286f-145">Esse transporte não pode ser usado com os contratos que têm operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="d286f-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d286f-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d286f-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d286f-147">Transportes</span><span class="sxs-lookup"><span data-stu-id="d286f-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="d286f-148">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="d286f-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d286f-149">Associações</span><span class="sxs-lookup"><span data-stu-id="d286f-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d286f-150">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d286f-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d286f-151">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d286f-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d286f-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d286f-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
