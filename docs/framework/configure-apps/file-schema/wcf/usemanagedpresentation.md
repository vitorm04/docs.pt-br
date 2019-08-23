---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940621"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="cd586-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="cd586-101">\<useManagedPresentation></span></span>
<span data-ttu-id="cd586-102">Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="cd586-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="cd586-103">Este elemento não tem nenhum atributo e está presente como uma opção vazia.</span><span class="sxs-lookup"><span data-stu-id="cd586-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="cd586-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cd586-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cd586-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="cd586-105">\<bindings></span></span>  
<span data-ttu-id="cd586-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="cd586-106">\<customBinding></span></span>  
<span data-ttu-id="cd586-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="cd586-107">\<binding></span></span>  
<span data-ttu-id="cd586-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="cd586-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd586-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd586-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd586-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cd586-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cd586-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cd586-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd586-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="cd586-112">Attributes</span></span>  
 <span data-ttu-id="cd586-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cd586-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd586-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cd586-114">Child Elements</span></span>  
 <span data-ttu-id="cd586-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cd586-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd586-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cd586-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cd586-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="cd586-117">Element</span></span>|<span data-ttu-id="cd586-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd586-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd586-119">\<binding></span><span class="sxs-lookup"><span data-stu-id="cd586-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="cd586-120">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="cd586-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd586-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd586-121">Remarks</span></span>  
 <span data-ttu-id="cd586-122">Esse elemento é usado por um provedor de identidade para expressar em sua política o fato de que ele dá suporte ao perfil do CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="cd586-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="cd586-123">Provedores de identidade que publicam tal declaração de política devem ser capazes de emitir tokens com base nesse perfil do CardSpace.</span><span class="sxs-lookup"><span data-stu-id="cd586-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd586-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd586-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cd586-125">Associações</span><span class="sxs-lookup"><span data-stu-id="cd586-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cd586-126">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="cd586-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cd586-127">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="cd586-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cd586-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="cd586-128">\<customBinding></span></span>](custombinding.md)
