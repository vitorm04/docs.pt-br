---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769844"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="9a7ea-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="9a7ea-101">\<useManagedPresentation></span></span>
<span data-ttu-id="9a7ea-102">Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="9a7ea-103">Esse elemento não tem nenhum atributo e está presente como um comutador vazio.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="9a7ea-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9a7ea-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9a7ea-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9a7ea-105">\<bindings></span></span>  
<span data-ttu-id="9a7ea-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9a7ea-106">\<customBinding></span></span>  
<span data-ttu-id="9a7ea-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="9a7ea-107">\<binding></span></span>  
<span data-ttu-id="9a7ea-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="9a7ea-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7ea-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a7ea-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a7ea-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a7ea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9a7ea-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a7ea-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a7ea-112">Attributes</span></span>  
 <span data-ttu-id="9a7ea-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a7ea-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a7ea-114">Child Elements</span></span>  
 <span data-ttu-id="9a7ea-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9a7ea-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a7ea-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a7ea-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9a7ea-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a7ea-117">Element</span></span>|<span data-ttu-id="9a7ea-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a7ea-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a7ea-119">\<binding></span><span class="sxs-lookup"><span data-stu-id="9a7ea-119">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9a7ea-120">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a7ea-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a7ea-121">Remarks</span></span>  
 <span data-ttu-id="9a7ea-122">Esse elemento é usado por um provedor de identidade para expressar em sua diretiva, o fato de que ele oferece suporte a perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="9a7ea-123">Provedores de identidade que tal uma declaração de política de publicação devem ser capazes de emitir tokens com base no perfil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="9a7ea-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7ea-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a7ea-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9a7ea-125">Associações</span><span class="sxs-lookup"><span data-stu-id="9a7ea-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9a7ea-126">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="9a7ea-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9a7ea-127">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9a7ea-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9a7ea-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9a7ea-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
