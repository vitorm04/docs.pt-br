---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 186990577ec4eedc7cae3710c455816c3162fc94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109403"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="c5be5-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="c5be5-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="c5be5-102">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5be5-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c5be5-103">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="c5be5-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="c5be5-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c5be5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c5be5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5be5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c5be5-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c5be5-106">\<tracking></span></span>  
<span data-ttu-id="c5be5-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c5be5-107">\<trackingProfile></span></span>  
<span data-ttu-id="c5be5-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c5be5-108">\<workflow></span></span>  
<span data-ttu-id="c5be5-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="c5be5-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="c5be5-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="c5be5-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5be5-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5be5-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5be5-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5be5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c5be5-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5be5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5be5-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5be5-114">Attributes</span></span>  
 <span data-ttu-id="c5be5-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c5be5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5be5-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5be5-116">Child Elements</span></span>  
  
|<span data-ttu-id="c5be5-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5be5-117">Element</span></span>|<span data-ttu-id="c5be5-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5be5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5be5-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="c5be5-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="c5be5-120">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5be5-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c5be5-121">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="c5be5-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5be5-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5be5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c5be5-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5be5-123">Element</span></span>|<span data-ttu-id="c5be5-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5be5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5be5-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c5be5-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c5be5-126">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c5be5-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5be5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5be5-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c5be5-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c5be5-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c5be5-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c5be5-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
