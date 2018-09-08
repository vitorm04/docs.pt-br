---
title: '&lt;resolver&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 48b6b6ca315f7ab63a8f7a64b97167fa04fe1e4e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180794"
---
# <a name="ltresolvergt"></a><span data-ttu-id="68cdb-102">&lt;resolver&gt;</span><span class="sxs-lookup"><span data-stu-id="68cdb-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="68cdb-103">Especifica a ID de malha de um resolvedor de pares que é usado para resolver um par para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="68cdb-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="68cdb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68cdb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="68cdb-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="68cdb-105">\<bindings></span></span>  
<span data-ttu-id="68cdb-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="68cdb-106">\<netPeerBinding></span></span>  
<span data-ttu-id="68cdb-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="68cdb-107">\<binding></span></span>  
<span data-ttu-id="68cdb-108">\<resolver></span><span class="sxs-lookup"><span data-stu-id="68cdb-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68cdb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68cdb-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68cdb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68cdb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="68cdb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68cdb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68cdb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="68cdb-112">Attributes</span></span>  
  
|<span data-ttu-id="68cdb-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="68cdb-113">Attribute</span></span>|<span data-ttu-id="68cdb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="68cdb-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="68cdb-115">Uma cadeia de caracteres que especifica se a instância do resolvedor de par associada a esse serviço é PNRP específico, um resolvedor personalizado ou determinado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="68cdb-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="68cdb-116">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="68cdb-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="68cdb-117">Uma cadeia de caracteres que especifica a forma como referências são compartilhadas entre pares.</span><span class="sxs-lookup"><span data-stu-id="68cdb-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="68cdb-118">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="68cdb-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68cdb-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68cdb-119">Child Elements</span></span>  
  
|<span data-ttu-id="68cdb-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="68cdb-120">Element</span></span>|<span data-ttu-id="68cdb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="68cdb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68cdb-122">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="68cdb-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="68cdb-123">Especifica configurações para um serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="68cdb-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68cdb-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68cdb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68cdb-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="68cdb-125">Element</span></span>|<span data-ttu-id="68cdb-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="68cdb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68cdb-127">\<associação ></span><span class="sxs-lookup"><span data-stu-id="68cdb-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="68cdb-128">Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="68cdb-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68cdb-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="68cdb-129">Remarks</span></span>  
 <span data-ttu-id="68cdb-130">Um resolvedor de pares nome é um serviço de descoberta usado pelos canais pares para localizar nós que participam de uma malha ponto a ponto a ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="68cdb-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="68cdb-131">Ele também é usado para "Registrar" um nó com uma malha ponto a ponto, o mecanismo pelo qual o nó par se torna conhecidos e estão disponíveis na malha ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="68cdb-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="68cdb-132">Para obter mais informações sobre os resolvedores de pares, consulte [resolvedores de pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="68cdb-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68cdb-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68cdb-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="68cdb-134">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="68cdb-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="68cdb-135">Adicionando um resolvedor personalizado a um aplicativo PeerChannel</span><span class="sxs-lookup"><span data-stu-id="68cdb-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
