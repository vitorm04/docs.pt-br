---
title: <bookmarkResumptionQueries> do WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 4b11543e240b482d52c157083d1184db4f81bb04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673427"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="113da-102">\<bookmarkResumptionQueries> of WCF</span><span class="sxs-lookup"><span data-stu-id="113da-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="113da-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="113da-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="113da-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="113da-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="113da-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="113da-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="113da-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="113da-106">\<system.serviceModel></span></span>  
<span data-ttu-id="113da-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="113da-107">\<tracking></span></span>  
<span data-ttu-id="113da-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="113da-108">\<profiles></span></span>  
<span data-ttu-id="113da-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="113da-109">\<trackingProfile></span></span>  
<span data-ttu-id="113da-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="113da-110">\<workflow></span></span>  
<span data-ttu-id="113da-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="113da-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="113da-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="113da-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="113da-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="113da-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="113da-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="113da-114">Attributes and elements</span></span>  
  
<span data-ttu-id="113da-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="113da-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="113da-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="113da-116">Attributes</span></span>  
  
<span data-ttu-id="113da-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="113da-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="113da-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="113da-118">Child elements</span></span>  
  
|<span data-ttu-id="113da-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="113da-119">Element</span></span>|<span data-ttu-id="113da-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="113da-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="113da-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="113da-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="113da-122">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="113da-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="113da-123">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="113da-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="113da-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="113da-124">Parent elements</span></span>  
  
|<span data-ttu-id="113da-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="113da-125">Element</span></span>|<span data-ttu-id="113da-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="113da-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="113da-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="113da-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="113da-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="113da-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="113da-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="113da-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="113da-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="113da-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="113da-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="113da-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
