---
title: <bookmarkResumptionQueries>do WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 5ec9827e9862866096265da576c91b10573012d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919737"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="b06e7-102">\<bookmarkResumptionQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="b06e7-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="b06e7-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b06e7-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b06e7-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="b06e7-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="b06e7-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b06e7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="b06e7-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b06e7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b06e7-107">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="b06e7-107">\<tracking></span></span>  
<span data-ttu-id="b06e7-108">\<perfis ></span><span class="sxs-lookup"><span data-stu-id="b06e7-108">\<profiles></span></span>  
<span data-ttu-id="b06e7-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b06e7-109">\<trackingProfile></span></span>  
<span data-ttu-id="b06e7-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b06e7-110">\<workflow></span></span>  
<span data-ttu-id="b06e7-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="b06e7-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="b06e7-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="b06e7-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b06e7-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b06e7-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b06e7-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b06e7-114">Attributes and elements</span></span>  
  
<span data-ttu-id="b06e7-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b06e7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b06e7-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="b06e7-116">Attributes</span></span>  
  
<span data-ttu-id="b06e7-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b06e7-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b06e7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b06e7-118">Child elements</span></span>  
  
|<span data-ttu-id="b06e7-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b06e7-119">Element</span></span>|<span data-ttu-id="b06e7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b06e7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b06e7-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="b06e7-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="b06e7-122">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b06e7-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b06e7-123">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="b06e7-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b06e7-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b06e7-124">Parent elements</span></span>  
  
|<span data-ttu-id="b06e7-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b06e7-125">Element</span></span>|<span data-ttu-id="b06e7-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b06e7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b06e7-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b06e7-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b06e7-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="b06e7-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b06e7-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b06e7-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b06e7-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b06e7-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b06e7-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b06e7-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
