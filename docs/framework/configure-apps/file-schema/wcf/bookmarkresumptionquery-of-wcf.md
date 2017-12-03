---
title: '&lt;bookmarkResumptionQuery&gt; of WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124b05d8e1ce9831a1efb3c6e62cc5e9fd3058fc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="c6797-102">&lt;bookmarkResumptionQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="c6797-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="c6797-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c6797-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c6797-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="c6797-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="c6797-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c6797-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="c6797-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c6797-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c6797-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="c6797-107">\<tracking></span></span>  
<span data-ttu-id="c6797-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c6797-108">\<trackingProfile></span></span>  
<span data-ttu-id="c6797-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="c6797-109">\<workflow></span></span>  
<span data-ttu-id="c6797-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="c6797-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="c6797-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="c6797-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6797-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6797-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6797-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6797-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c6797-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6797-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6797-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6797-115">Attributes</span></span>  
  
|<span data-ttu-id="c6797-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6797-116">Attribute</span></span>|<span data-ttu-id="c6797-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6797-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6797-118">name</span><span class="sxs-lookup"><span data-stu-id="c6797-118">name</span></span>|<span data-ttu-id="c6797-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="c6797-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6797-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6797-120">Child Elements</span></span>  
 <span data-ttu-id="c6797-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c6797-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6797-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6797-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c6797-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6797-123">Element</span></span>|<span data-ttu-id="c6797-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6797-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6797-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="c6797-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="c6797-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c6797-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6797-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6797-127">See Also</span></span>  
 <span data-ttu-id="c6797-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c6797-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c6797-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c6797-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="c6797-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c6797-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c6797-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c6797-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
