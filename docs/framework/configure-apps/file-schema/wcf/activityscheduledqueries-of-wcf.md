---
title: '&lt;activityScheduledQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 35bcb0dc0c33d30eee566869579edb32f131f495
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452690"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="b32d2-102">&lt;activityScheduledQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="b32d2-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="b32d2-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b32d2-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b32d2-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="b32d2-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="b32d2-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b32d2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b32d2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b32d2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b32d2-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="b32d2-107">\<tracking></span></span>  
<span data-ttu-id="b32d2-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="b32d2-108">\<profiles></span></span>  
<span data-ttu-id="b32d2-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b32d2-109">\<trackingProfile></span></span>  
<span data-ttu-id="b32d2-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b32d2-110">\<workflow></span></span>  
<span data-ttu-id="b32d2-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="b32d2-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b32d2-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b32d2-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"   
                                  childActivityName="String"/>
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b32d2-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b32d2-113">Attributes and elements</span></span>  

<span data-ttu-id="b32d2-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b32d2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b32d2-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b32d2-115">Attributes</span></span>  

<span data-ttu-id="b32d2-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b32d2-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b32d2-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b32d2-117">Child elements</span></span>  
  
|<span data-ttu-id="b32d2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b32d2-118">Element</span></span>|<span data-ttu-id="b32d2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b32d2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b32d2-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b32d2-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="b32d2-121">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b32d2-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b32d2-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b32d2-122">Parent elements</span></span>  
  
|<span data-ttu-id="b32d2-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b32d2-123">Element</span></span>|<span data-ttu-id="b32d2-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b32d2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b32d2-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b32d2-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b32d2-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="b32d2-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b32d2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b32d2-127">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="b32d2-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b32d2-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b32d2-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b32d2-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
