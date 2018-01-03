---
title: '&lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb60d901d498c6db194e60a9229c0d5b69eee31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="8ff2b-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="8ff2b-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="8ff2b-103">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="8ff2b-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8ff2b-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-105">\<bindings></span></span>  
<span data-ttu-id="8ff2b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-106">\<customBinding></span></span>  
<span data-ttu-id="8ff2b-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-107">\<binding></span></span>  
<span data-ttu-id="8ff2b-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff2b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ff2b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ff2b-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8ff2b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ff2b-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ff2b-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8ff2b-112">Attributes</span></span>  
  
|<span data-ttu-id="8ff2b-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8ff2b-113">Attribute</span></span>|<span data-ttu-id="8ff2b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ff2b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ff2b-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="8ff2b-115">listenIpAddress</span></span>|<span data-ttu-id="8ff2b-116">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="8ff2b-117">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-117">The default is `null`.</span></span>|  
|<span data-ttu-id="8ff2b-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8ff2b-118">maxBufferPoolSize</span></span>|<span data-ttu-id="8ff2b-119">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="8ff2b-120">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="8ff2b-121">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="8ff2b-122">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="8ff2b-123">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="8ff2b-124">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="8ff2b-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8ff2b-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="8ff2b-126">Um inteiro positivo que define o tamanho máximo em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="8ff2b-127">O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="8ff2b-128">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8ff2b-129">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-129">The default is 65536.</span></span>|  
|<span data-ttu-id="8ff2b-130">porta</span><span class="sxs-lookup"><span data-stu-id="8ff2b-130">port</span></span>|<span data-ttu-id="8ff2b-131">Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens TCP de canal par.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="8ff2b-132">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="8ff2b-133">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ff2b-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8ff2b-134">Child Elements</span></span>  
  
|<span data-ttu-id="8ff2b-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ff2b-135">Element</span></span>|<span data-ttu-id="8ff2b-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ff2b-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ff2b-137">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="8ff2b-138">Define as configurações de segurança para este transporte.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="8ff2b-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ff2b-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8ff2b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8ff2b-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ff2b-141">Element</span></span>|<span data-ttu-id="8ff2b-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ff2b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ff2b-143">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8ff2b-144">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ff2b-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ff2b-145">Remarks</span></span>  
 <span data-ttu-id="8ff2b-146">Esse transporte não pode ser usado com contratos com operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="8ff2b-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff2b-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff2b-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8ff2b-148">Transportes</span><span class="sxs-lookup"><span data-stu-id="8ff2b-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="8ff2b-149">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="8ff2b-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="8ff2b-150">Associações</span><span class="sxs-lookup"><span data-stu-id="8ff2b-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8ff2b-151">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="8ff2b-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8ff2b-152">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="8ff2b-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8ff2b-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8ff2b-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
