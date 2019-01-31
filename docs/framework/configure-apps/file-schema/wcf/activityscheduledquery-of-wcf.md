---
title: <activityScheduledQuery> do WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 5087d56092296f8c68b719ec0945993adeb3de0a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272897"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="cdc85-102">\<activityScheduledQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="cdc85-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="cdc85-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cdc85-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cdc85-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="cdc85-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="cdc85-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cdc85-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cdc85-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cdc85-106">\<system.serviceModel></span></span>  
<span data-ttu-id="cdc85-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="cdc85-107">\<tracking></span></span>  
<span data-ttu-id="cdc85-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="cdc85-108">\<profiles></span></span>  
<span data-ttu-id="cdc85-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cdc85-109">\<trackingProfile></span></span>  
<span data-ttu-id="cdc85-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cdc85-110">\<workflow></span></span>  
<span data-ttu-id="cdc85-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="cdc85-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="cdc85-112">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="cdc85-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc85-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdc85-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdc85-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cdc85-114">Attributes and elements</span></span>  

<span data-ttu-id="cdc85-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cdc85-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdc85-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="cdc85-116">Attributes</span></span>  
  
|<span data-ttu-id="cdc85-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="cdc85-117">Attribute</span></span>|<span data-ttu-id="cdc85-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdc85-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="cdc85-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="cdc85-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="cdc85-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="cdc85-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdc85-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cdc85-121">Child elements</span></span>

<span data-ttu-id="cdc85-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cdc85-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="cdc85-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cdc85-123">Parent elements</span></span>  
  
|<span data-ttu-id="cdc85-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdc85-124">Element</span></span>|<span data-ttu-id="cdc85-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdc85-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdc85-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="cdc85-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="cdc85-127">Uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cdc85-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdc85-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdc85-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="cdc85-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="cdc85-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cdc85-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="cdc85-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
