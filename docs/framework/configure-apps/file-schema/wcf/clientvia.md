---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 48e56b79f47e84122ddd4d7f55d50044510bfa66
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149045"
---
# <a name="ltclientviagt"></a><span data-ttu-id="cb779-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="cb779-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="cb779-103">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="cb779-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="cb779-104">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="cb779-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="cb779-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cb779-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cb779-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="cb779-106">\<behaviors></span></span>  
<span data-ttu-id="cb779-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="cb779-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="cb779-108">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="cb779-108">\<behavior></span></span>  
<span data-ttu-id="cb779-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="cb779-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb779-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb779-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb779-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb779-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cb779-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cb779-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb779-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb779-113">Attributes</span></span>  
  
|<span data-ttu-id="cb779-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="cb779-114">Attribute</span></span>|<span data-ttu-id="cb779-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb779-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="cb779-116">Uma cadeia de caracteres que especifica um URI que indica a rota que uma mensagem deve seguir.</span><span class="sxs-lookup"><span data-stu-id="cb779-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb779-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cb779-117">Child Elements</span></span>  
 <span data-ttu-id="cb779-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cb779-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb779-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb779-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cb779-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb779-120">Element</span></span>|<span data-ttu-id="cb779-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb779-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb779-122">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="cb779-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cb779-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cb779-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb779-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb779-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
