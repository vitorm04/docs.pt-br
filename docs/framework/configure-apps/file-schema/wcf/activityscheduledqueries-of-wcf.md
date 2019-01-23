---
title: '&lt;activityScheduledQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 5430058049e8a09c1e2a289e1f997338c23b9d94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492150"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="0b950-102">&lt;activityScheduledQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="0b950-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="0b950-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="0b950-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="0b950-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="0b950-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="0b950-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0b950-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0b950-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0b950-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0b950-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="0b950-107">\<tracking></span></span>  
<span data-ttu-id="0b950-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="0b950-108">\<profiles></span></span>  
<span data-ttu-id="0b950-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0b950-109">\<trackingProfile></span></span>  
<span data-ttu-id="0b950-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0b950-110">\<workflow></span></span>  
<span data-ttu-id="0b950-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="0b950-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b950-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b950-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b950-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b950-113">Attributes and elements</span></span>  

<span data-ttu-id="0b950-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b950-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b950-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b950-115">Attributes</span></span>  

<span data-ttu-id="0b950-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b950-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0b950-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b950-117">Child elements</span></span>  
  
|<span data-ttu-id="0b950-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b950-118">Element</span></span>|<span data-ttu-id="0b950-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b950-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b950-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="0b950-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="0b950-121">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="0b950-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b950-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b950-122">Parent elements</span></span>  
  
|<span data-ttu-id="0b950-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b950-123">Element</span></span>|<span data-ttu-id="0b950-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b950-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b950-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0b950-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="0b950-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0b950-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b950-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b950-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="0b950-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0b950-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0b950-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0b950-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
