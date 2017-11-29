---
title: '&lt;activityScheduledQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 686b58d9efa4420de26fd7be52fe76208af63c6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="8d13f-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="8d13f-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="8d13f-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="8d13f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="8d13f-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="8d13f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="8d13f-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8d13f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8d13f-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8d13f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8d13f-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="8d13f-107">\<tracking></span></span>  
<span data-ttu-id="8d13f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8d13f-108">\<trackingProfile></span></span>  
<span data-ttu-id="8d13f-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="8d13f-109">\<workflow></span></span>  
<span data-ttu-id="8d13f-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="8d13f-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d13f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d13f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d13f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d13f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8d13f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d13f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d13f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d13f-114">Attributes</span></span>  
 <span data-ttu-id="8d13f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8d13f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d13f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d13f-116">Child Elements</span></span>  
  
|<span data-ttu-id="8d13f-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d13f-117">Element</span></span>|<span data-ttu-id="8d13f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d13f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d13f-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="8d13f-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="8d13f-120">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="8d13f-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d13f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d13f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8d13f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d13f-122">Element</span></span>|<span data-ttu-id="8d13f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d13f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d13f-124">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="8d13f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8d13f-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d13f-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d13f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d13f-126">See Also</span></span>  
 <span data-ttu-id="8d13f-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8d13f-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8d13f-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8d13f-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8d13f-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d13f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8d13f-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8d13f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
