---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="63798-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="63798-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="63798-103">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="63798-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="63798-104">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="63798-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="63798-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="63798-105">\<system.serviceModel></span></span>  
<span data-ttu-id="63798-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="63798-106">\<bindings></span></span>  
<span data-ttu-id="63798-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="63798-107">\<customBinding></span></span>  
<span data-ttu-id="63798-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="63798-108">\<binding></span></span>  
<span data-ttu-id="63798-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="63798-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63798-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63798-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63798-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63798-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63798-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63798-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63798-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="63798-113">Attributes</span></span>  
  
|<span data-ttu-id="63798-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="63798-114">Attribute</span></span>|<span data-ttu-id="63798-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="63798-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63798-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="63798-116">resolverType</span></span>|<span data-ttu-id="63798-117">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="63798-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="63798-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="63798-118">This attribute is optional.</span></span> <span data-ttu-id="63798-119">Se não for definido, ou se ele for definido como uma cadeia de caracteres vazia, o PNRP é usado.</span><span class="sxs-lookup"><span data-stu-id="63798-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63798-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63798-120">Child Elements</span></span>  
 <span data-ttu-id="63798-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="63798-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63798-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63798-122">Parent Elements</span></span>  
  
|<span data-ttu-id="63798-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="63798-123">Element</span></span>|<span data-ttu-id="63798-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="63798-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63798-125">\<associação ></span><span class="sxs-lookup"><span data-stu-id="63798-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="63798-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="63798-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63798-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63798-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="63798-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63798-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <span data-ttu-id="63798-129">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="63798-129">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="63798-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="63798-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="63798-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="63798-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="63798-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="63798-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="63798-133">Resolvedor Peer</span><span class="sxs-lookup"><span data-stu-id="63798-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
