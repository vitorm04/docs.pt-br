---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738732"
---
# \<resolver>
<span data-ttu-id="d9941-101">Especifica um resolvedor de pares que é usado para resolver uma ID de malha de mesmo nível para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="d9941-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="d9941-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9941-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9941-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9941-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d9941-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9941-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9941-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9941-105">Attributes</span></span>  
  
|<span data-ttu-id="d9941-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="d9941-106">Attribute</span></span>|<span data-ttu-id="d9941-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9941-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d9941-108">Uma cadeia de caracteres que especifica se a instância do resolvedor de pares associada a esse serviço é específica do PNRP, um resolvedor personalizado ou determinado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d9941-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="d9941-109">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> .</span><span class="sxs-lookup"><span data-stu-id="d9941-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="d9941-110">Uma cadeia de caracteres que especifica a maneira como as referências são compartilhadas entre os pares.</span><span class="sxs-lookup"><span data-stu-id="d9941-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="d9941-111">Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> .</span><span class="sxs-lookup"><span data-stu-id="d9941-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9941-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9941-112">Child Elements</span></span>  
  
|<span data-ttu-id="d9941-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9941-113">Element</span></span>|<span data-ttu-id="d9941-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9941-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="d9941-115">Especifica as configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="d9941-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9941-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9941-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d9941-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9941-117">Element</span></span>|<span data-ttu-id="d9941-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9941-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d9941-119">Define todos os recursos de associação do [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d9941-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9941-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9941-120">Remarks</span></span>  
 <span data-ttu-id="d9941-121">Um resolvedor de nome de par é um serviço de descoberta usado por canais de mesmo nível para localizar nós de mesmo nível que participam de uma malha de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="d9941-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="d9941-122">Ele também é usado para "registrar" um nó com uma malha de mesmo nível, o mecanismo pelo qual o nó par se torna conhecido e disponível na malha de pares.</span><span class="sxs-lookup"><span data-stu-id="d9941-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="d9941-123">Para obter mais informações sobre resolvedores de pares, consulte [resolvedores de pares](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="d9941-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9941-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9941-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="d9941-125">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="d9941-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="d9941-126">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d9941-126">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
