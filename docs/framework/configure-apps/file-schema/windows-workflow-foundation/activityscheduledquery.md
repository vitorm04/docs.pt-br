---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0e69c32a7c292fda90828396c402c95e4899600a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687434"
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="4292f-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="4292f-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="4292f-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="4292f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="4292f-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="4292f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="4292f-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4292f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4292f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4292f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4292f-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="4292f-107">\<tracking></span></span>  
<span data-ttu-id="4292f-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4292f-108">\<trackingProfile></span></span>  
<span data-ttu-id="4292f-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4292f-109">\<workflow></span></span>  
<span data-ttu-id="4292f-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="4292f-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="4292f-111">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="4292f-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4292f-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4292f-112">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4292f-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4292f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4292f-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4292f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4292f-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="4292f-115">Attributes</span></span>  
  
|<span data-ttu-id="4292f-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="4292f-116">Attribute</span></span>|<span data-ttu-id="4292f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4292f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4292f-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="4292f-118">activityName</span></span>|<span data-ttu-id="4292f-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4292f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="4292f-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="4292f-120">childActivityName</span></span>|<span data-ttu-id="4292f-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="4292f-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4292f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4292f-122">Child Elements</span></span>  
 <span data-ttu-id="4292f-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4292f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4292f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4292f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4292f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="4292f-125">Element</span></span>|<span data-ttu-id="4292f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="4292f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4292f-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="4292f-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="4292f-128">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="4292f-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4292f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4292f-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4292f-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4292f-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4292f-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4292f-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
