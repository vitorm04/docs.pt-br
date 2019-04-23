---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214047"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="76442-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="76442-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="76442-102">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="76442-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="76442-103">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="76442-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="76442-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="76442-104">\<system.serviceModel></span></span>  
<span data-ttu-id="76442-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="76442-105">\<bindings></span></span>  
<span data-ttu-id="76442-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="76442-106">\<customBinding></span></span>  
<span data-ttu-id="76442-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="76442-107">\<binding></span></span>  
<span data-ttu-id="76442-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="76442-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76442-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76442-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76442-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="76442-110">Attributes and Elements</span></span>  
 <span data-ttu-id="76442-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="76442-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76442-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="76442-112">Attributes</span></span>  
  
|<span data-ttu-id="76442-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="76442-113">Attribute</span></span>|<span data-ttu-id="76442-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="76442-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76442-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="76442-115">resolverType</span></span>|<span data-ttu-id="76442-116">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="76442-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="76442-117">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="76442-117">This attribute is optional.</span></span> <span data-ttu-id="76442-118">Se não for definido, ou se ele for definido como uma cadeia de caracteres vazia, o PNRP é usado.</span><span class="sxs-lookup"><span data-stu-id="76442-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76442-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="76442-119">Child Elements</span></span>  
 <span data-ttu-id="76442-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="76442-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76442-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="76442-121">Parent Elements</span></span>  
  
|<span data-ttu-id="76442-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="76442-122">Element</span></span>|<span data-ttu-id="76442-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="76442-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76442-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="76442-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="76442-125">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="76442-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76442-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76442-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="76442-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76442-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="76442-128">Associações</span><span class="sxs-lookup"><span data-stu-id="76442-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="76442-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="76442-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="76442-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="76442-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="76442-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="76442-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="76442-132">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="76442-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
