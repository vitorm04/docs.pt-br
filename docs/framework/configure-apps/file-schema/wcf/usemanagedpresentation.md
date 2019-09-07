---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399219"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="7c0a2-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="7c0a2-101">\<useManagedPresentation></span></span>
<span data-ttu-id="7c0a2-102">Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="7c0a2-103">Este elemento não tem nenhum atributo e está presente como uma opção vazia.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="7c0a2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c0a2-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7c0a2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7c0a2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7c0a2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="7c0a2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7c0a2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> useManagedPresentation**</span><span class="sxs-lookup"><span data-stu-id="7c0a2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0a2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c0a2-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c0a2-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c0a2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7c0a2-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c0a2-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c0a2-113">Attributes</span></span>  
 <span data-ttu-id="7c0a2-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c0a2-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c0a2-115">Child Elements</span></span>  
 <span data-ttu-id="7c0a2-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7c0a2-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c0a2-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c0a2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7c0a2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c0a2-118">Element</span></span>|<span data-ttu-id="7c0a2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c0a2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c0a2-120">\<binding></span><span class="sxs-lookup"><span data-stu-id="7c0a2-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="7c0a2-121">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c0a2-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c0a2-122">Remarks</span></span>  
 <span data-ttu-id="7c0a2-123">Esse elemento é usado por um provedor de identidade para expressar em sua política o fato de que ele dá suporte ao perfil do CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="7c0a2-124">Provedores de identidade que publicam tal declaração de política devem ser capazes de emitir tokens com base nesse perfil do CardSpace.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c0a2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c0a2-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7c0a2-126">Associações</span><span class="sxs-lookup"><span data-stu-id="7c0a2-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7c0a2-127">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="7c0a2-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7c0a2-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7c0a2-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7c0a2-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7c0a2-129">\<customBinding></span></span>](custombinding.md)
