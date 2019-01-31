---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f98c358cc9891e9d7223d280fc8e50c19aad9759
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260640"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="5ced8-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="5ced8-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="5ced8-102">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="5ced8-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="5ced8-103">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="5ced8-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="5ced8-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5ced8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5ced8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5ced8-105">\<bindings></span></span>  
<span data-ttu-id="5ced8-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5ced8-106">\<customBinding></span></span>  
<span data-ttu-id="5ced8-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="5ced8-107">\<binding></span></span>  
<span data-ttu-id="5ced8-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="5ced8-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ced8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ced8-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ced8-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ced8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ced8-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ced8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ced8-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ced8-112">Attributes</span></span>  
  
|<span data-ttu-id="5ced8-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ced8-113">Attribute</span></span>|<span data-ttu-id="5ced8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ced8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ced8-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="5ced8-115">resolverType</span></span>|<span data-ttu-id="5ced8-116">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="5ced8-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="5ced8-117">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="5ced8-117">This attribute is optional.</span></span> <span data-ttu-id="5ced8-118">Se não for definido, ou se ele for definido como uma cadeia de caracteres vazia, o PNRP é usado.</span><span class="sxs-lookup"><span data-stu-id="5ced8-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ced8-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ced8-119">Child Elements</span></span>  
 <span data-ttu-id="5ced8-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5ced8-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ced8-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ced8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5ced8-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ced8-122">Element</span></span>|<span data-ttu-id="5ced8-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ced8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ced8-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="5ced8-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5ced8-125">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5ced8-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5ced8-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ced8-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="5ced8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ced8-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5ced8-128">Associações</span><span class="sxs-lookup"><span data-stu-id="5ced8-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="5ced8-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5ced8-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5ced8-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5ced8-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5ced8-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5ced8-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="5ced8-132">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="5ced8-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
