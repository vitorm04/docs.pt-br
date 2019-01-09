---
title: '&lt;activityScheduledQuery&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: fd7830bc178de0693f0632cea3b390d792408ec1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147870"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="63f20-102">&lt;activityScheduledQuery&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="63f20-102">&lt;activityScheduledQuery&gt; of WCF</span></span>

<span data-ttu-id="63f20-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="63f20-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="63f20-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="63f20-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="63f20-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="63f20-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="63f20-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="63f20-106">\<system.serviceModel></span></span>  
<span data-ttu-id="63f20-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="63f20-107">\<tracking></span></span>  
<span data-ttu-id="63f20-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="63f20-108">\<profiles></span></span>  
<span data-ttu-id="63f20-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="63f20-109">\<trackingProfile></span></span>  
<span data-ttu-id="63f20-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="63f20-110">\<workflow></span></span>  
<span data-ttu-id="63f20-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="63f20-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="63f20-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="63f20-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f20-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63f20-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63f20-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63f20-114">Attributes and elements</span></span>  

<span data-ttu-id="63f20-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63f20-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63f20-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="63f20-116">Attributes</span></span>  
  
|<span data-ttu-id="63f20-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="63f20-117">Attribute</span></span>|<span data-ttu-id="63f20-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="63f20-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="63f20-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="63f20-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="63f20-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="63f20-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63f20-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63f20-121">Child elements</span></span>

<span data-ttu-id="63f20-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="63f20-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="63f20-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63f20-123">Parent elements</span></span>  
  
|<span data-ttu-id="63f20-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="63f20-124">Element</span></span>|<span data-ttu-id="63f20-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="63f20-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63f20-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="63f20-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="63f20-127">Uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="63f20-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63f20-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63f20-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="63f20-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="63f20-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63f20-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="63f20-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
