---
title: '&lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 76c100c0ec793d6dc4e7e5385f9dcf4521d0039e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151937"
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="43159-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="43159-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="43159-103">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="43159-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="43159-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="43159-104">\<system.serviceModel></span></span>  
<span data-ttu-id="43159-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="43159-105">\<bindings></span></span>  
<span data-ttu-id="43159-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="43159-106">\<customBinding></span></span>  
<span data-ttu-id="43159-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="43159-107">\<binding></span></span>  
<span data-ttu-id="43159-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="43159-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43159-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43159-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43159-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43159-110">Attributes and Elements</span></span>  
 <span data-ttu-id="43159-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43159-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43159-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="43159-112">Attributes</span></span>  
  
|<span data-ttu-id="43159-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="43159-113">Attribute</span></span>|<span data-ttu-id="43159-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="43159-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43159-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="43159-115">listenIpAddress</span></span>|<span data-ttu-id="43159-116">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="43159-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="43159-117">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="43159-117">The default is `null`.</span></span>|  
|<span data-ttu-id="43159-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="43159-118">maxBufferPoolSize</span></span>|<span data-ttu-id="43159-119">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="43159-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="43159-120">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="43159-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="43159-121">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="43159-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="43159-122">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="43159-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="43159-123">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="43159-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="43159-124">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="43159-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="43159-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="43159-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="43159-126">Um inteiro positivo que define o tamanho máximo em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="43159-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="43159-127">O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="43159-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="43159-128">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="43159-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="43159-129">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="43159-129">The default is 65536.</span></span>|  
|<span data-ttu-id="43159-130">porta</span><span class="sxs-lookup"><span data-stu-id="43159-130">port</span></span>|<span data-ttu-id="43159-131">Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens do TCP de canal par.</span><span class="sxs-lookup"><span data-stu-id="43159-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="43159-132">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="43159-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="43159-133">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="43159-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43159-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43159-134">Child Elements</span></span>  
  
|<span data-ttu-id="43159-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="43159-135">Element</span></span>|<span data-ttu-id="43159-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="43159-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43159-137">\<security></span><span class="sxs-lookup"><span data-stu-id="43159-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="43159-138">Define as configurações de segurança para esse transporte.</span><span class="sxs-lookup"><span data-stu-id="43159-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="43159-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="43159-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43159-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43159-140">Parent Elements</span></span>  
  
|<span data-ttu-id="43159-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="43159-141">Element</span></span>|<span data-ttu-id="43159-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="43159-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43159-143">\<associação ></span><span class="sxs-lookup"><span data-stu-id="43159-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="43159-144">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="43159-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43159-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="43159-145">Remarks</span></span>  
 <span data-ttu-id="43159-146">Esse transporte não pode ser usado com os contratos que têm operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="43159-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43159-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43159-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="43159-148">Transportes</span><span class="sxs-lookup"><span data-stu-id="43159-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="43159-149">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="43159-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="43159-150">Associações</span><span class="sxs-lookup"><span data-stu-id="43159-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="43159-151">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="43159-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="43159-152">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="43159-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="43159-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="43159-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
