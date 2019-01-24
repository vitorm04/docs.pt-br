---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: ae6a81123379ecd0e7fdc72f4e115a462f81eb90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555031"
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="60aa0-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="60aa0-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="60aa0-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="60aa0-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="60aa0-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="60aa0-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="60aa0-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="60aa0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="60aa0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="60aa0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="60aa0-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="60aa0-107">\<tracking></span></span>  
<span data-ttu-id="60aa0-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="60aa0-108">\<trackingProfile></span></span>  
<span data-ttu-id="60aa0-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="60aa0-109">\<workflow></span></span>  
<span data-ttu-id="60aa0-110">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="60aa0-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="60aa0-111">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="60aa0-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60aa0-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60aa0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60aa0-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60aa0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="60aa0-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60aa0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60aa0-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="60aa0-115">Attributes</span></span>  
 <span data-ttu-id="60aa0-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="60aa0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60aa0-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60aa0-117">Child Elements</span></span>  
  
|<span data-ttu-id="60aa0-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="60aa0-118">Element</span></span>|<span data-ttu-id="60aa0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="60aa0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60aa0-120">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="60aa0-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="60aa0-121">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="60aa0-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="60aa0-122">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="60aa0-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60aa0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60aa0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="60aa0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="60aa0-124">Element</span></span>|<span data-ttu-id="60aa0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="60aa0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60aa0-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="60aa0-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="60aa0-127">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="60aa0-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60aa0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60aa0-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="60aa0-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="60aa0-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="60aa0-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="60aa0-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
