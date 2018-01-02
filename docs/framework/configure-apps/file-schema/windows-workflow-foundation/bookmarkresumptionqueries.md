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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="19d65-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="19d65-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="19d65-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="19d65-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="19d65-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="19d65-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="19d65-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="19d65-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="19d65-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="19d65-106">\<system.serviceModel></span></span>  
<span data-ttu-id="19d65-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="19d65-107">\<tracking></span></span>  
<span data-ttu-id="19d65-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="19d65-108">\<trackingProfile></span></span>  
<span data-ttu-id="19d65-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="19d65-109">\<workflow></span></span>  
<span data-ttu-id="19d65-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="19d65-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="19d65-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="19d65-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d65-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19d65-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19d65-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="19d65-113">Attributes and Elements</span></span>  
 <span data-ttu-id="19d65-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="19d65-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19d65-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="19d65-115">Attributes</span></span>  
 <span data-ttu-id="19d65-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="19d65-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19d65-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="19d65-117">Child Elements</span></span>  
  
|<span data-ttu-id="19d65-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="19d65-118">Element</span></span>|<span data-ttu-id="19d65-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="19d65-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19d65-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="19d65-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="19d65-121">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="19d65-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="19d65-122">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="19d65-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19d65-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="19d65-123">Parent Elements</span></span>  
  
|<span data-ttu-id="19d65-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="19d65-124">Element</span></span>|<span data-ttu-id="19d65-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="19d65-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19d65-126">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="19d65-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="19d65-127">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="19d65-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19d65-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19d65-128">See Also</span></span>  
 <span data-ttu-id="19d65-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="19d65-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="19d65-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="19d65-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="19d65-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="19d65-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="19d65-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="19d65-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
