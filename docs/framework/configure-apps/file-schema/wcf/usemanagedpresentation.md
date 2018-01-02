---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9851794d77972066fb897aa76528fec86fd6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="29cb7-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="29cb7-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="29cb7-103">Um elemento de associação usado para se comunicar com um serviço de Token de segurança de CardSpace que suporte o perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="29cb7-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="29cb7-104">Esse elemento não tem nenhum atributo e está presente como uma chave vazia.</span><span class="sxs-lookup"><span data-stu-id="29cb7-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="29cb7-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29cb7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="29cb7-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="29cb7-106">\<bindings></span></span>  
<span data-ttu-id="29cb7-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="29cb7-107">\<customBinding></span></span>  
<span data-ttu-id="29cb7-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="29cb7-108">\<binding></span></span>  
<span data-ttu-id="29cb7-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="29cb7-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29cb7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29cb7-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29cb7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="29cb7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="29cb7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="29cb7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29cb7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="29cb7-113">Attributes</span></span>  
 <span data-ttu-id="29cb7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="29cb7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29cb7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="29cb7-115">Child Elements</span></span>  
 <span data-ttu-id="29cb7-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="29cb7-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29cb7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="29cb7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="29cb7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="29cb7-118">Element</span></span>|<span data-ttu-id="29cb7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="29cb7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29cb7-120">\<associação ></span><span class="sxs-lookup"><span data-stu-id="29cb7-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="29cb7-121">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="29cb7-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29cb7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="29cb7-122">Remarks</span></span>  
 <span data-ttu-id="29cb7-123">Esse elemento é usado por um provedor de identidade para expressar em sua política o fato de que ele oferece suporte o perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="29cb7-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="29cb7-124">Provedores de identidade que uma declaração de política desse tipo de publicação devem ser capazes de emitir tokens com base no perfil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="29cb7-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cb7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29cb7-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="29cb7-126">Associações</span><span class="sxs-lookup"><span data-stu-id="29cb7-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="29cb7-127">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="29cb7-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="29cb7-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="29cb7-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="29cb7-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="29cb7-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
