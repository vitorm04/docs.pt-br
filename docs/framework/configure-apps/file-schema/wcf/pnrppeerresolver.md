---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f0874d38c3432f066d1bec5cc84f53e1f3730180
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747974"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="96a33-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="96a33-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="96a33-103">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="96a33-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="96a33-104">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="96a33-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="96a33-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96a33-105">\<system.serviceModel></span></span>  
<span data-ttu-id="96a33-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="96a33-106">\<bindings></span></span>  
<span data-ttu-id="96a33-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96a33-107">\<customBinding></span></span>  
<span data-ttu-id="96a33-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="96a33-108">\<binding></span></span>  
<span data-ttu-id="96a33-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="96a33-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a33-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96a33-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96a33-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="96a33-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96a33-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="96a33-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96a33-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="96a33-113">Attributes</span></span>  
  
|<span data-ttu-id="96a33-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="96a33-114">Attribute</span></span>|<span data-ttu-id="96a33-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a33-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96a33-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="96a33-116">resolverType</span></span>|<span data-ttu-id="96a33-117">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="96a33-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="96a33-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="96a33-118">This attribute is optional.</span></span> <span data-ttu-id="96a33-119">Se não for definido, ou se ele for definido como uma cadeia de caracteres vazia, o PNRP é usado.</span><span class="sxs-lookup"><span data-stu-id="96a33-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96a33-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="96a33-120">Child Elements</span></span>  
 <span data-ttu-id="96a33-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="96a33-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96a33-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="96a33-122">Parent Elements</span></span>  
  
|<span data-ttu-id="96a33-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="96a33-123">Element</span></span>|<span data-ttu-id="96a33-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a33-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96a33-125">\<associação ></span><span class="sxs-lookup"><span data-stu-id="96a33-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="96a33-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="96a33-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96a33-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96a33-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="96a33-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96a33-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="96a33-129">Associações</span><span class="sxs-lookup"><span data-stu-id="96a33-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="96a33-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="96a33-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="96a33-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="96a33-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="96a33-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96a33-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="96a33-133">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="96a33-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
