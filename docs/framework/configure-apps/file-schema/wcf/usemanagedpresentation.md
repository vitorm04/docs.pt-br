---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: a60e1e16b9b41cc5df4ded51cc05d6109dd7b3dc
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147701"
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="8d5a7-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="8d5a7-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="8d5a7-103">Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="8d5a7-104">Esse elemento não tem nenhum atributo e está presente como um comutador vazio.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="8d5a7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8d5a7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8d5a7-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="8d5a7-106">\<bindings></span></span>  
<span data-ttu-id="8d5a7-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8d5a7-107">\<customBinding></span></span>  
<span data-ttu-id="8d5a7-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8d5a7-108">\<binding></span></span>  
<span data-ttu-id="8d5a7-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="8d5a7-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d5a7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d5a7-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d5a7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d5a7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8d5a7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d5a7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d5a7-113">Attributes</span></span>  
 <span data-ttu-id="8d5a7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d5a7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d5a7-115">Child Elements</span></span>  
 <span data-ttu-id="8d5a7-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8d5a7-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d5a7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d5a7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8d5a7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d5a7-118">Element</span></span>|<span data-ttu-id="8d5a7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d5a7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d5a7-120">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8d5a7-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8d5a7-121">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d5a7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d5a7-122">Remarks</span></span>  
 <span data-ttu-id="8d5a7-123">Esse elemento é usado por um provedor de identidade para expressar em sua diretiva, o fato de que ele oferece suporte a perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="8d5a7-124">Provedores de identidade que tal uma declaração de política de publicação devem ser capazes de emitir tokens com base no perfil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5a7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d5a7-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8d5a7-126">Associações</span><span class="sxs-lookup"><span data-stu-id="8d5a7-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8d5a7-127">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="8d5a7-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8d5a7-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="8d5a7-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8d5a7-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8d5a7-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
