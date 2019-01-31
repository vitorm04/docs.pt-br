---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 4277df5b4c36fa2f3571ba8441a7eb8aaf6d106a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261536"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="7fe40-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7fe40-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="7fe40-102">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7fe40-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7fe40-103">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="7fe40-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="7fe40-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7fe40-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7fe40-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7fe40-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7fe40-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="7fe40-106">\<tracking></span></span>  
<span data-ttu-id="7fe40-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7fe40-107">\<trackingProfile></span></span>  
<span data-ttu-id="7fe40-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7fe40-108">\<workflow></span></span>  
<span data-ttu-id="7fe40-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7fe40-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7fe40-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7fe40-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe40-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fe40-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fe40-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7fe40-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7fe40-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7fe40-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fe40-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7fe40-114">Attributes</span></span>  
 <span data-ttu-id="7fe40-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7fe40-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7fe40-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7fe40-116">Child Elements</span></span>  
  
|<span data-ttu-id="7fe40-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="7fe40-117">Element</span></span>|<span data-ttu-id="7fe40-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fe40-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fe40-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7fe40-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="7fe40-120">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7fe40-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7fe40-121">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="7fe40-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fe40-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7fe40-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7fe40-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7fe40-123">Element</span></span>|<span data-ttu-id="7fe40-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fe40-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fe40-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7fe40-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7fe40-126">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="7fe40-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fe40-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fe40-127">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7fe40-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7fe40-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7fe40-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7fe40-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
