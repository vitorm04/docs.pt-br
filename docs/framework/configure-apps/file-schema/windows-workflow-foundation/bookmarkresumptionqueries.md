---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bf209525bcc9748e9a5f5b71a0407a4eca1a897
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="fba45-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="fba45-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="fba45-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fba45-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fba45-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="fba45-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="fba45-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fba45-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fba45-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fba45-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fba45-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="fba45-107">\<tracking></span></span>  
<span data-ttu-id="fba45-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="fba45-108">\<trackingProfile></span></span>  
<span data-ttu-id="fba45-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="fba45-109">\<workflow></span></span>  
<span data-ttu-id="fba45-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="fba45-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="fba45-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="fba45-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba45-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fba45-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fba45-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fba45-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fba45-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fba45-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fba45-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="fba45-115">Attributes</span></span>  
 <span data-ttu-id="fba45-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fba45-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fba45-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fba45-117">Child Elements</span></span>  
  
|<span data-ttu-id="fba45-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="fba45-118">Element</span></span>|<span data-ttu-id="fba45-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fba45-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fba45-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="fba45-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="fba45-121">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fba45-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fba45-122">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="fba45-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fba45-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fba45-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fba45-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="fba45-124">Element</span></span>|<span data-ttu-id="fba45-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="fba45-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fba45-126">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="fba45-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fba45-127">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="fba45-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fba45-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fba45-128">See Also</span></span>  
 <span data-ttu-id="fba45-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fba45-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="fba45-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fba45-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="fba45-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="fba45-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="fba45-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="fba45-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
