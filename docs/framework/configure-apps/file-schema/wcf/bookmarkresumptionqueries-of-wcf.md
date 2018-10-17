---
title: '&lt;bookmarkResumptionQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: d2b3365f3793c114003bbd9b9da664448bbac243
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374428"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="9d156-102">&lt;bookmarkResumptionQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="9d156-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>

<span data-ttu-id="9d156-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9d156-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9d156-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="9d156-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="9d156-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9d156-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="9d156-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9d156-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9d156-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="9d156-107">\<tracking></span></span>  
<span data-ttu-id="9d156-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="9d156-108">\<profiles></span></span>  
<span data-ttu-id="9d156-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9d156-109">\<trackingProfile></span></span>  
<span data-ttu-id="9d156-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9d156-110">\<workflow></span></span>  
<span data-ttu-id="9d156-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="9d156-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="9d156-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9d156-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d156-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d156-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="9d156-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9d156-114">Attributes and elements</span></span>

<span data-ttu-id="9d156-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9d156-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d156-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d156-116">Attributes</span></span>

<span data-ttu-id="9d156-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9d156-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d156-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9d156-118">Child elements</span></span>  
  
|<span data-ttu-id="9d156-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d156-119">Element</span></span>|<span data-ttu-id="9d156-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d156-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d156-121">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9d156-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="9d156-122">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9d156-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9d156-123">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="9d156-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d156-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9d156-124">Parent elements</span></span>  
  
|<span data-ttu-id="9d156-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d156-125">Element</span></span>|<span data-ttu-id="9d156-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d156-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d156-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9d156-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9d156-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="9d156-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d156-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d156-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType> 
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="9d156-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9d156-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="9d156-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="9d156-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
