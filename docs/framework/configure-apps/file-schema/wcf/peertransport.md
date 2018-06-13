---
title: '&lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: df192c6a602aa073f48fab4229b4be3fbeb2349d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748614"
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="d264a-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="d264a-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="d264a-103">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d264a-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="d264a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d264a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d264a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d264a-105">\<bindings></span></span>  
<span data-ttu-id="d264a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d264a-106">\<customBinding></span></span>  
<span data-ttu-id="d264a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d264a-107">\<binding></span></span>  
<span data-ttu-id="d264a-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="d264a-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d264a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d264a-109">Syntax</span></span>  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d264a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d264a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d264a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d264a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d264a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d264a-112">Attributes</span></span>  
  
|<span data-ttu-id="d264a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d264a-113">Attribute</span></span>|<span data-ttu-id="d264a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d264a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d264a-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="d264a-115">listenIpAddress</span></span>|<span data-ttu-id="d264a-116">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="d264a-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="d264a-117">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="d264a-117">The default is `null`.</span></span>|  
|<span data-ttu-id="d264a-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d264a-118">maxBufferPoolSize</span></span>|<span data-ttu-id="d264a-119">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="d264a-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="d264a-120">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="d264a-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="d264a-121">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="d264a-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="d264a-122">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="d264a-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d264a-123">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="d264a-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d264a-124">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="d264a-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="d264a-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d264a-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="d264a-126">Um inteiro positivo que define o tamanho máximo em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="d264a-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="d264a-127">O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d264a-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="d264a-128">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d264a-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d264a-129">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="d264a-129">The default is 65536.</span></span>|  
|<span data-ttu-id="d264a-130">porta</span><span class="sxs-lookup"><span data-stu-id="d264a-130">port</span></span>|<span data-ttu-id="d264a-131">Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens TCP de canal par.</span><span class="sxs-lookup"><span data-stu-id="d264a-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="d264a-132">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="d264a-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="d264a-133">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="d264a-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d264a-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d264a-134">Child Elements</span></span>  
  
|<span data-ttu-id="d264a-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="d264a-135">Element</span></span>|<span data-ttu-id="d264a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="d264a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d264a-137">\<security></span><span class="sxs-lookup"><span data-stu-id="d264a-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="d264a-138">Define as configurações de segurança para este transporte.</span><span class="sxs-lookup"><span data-stu-id="d264a-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="d264a-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d264a-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d264a-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d264a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="d264a-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="d264a-141">Element</span></span>|<span data-ttu-id="d264a-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="d264a-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d264a-143">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d264a-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d264a-144">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d264a-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d264a-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="d264a-145">Remarks</span></span>  
 <span data-ttu-id="d264a-146">Esse transporte não pode ser usado com contratos com operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="d264a-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d264a-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d264a-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="d264a-148">Transportes</span><span class="sxs-lookup"><span data-stu-id="d264a-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="d264a-149">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="d264a-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="d264a-150">Associações</span><span class="sxs-lookup"><span data-stu-id="d264a-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d264a-151">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d264a-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d264a-152">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d264a-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d264a-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d264a-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
