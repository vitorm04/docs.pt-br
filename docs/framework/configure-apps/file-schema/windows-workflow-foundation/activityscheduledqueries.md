---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 89de9ef10449fbae78a8c5b558101a2cf6477b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945530"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="647a7-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="647a7-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="647a7-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="647a7-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="647a7-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="647a7-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="647a7-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="647a7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="647a7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="647a7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="647a7-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="647a7-106">\<tracking></span></span>  
<span data-ttu-id="647a7-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="647a7-107">\<trackingProfile></span></span>  
<span data-ttu-id="647a7-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="647a7-108">\<workflow></span></span>  
<span data-ttu-id="647a7-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="647a7-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647a7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="647a7-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="647a7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="647a7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="647a7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="647a7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="647a7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="647a7-113">Attributes</span></span>  
 <span data-ttu-id="647a7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="647a7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="647a7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="647a7-115">Child Elements</span></span>  
  
|<span data-ttu-id="647a7-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="647a7-116">Element</span></span>|<span data-ttu-id="647a7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="647a7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="647a7-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="647a7-118">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="647a7-119">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="647a7-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="647a7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="647a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="647a7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="647a7-121">Element</span></span>|<span data-ttu-id="647a7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="647a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="647a7-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="647a7-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="647a7-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="647a7-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="647a7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="647a7-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="647a7-126">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="647a7-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="647a7-127">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="647a7-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
