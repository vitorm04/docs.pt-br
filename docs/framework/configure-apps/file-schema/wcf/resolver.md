---
title: '&lt;resolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db95b6f9a988c133a6b4afd55849fc6fb650c24c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltresolvergt"></a><span data-ttu-id="14d7f-102">&lt;resolver&gt;</span><span class="sxs-lookup"><span data-stu-id="14d7f-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="14d7f-103">Especifica a ID de um resolvedor de pares que é usado para resolver um par de malha para um conjunto de endereços de nó par que representa vários nós que participam na malha.</span><span class="sxs-lookup"><span data-stu-id="14d7f-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="14d7f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14d7f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14d7f-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="14d7f-105">\<bindings></span></span>  
<span data-ttu-id="14d7f-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="14d7f-106">\<netPeerBinding></span></span>  
<span data-ttu-id="14d7f-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="14d7f-107">\<binding></span></span>  
<span data-ttu-id="14d7f-108">\<resolver></span><span class="sxs-lookup"><span data-stu-id="14d7f-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d7f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14d7f-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14d7f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="14d7f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14d7f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="14d7f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14d7f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="14d7f-112">Attributes</span></span>  
  
|<span data-ttu-id="14d7f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="14d7f-113">Attribute</span></span>|<span data-ttu-id="14d7f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="14d7f-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="14d7f-115">Uma cadeia de caracteres que especifica se a instância do resolvedor peer associada a esse serviço é específico PNRP, um resolvedor personalizado ou determinado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="14d7f-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="14d7f-116">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="14d7f-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="14d7f-117">Uma cadeia de caracteres que especifica a forma como referências são compartilhadas entre pares.</span><span class="sxs-lookup"><span data-stu-id="14d7f-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="14d7f-118">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="14d7f-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14d7f-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="14d7f-119">Child Elements</span></span>  
  
|<span data-ttu-id="14d7f-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="14d7f-120">Element</span></span>|<span data-ttu-id="14d7f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="14d7f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14d7f-122">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="14d7f-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="14d7f-123">Especifica configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="14d7f-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14d7f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="14d7f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="14d7f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="14d7f-125">Element</span></span>|<span data-ttu-id="14d7f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="14d7f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14d7f-127">\<binding></span><span class="sxs-lookup"><span data-stu-id="14d7f-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="14d7f-128">Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="14d7f-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14d7f-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="14d7f-129">Remarks</span></span>  
 <span data-ttu-id="14d7f-130">Um resolvedor de nome de ponto a ponto é um serviço de descoberta usado pelos canais de ponto a ponto para localizar nós que participam de uma malha de pontos de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="14d7f-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="14d7f-131">Ele também é usado para "Registrar" de um nó com uma malha de ponto a ponto, o mecanismo pelo qual o nó par torna-se e conhecida da malha ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="14d7f-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="14d7f-132">Para obter mais informações sobre o resolvedor peer, consulte [resolvedor Peer](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="14d7f-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d7f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14d7f-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="14d7f-134">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="14d7f-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="14d7f-135">Adicionando um resolvedor personalizado para um aplicativo PeerChannel</span><span class="sxs-lookup"><span data-stu-id="14d7f-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
