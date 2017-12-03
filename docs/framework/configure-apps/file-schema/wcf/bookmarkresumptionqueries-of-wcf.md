---
title: '&lt;bookmarkResumptionQueries&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa46d62262b91d5b88564b50f97fccf7aefefa6d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="10492-102">&lt;bookmarkResumptionQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="10492-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="10492-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="10492-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="10492-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="10492-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="10492-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10492-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="10492-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="10492-106">\<system.serviceModel></span></span>  
<span data-ttu-id="10492-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="10492-107">\<tracking></span></span>  
<span data-ttu-id="10492-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="10492-108">\<trackingProfile></span></span>  
<span data-ttu-id="10492-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="10492-109">\<workflow></span></span>  
<span data-ttu-id="10492-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="10492-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="10492-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="10492-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10492-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10492-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10492-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="10492-113">Attributes and Elements</span></span>  
 <span data-ttu-id="10492-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="10492-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10492-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="10492-115">Attributes</span></span>  
 <span data-ttu-id="10492-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="10492-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10492-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="10492-117">Child Elements</span></span>  
  
|<span data-ttu-id="10492-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="10492-118">Element</span></span>|<span data-ttu-id="10492-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="10492-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10492-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="10492-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="10492-121">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="10492-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="10492-122">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="10492-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10492-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="10492-123">Parent Elements</span></span>  
  
|<span data-ttu-id="10492-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="10492-124">Element</span></span>|<span data-ttu-id="10492-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="10492-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10492-126">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="10492-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="10492-127">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="10492-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10492-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10492-128">See Also</span></span>  
 <span data-ttu-id="10492-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="10492-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="10492-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="10492-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="10492-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="10492-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="10492-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="10492-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
