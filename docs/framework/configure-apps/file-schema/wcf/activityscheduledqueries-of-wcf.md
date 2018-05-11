---
title: '&lt;activityScheduledQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 946406e5513a0fee6793071c397f61bf1fe71c65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="381dc-102">&lt;activityScheduledQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="381dc-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="381dc-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="381dc-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="381dc-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="381dc-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="381dc-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="381dc-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="381dc-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="381dc-106">\<system.serviceModel></span></span>  
<span data-ttu-id="381dc-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="381dc-107">\<tracking></span></span>  
<span data-ttu-id="381dc-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="381dc-108">\<trackingProfile></span></span>  
<span data-ttu-id="381dc-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="381dc-109">\<workflow></span></span>  
<span data-ttu-id="381dc-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="381dc-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381dc-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="381dc-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="381dc-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="381dc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="381dc-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="381dc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="381dc-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="381dc-114">Attributes</span></span>  
 <span data-ttu-id="381dc-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="381dc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="381dc-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="381dc-116">Child Elements</span></span>  
  
|<span data-ttu-id="381dc-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="381dc-117">Element</span></span>|<span data-ttu-id="381dc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="381dc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="381dc-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="381dc-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="381dc-120">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="381dc-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="381dc-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="381dc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="381dc-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="381dc-122">Element</span></span>|<span data-ttu-id="381dc-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="381dc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="381dc-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="381dc-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="381dc-125">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="381dc-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="381dc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="381dc-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="381dc-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="381dc-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="381dc-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="381dc-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
