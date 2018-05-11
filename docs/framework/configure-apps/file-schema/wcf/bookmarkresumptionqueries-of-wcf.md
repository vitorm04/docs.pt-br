---
title: '&lt;bookmarkResumptionQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 8a83f521e444838b6495221c00211710dd99ab6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="e346c-102">&lt;bookmarkResumptionQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="e346c-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="e346c-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e346c-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e346c-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="e346c-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="e346c-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e346c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e346c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e346c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e346c-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="e346c-107">\<tracking></span></span>  
<span data-ttu-id="e346c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e346c-108">\<trackingProfile></span></span>  
<span data-ttu-id="e346c-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e346c-109">\<workflow></span></span>  
<span data-ttu-id="e346c-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="e346c-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="e346c-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="e346c-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e346c-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e346c-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e346c-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e346c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e346c-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e346c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e346c-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="e346c-115">Attributes</span></span>  
 <span data-ttu-id="e346c-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e346c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e346c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e346c-117">Child Elements</span></span>  
  
|<span data-ttu-id="e346c-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e346c-118">Element</span></span>|<span data-ttu-id="e346c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e346c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e346c-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="e346c-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="e346c-121">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e346c-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e346c-122">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="e346c-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e346c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e346c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e346c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e346c-124">Element</span></span>|<span data-ttu-id="e346c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e346c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e346c-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e346c-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e346c-127">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="e346c-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e346c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e346c-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="e346c-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e346c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e346c-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e346c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
