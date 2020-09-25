---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 68832c3a5bd4cc423642a6272e70cbecab86d6a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181538"
---
# \<peerTransport>

<span data-ttu-id="e0c93-101">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e0c93-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="e0c93-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0c93-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0c93-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e0c93-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e0c93-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e0c93-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0c93-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0c93-105">Attributes</span></span>  
  
|<span data-ttu-id="e0c93-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="e0c93-106">Attribute</span></span>|<span data-ttu-id="e0c93-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0c93-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0c93-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="e0c93-108">listenIpAddress</span></span>|<span data-ttu-id="e0c93-109">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="e0c93-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="e0c93-110">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="e0c93-110">The default is `null`.</span></span>|  
|<span data-ttu-id="e0c93-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e0c93-111">maxBufferPoolSize</span></span>|<span data-ttu-id="e0c93-112">Um inteiro positivo que especifica o tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="e0c93-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="e0c93-113">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="e0c93-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="e0c93-114">Muitas partes do WCF usam buffers.</span><span class="sxs-lookup"><span data-stu-id="e0c93-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="e0c93-115">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="e0c93-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e0c93-116">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="e0c93-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e0c93-117">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="e0c93-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="e0c93-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e0c93-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="e0c93-119">Um inteiro positivo que define o tamanho máximo da mensagem em bytes, incluindo cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="e0c93-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="e0c93-120">O remetente de uma mensagem recebe uma falha de SOAP quando a mensagem é muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="e0c93-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="e0c93-121">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e0c93-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e0c93-122">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="e0c93-122">The default is 65536.</span></span>|  
|<span data-ttu-id="e0c93-123">porta</span><span class="sxs-lookup"><span data-stu-id="e0c93-123">port</span></span>|<span data-ttu-id="e0c93-124">Um inteiro que especifica a porta da interface de rede na qual essa associação processará as mensagens TCP do canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="e0c93-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="e0c93-125">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="e0c93-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="e0c93-126">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="e0c93-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0c93-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e0c93-127">Child Elements</span></span>  
  
|<span data-ttu-id="e0c93-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0c93-128">Element</span></span>|<span data-ttu-id="e0c93-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0c93-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="e0c93-130">Define as configurações de segurança para esse transporte.</span><span class="sxs-lookup"><span data-stu-id="e0c93-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="e0c93-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="e0c93-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0c93-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e0c93-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e0c93-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0c93-133">Element</span></span>|<span data-ttu-id="e0c93-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0c93-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e0c93-135">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e0c93-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0c93-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0c93-136">Remarks</span></span>  

 <span data-ttu-id="e0c93-137">Esse transporte não pode ser usado com contratos que têm operações de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="e0c93-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c93-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="e0c93-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e0c93-139">Transportes</span><span class="sxs-lookup"><span data-stu-id="e0c93-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="e0c93-140">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="e0c93-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="e0c93-141">Associações</span><span class="sxs-lookup"><span data-stu-id="e0c93-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e0c93-142">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="e0c93-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e0c93-143">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e0c93-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
