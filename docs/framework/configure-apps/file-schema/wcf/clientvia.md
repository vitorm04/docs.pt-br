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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3782eb9cbe793fef450c8b1c58456a1d4f7b0b94
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="a75f9-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="a75f9-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="a75f9-103">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="a75f9-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="a75f9-104">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a75f9-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="a75f9-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a75f9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a75f9-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a75f9-106">\<behaviors></span></span>  
<span data-ttu-id="a75f9-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a75f9-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a75f9-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="a75f9-108">\<behavior></span></span>  
<span data-ttu-id="a75f9-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="a75f9-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75f9-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a75f9-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a75f9-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a75f9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a75f9-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a75f9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a75f9-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a75f9-113">Attributes</span></span>  
  
|<span data-ttu-id="a75f9-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a75f9-114">Attribute</span></span>|<span data-ttu-id="a75f9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a75f9-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="a75f9-116">Uma cadeia de caracteres que especifica um URI que indica a rota que uma mensagem deve seguir.</span><span class="sxs-lookup"><span data-stu-id="a75f9-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a75f9-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a75f9-117">Child Elements</span></span>  
 <span data-ttu-id="a75f9-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a75f9-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a75f9-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a75f9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a75f9-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="a75f9-120">Element</span></span>|<span data-ttu-id="a75f9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a75f9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a75f9-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="a75f9-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a75f9-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a75f9-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a75f9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a75f9-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
