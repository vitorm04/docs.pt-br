---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 7217fb886cc96e1ad19f96e2c6542277cfc7979e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175754"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="c54a5-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="c54a5-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="c54a5-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c54a5-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c54a5-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="c54a5-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="c54a5-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c54a5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c54a5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c54a5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c54a5-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c54a5-106">\<tracking></span></span>  
<span data-ttu-id="c54a5-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c54a5-107">\<trackingProfile></span></span>  
<span data-ttu-id="c54a5-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c54a5-108">\<workflow></span></span>  
<span data-ttu-id="c54a5-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="c54a5-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c54a5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c54a5-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c54a5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c54a5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c54a5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c54a5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c54a5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c54a5-113">Attributes</span></span>  
 <span data-ttu-id="c54a5-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c54a5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c54a5-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c54a5-115">Child Elements</span></span>  
  
|<span data-ttu-id="c54a5-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="c54a5-116">Element</span></span>|<span data-ttu-id="c54a5-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c54a5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c54a5-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="c54a5-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="c54a5-119">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c54a5-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c54a5-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c54a5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c54a5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c54a5-121">Element</span></span>|<span data-ttu-id="c54a5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c54a5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c54a5-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c54a5-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c54a5-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c54a5-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c54a5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c54a5-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c54a5-126">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c54a5-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c54a5-127">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c54a5-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
