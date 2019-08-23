---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: e3a9ee00aab6ab48a1ba891565b63824e62b20fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934222"
---
# <a name="resolver"></a><span data-ttu-id="bad33-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="bad33-101">\<resolver></span></span>
<span data-ttu-id="bad33-102">Especifica um resolvedor de pares que é usado para resolver uma ID de malha de mesmo nível para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="bad33-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="bad33-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bad33-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bad33-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bad33-104">\<bindings></span></span>  
<span data-ttu-id="bad33-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="bad33-105">\<netPeerBinding></span></span>  
<span data-ttu-id="bad33-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="bad33-106">\<binding></span></span>  
<span data-ttu-id="bad33-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="bad33-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad33-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bad33-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bad33-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bad33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bad33-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bad33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bad33-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bad33-111">Attributes</span></span>  
  
|<span data-ttu-id="bad33-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="bad33-112">Attribute</span></span>|<span data-ttu-id="bad33-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bad33-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="bad33-114">Uma cadeia de caracteres que especifica se a instância do resolvedor de pares associada a esse serviço é específica do PNRP, um resolvedor personalizado ou determinado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="bad33-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="bad33-115">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="bad33-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="bad33-116">Uma cadeia de caracteres que especifica a maneira como as referências são compartilhadas entre os pares.</span><span class="sxs-lookup"><span data-stu-id="bad33-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="bad33-117">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="bad33-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bad33-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bad33-118">Child Elements</span></span>  
  
|<span data-ttu-id="bad33-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="bad33-119">Element</span></span>|<span data-ttu-id="bad33-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="bad33-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bad33-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="bad33-121">\<headers></span></span>](headers.md)|<span data-ttu-id="bad33-122">Especifica as configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="bad33-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bad33-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bad33-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bad33-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bad33-124">Element</span></span>|<span data-ttu-id="bad33-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bad33-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bad33-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="bad33-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bad33-127">Define todos os recursos de associação do [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bad33-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad33-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bad33-128">Remarks</span></span>  
 <span data-ttu-id="bad33-129">Um resolvedor de nome de par é um serviço de descoberta usado por canais de mesmo nível para localizar nós de mesmo nível que participam de uma malha de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="bad33-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="bad33-130">Ele também é usado para "registrar" um nó com uma malha de mesmo nível, o mecanismo pelo qual o nó par se torna conhecido e disponível na malha de pares.</span><span class="sxs-lookup"><span data-stu-id="bad33-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="bad33-131">Para obter mais informações sobre resolvedores de pares, consulte Resolvedores de [pares](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="bad33-131">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad33-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bad33-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="bad33-133">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="bad33-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="bad33-134">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bad33-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
