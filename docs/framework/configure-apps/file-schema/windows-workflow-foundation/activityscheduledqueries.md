---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 2285dfae84f078483c03d85801051e29b79e74c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561836"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="48296-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="48296-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="48296-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="48296-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="48296-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="48296-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="48296-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="48296-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="48296-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="48296-106">\<system.serviceModel></span></span>  
<span data-ttu-id="48296-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="48296-107">\<tracking></span></span>  
<span data-ttu-id="48296-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="48296-108">\<trackingProfile></span></span>  
<span data-ttu-id="48296-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="48296-109">\<workflow></span></span>  
<span data-ttu-id="48296-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="48296-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48296-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48296-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48296-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48296-112">Attributes and Elements</span></span>  
 <span data-ttu-id="48296-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="48296-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48296-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="48296-114">Attributes</span></span>  
 <span data-ttu-id="48296-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="48296-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48296-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48296-116">Child Elements</span></span>  
  
|<span data-ttu-id="48296-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="48296-117">Element</span></span>|<span data-ttu-id="48296-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="48296-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48296-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="48296-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="48296-120">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="48296-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48296-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48296-121">Parent Elements</span></span>  
  
|<span data-ttu-id="48296-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="48296-122">Element</span></span>|<span data-ttu-id="48296-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="48296-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48296-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="48296-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="48296-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="48296-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48296-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48296-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="48296-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="48296-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="48296-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="48296-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
