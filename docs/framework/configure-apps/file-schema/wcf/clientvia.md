---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cdc85c23202154728610ab4721bf830004928c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="bbbfb-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="bbbfb-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="bbbfb-103">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="bbbfb-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="bbbfb-104">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="bbbfb-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="bbbfb-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bbbfb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bbbfb-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="bbbfb-106">\<behaviors></span></span>  
<span data-ttu-id="bbbfb-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bbbfb-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="bbbfb-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="bbbfb-108">\<behavior></span></span>  
<span data-ttu-id="bbbfb-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="bbbfb-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbfb-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbbfb-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbbfb-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bbbfb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bbbfb-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bbbfb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbbfb-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="bbbfb-113">Attributes</span></span>  
  
|<span data-ttu-id="bbbfb-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="bbbfb-114">Attribute</span></span>|<span data-ttu-id="bbbfb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbbfb-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="bbbfb-116">Uma cadeia de caracteres que especifica um URI que indica a rota que uma mensagem deve seguir.</span><span class="sxs-lookup"><span data-stu-id="bbbfb-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbbfb-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bbbfb-117">Child Elements</span></span>  
 <span data-ttu-id="bbbfb-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bbbfb-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbbfb-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bbbfb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bbbfb-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbbfb-120">Element</span></span>|<span data-ttu-id="bbbfb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbbfb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbbfb-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="bbbfb-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bbbfb-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="bbbfb-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbbfb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbbfb-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
