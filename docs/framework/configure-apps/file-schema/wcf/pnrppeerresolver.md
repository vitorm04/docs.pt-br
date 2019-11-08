---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738772"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="b723d-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="b723d-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="b723d-102">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="b723d-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="b723d-103">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="b723d-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="b723d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b723d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b723d-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b723d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b723d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="b723d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b723d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="b723d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b723d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="b723d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b723d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="b723d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b723d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b723d-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b723d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b723d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b723d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b723d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b723d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="b723d-113">Attributes</span></span>  
  
|<span data-ttu-id="b723d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="b723d-114">Attribute</span></span>|<span data-ttu-id="b723d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b723d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b723d-116">resolvedor</span><span class="sxs-lookup"><span data-stu-id="b723d-116">resolverType</span></span>|<span data-ttu-id="b723d-117">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b723d-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="b723d-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="b723d-118">This attribute is optional.</span></span> <span data-ttu-id="b723d-119">Se não estiver definido, ou se estiver definido como uma cadeia de caracteres vazia, o PNRP será usado.</span><span class="sxs-lookup"><span data-stu-id="b723d-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b723d-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b723d-120">Child Elements</span></span>  
 <span data-ttu-id="b723d-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b723d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b723d-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b723d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b723d-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b723d-123">Element</span></span>|<span data-ttu-id="b723d-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b723d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b723d-125">\<binding ></span><span class="sxs-lookup"><span data-stu-id="b723d-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="b723d-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b723d-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b723d-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b723d-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b723d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b723d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b723d-129">Associações</span><span class="sxs-lookup"><span data-stu-id="b723d-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b723d-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="b723d-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b723d-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="b723d-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b723d-132">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="b723d-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b723d-133">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="b723d-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
