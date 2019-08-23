---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933805"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="17bac-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="17bac-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="17bac-102">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="17bac-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="17bac-103">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="17bac-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="17bac-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="17bac-104">\<system.serviceModel></span></span>  
<span data-ttu-id="17bac-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="17bac-105">\<bindings></span></span>  
<span data-ttu-id="17bac-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="17bac-106">\<customBinding></span></span>  
<span data-ttu-id="17bac-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="17bac-107">\<binding></span></span>  
<span data-ttu-id="17bac-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="17bac-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bac-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17bac-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17bac-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17bac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17bac-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="17bac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17bac-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="17bac-112">Attributes</span></span>  
  
|<span data-ttu-id="17bac-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="17bac-113">Attribute</span></span>|<span data-ttu-id="17bac-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="17bac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17bac-115">resolvedor</span><span class="sxs-lookup"><span data-stu-id="17bac-115">resolverType</span></span>|<span data-ttu-id="17bac-116">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="17bac-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="17bac-117">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="17bac-117">This attribute is optional.</span></span> <span data-ttu-id="17bac-118">Se não estiver definido, ou se estiver definido como uma cadeia de caracteres vazia, o PNRP será usado.</span><span class="sxs-lookup"><span data-stu-id="17bac-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17bac-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="17bac-119">Child Elements</span></span>  
 <span data-ttu-id="17bac-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="17bac-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17bac-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="17bac-121">Parent Elements</span></span>  
  
|<span data-ttu-id="17bac-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="17bac-122">Element</span></span>|<span data-ttu-id="17bac-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="17bac-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17bac-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="17bac-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="17bac-125">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="17bac-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17bac-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17bac-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="17bac-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17bac-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="17bac-128">Associações</span><span class="sxs-lookup"><span data-stu-id="17bac-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="17bac-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="17bac-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="17bac-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="17bac-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="17bac-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="17bac-131">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="17bac-132">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="17bac-132">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
