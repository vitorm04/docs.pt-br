---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: cefd46d7810149264f9c431a212da0f3f51f8186
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577636"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="31d99-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="31d99-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="31d99-103">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="31d99-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="31d99-104">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="31d99-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="31d99-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="31d99-105">\<system.serviceModel></span></span>  
<span data-ttu-id="31d99-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="31d99-106">\<bindings></span></span>  
<span data-ttu-id="31d99-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="31d99-107">\<customBinding></span></span>  
<span data-ttu-id="31d99-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="31d99-108">\<binding></span></span>  
<span data-ttu-id="31d99-109">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="31d99-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d99-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31d99-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31d99-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="31d99-111">Attributes and Elements</span></span>  
 <span data-ttu-id="31d99-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="31d99-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31d99-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="31d99-113">Attributes</span></span>  
  
|<span data-ttu-id="31d99-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="31d99-114">Attribute</span></span>|<span data-ttu-id="31d99-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="31d99-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31d99-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="31d99-116">resolverType</span></span>|<span data-ttu-id="31d99-117">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="31d99-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="31d99-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="31d99-118">This attribute is optional.</span></span> <span data-ttu-id="31d99-119">Se não for definido, ou se ele for definido como uma cadeia de caracteres vazia, o PNRP é usado.</span><span class="sxs-lookup"><span data-stu-id="31d99-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31d99-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="31d99-120">Child Elements</span></span>  
 <span data-ttu-id="31d99-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="31d99-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31d99-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="31d99-122">Parent Elements</span></span>  
  
|<span data-ttu-id="31d99-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="31d99-123">Element</span></span>|<span data-ttu-id="31d99-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="31d99-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31d99-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="31d99-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="31d99-126">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="31d99-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="31d99-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31d99-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="31d99-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31d99-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="31d99-129">Associações</span><span class="sxs-lookup"><span data-stu-id="31d99-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="31d99-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="31d99-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="31d99-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="31d99-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="31d99-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="31d99-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="31d99-133">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="31d99-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
