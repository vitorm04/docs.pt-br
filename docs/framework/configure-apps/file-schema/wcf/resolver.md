---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f3d4b049afe55fb9fb80cbad56c49e8ec13e60db
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758736"
---
# <a name="resolver"></a><span data-ttu-id="7289e-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="7289e-101">\<resolver></span></span>
<span data-ttu-id="7289e-102">Especifica a ID de malha de um resolvedor de pares que é usado para resolver um par para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="7289e-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="7289e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7289e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7289e-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7289e-104">\<bindings></span></span>  
<span data-ttu-id="7289e-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="7289e-105">\<netPeerBinding></span></span>  
<span data-ttu-id="7289e-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="7289e-106">\<binding></span></span>  
<span data-ttu-id="7289e-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="7289e-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7289e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7289e-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7289e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7289e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7289e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7289e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7289e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7289e-111">Attributes</span></span>  
  
|<span data-ttu-id="7289e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7289e-112">Attribute</span></span>|<span data-ttu-id="7289e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7289e-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="7289e-114">Uma cadeia de caracteres que especifica se a instância do resolvedor de par associada a esse serviço é PNRP específico, um resolvedor personalizado ou determinado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7289e-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="7289e-115">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="7289e-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="7289e-116">Uma cadeia de caracteres que especifica a forma como referências são compartilhadas entre pares.</span><span class="sxs-lookup"><span data-stu-id="7289e-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="7289e-117">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="7289e-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7289e-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7289e-118">Child Elements</span></span>  
  
|<span data-ttu-id="7289e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="7289e-119">Element</span></span>|<span data-ttu-id="7289e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="7289e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7289e-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="7289e-121">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="7289e-122">Especifica configurações para um serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="7289e-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7289e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7289e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7289e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="7289e-124">Element</span></span>|<span data-ttu-id="7289e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7289e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7289e-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="7289e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7289e-127">Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7289e-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7289e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7289e-128">Remarks</span></span>  
 <span data-ttu-id="7289e-129">Um resolvedor de pares nome é um serviço de descoberta usado pelos canais pares para localizar nós que participam de uma malha ponto a ponto a ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="7289e-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="7289e-130">Ele também é usado para "Registrar" um nó com uma malha ponto a ponto, o mecanismo pelo qual o nó par se torna conhecidos e estão disponíveis na malha ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="7289e-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="7289e-131">Para obter mais informações sobre os resolvedores de pares, consulte [resolvedores de pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="7289e-131">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7289e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7289e-132">See also</span></span>
- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="7289e-133">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="7289e-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="7289e-134">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7289e-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
