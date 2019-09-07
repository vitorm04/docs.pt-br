---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: fb974492dee6b2a4244cedc06e3f5e40334dd02a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399976"
---
# <a name="resolver"></a><span data-ttu-id="c7eac-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="c7eac-101">\<resolver></span></span>
<span data-ttu-id="c7eac-102">Especifica um resolvedor de pares que é usado para resolver uma ID de malha de mesmo nível para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="c7eac-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="c7eac-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c7eac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7eac-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c7eac-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c7eac-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c7eac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c7eac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> netPeerTcpBinding**](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c7eac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="c7eac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="c7eac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c7eac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do resolvedor**</span><span class="sxs-lookup"><span data-stu-id="c7eac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7eac-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7eac-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7eac-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c7eac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c7eac-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c7eac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7eac-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c7eac-112">Attributes</span></span>  
  
|<span data-ttu-id="c7eac-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c7eac-113">Attribute</span></span>|<span data-ttu-id="c7eac-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7eac-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="c7eac-115">Uma cadeia de caracteres que especifica se a instância do resolvedor de pares associada a esse serviço é específica do PNRP, um resolvedor personalizado ou determinado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c7eac-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="c7eac-116">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="c7eac-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="c7eac-117">Uma cadeia de caracteres que especifica a maneira como as referências são compartilhadas entre os pares.</span><span class="sxs-lookup"><span data-stu-id="c7eac-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="c7eac-118">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="c7eac-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7eac-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c7eac-119">Child Elements</span></span>  
  
|<span data-ttu-id="c7eac-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7eac-120">Element</span></span>|<span data-ttu-id="c7eac-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7eac-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7eac-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="c7eac-122">\<headers></span></span>](headers.md)|<span data-ttu-id="c7eac-123">Especifica as configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="c7eac-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7eac-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c7eac-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c7eac-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7eac-125">Element</span></span>|<span data-ttu-id="c7eac-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7eac-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7eac-127">\<binding></span><span class="sxs-lookup"><span data-stu-id="c7eac-127">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="c7eac-128">Define todos os recursos de associação do [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c7eac-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7eac-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7eac-129">Remarks</span></span>  
 <span data-ttu-id="c7eac-130">Um resolvedor de nome de par é um serviço de descoberta usado por canais de mesmo nível para localizar nós de mesmo nível que participam de uma malha de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="c7eac-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="c7eac-131">Ele também é usado para "registrar" um nó com uma malha de mesmo nível, o mecanismo pelo qual o nó par se torna conhecido e disponível na malha de pares.</span><span class="sxs-lookup"><span data-stu-id="c7eac-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="c7eac-132">Para obter mais informações sobre resolvedores de pares, consulte [resolvedores de pares](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="c7eac-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7eac-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7eac-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="c7eac-134">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="c7eac-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="c7eac-135">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c7eac-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
