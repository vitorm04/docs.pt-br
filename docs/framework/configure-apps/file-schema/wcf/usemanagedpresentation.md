---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735945"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="d6510-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="d6510-101">\<useManagedPresentation></span></span>
<span data-ttu-id="d6510-102">Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="d6510-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d6510-103">Este elemento não tem nenhum atributo e está presente como uma opção vazia.</span><span class="sxs-lookup"><span data-stu-id="d6510-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="d6510-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d6510-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d6510-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d6510-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d6510-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="d6510-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d6510-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="d6510-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="d6510-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="d6510-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d6510-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="d6510-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6510-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6510-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6510-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6510-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6510-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6510-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6510-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6510-113">Attributes</span></span>  
 <span data-ttu-id="d6510-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d6510-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6510-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6510-115">Child Elements</span></span>  
 <span data-ttu-id="d6510-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d6510-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6510-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6510-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d6510-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6510-118">Element</span></span>|<span data-ttu-id="d6510-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6510-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6510-120">\<binding ></span><span class="sxs-lookup"><span data-stu-id="d6510-120">\<binding></span></span>](bindings.md)|<span data-ttu-id="d6510-121">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d6510-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6510-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6510-122">Remarks</span></span>  
 <span data-ttu-id="d6510-123">Esse elemento é usado por um provedor de identidade para expressar em sua política o fato de que ele dá suporte ao perfil do CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="d6510-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d6510-124">Provedores de identidade que publicam tal declaração de política devem ser capazes de emitir tokens com base nesse perfil do CardSpace.</span><span class="sxs-lookup"><span data-stu-id="d6510-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6510-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6510-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d6510-126">Associações</span><span class="sxs-lookup"><span data-stu-id="d6510-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6510-127">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d6510-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d6510-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d6510-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d6510-129">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="d6510-129">\<customBinding></span></span>](custombinding.md)
