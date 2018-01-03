---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51db0762c10459d67929867a0fe44908dc7ec750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="dd17a-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="dd17a-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="dd17a-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="dd17a-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="dd17a-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="dd17a-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="dd17a-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dd17a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="dd17a-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dd17a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dd17a-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="dd17a-107">\<tracking></span></span>  
<span data-ttu-id="dd17a-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dd17a-108">\<trackingProfile></span></span>  
<span data-ttu-id="dd17a-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="dd17a-109">\<workflow></span></span>  
<span data-ttu-id="dd17a-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="dd17a-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="dd17a-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="dd17a-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd17a-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd17a-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd17a-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd17a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dd17a-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd17a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd17a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd17a-115">Attributes</span></span>  
  
|<span data-ttu-id="dd17a-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="dd17a-116">Attribute</span></span>|<span data-ttu-id="dd17a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd17a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd17a-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="dd17a-118">activityName</span></span>|<span data-ttu-id="dd17a-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="dd17a-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="dd17a-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="dd17a-120">childActivityName</span></span>|<span data-ttu-id="dd17a-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="dd17a-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd17a-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd17a-122">Child Elements</span></span>  
 <span data-ttu-id="dd17a-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dd17a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd17a-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd17a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dd17a-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd17a-125">Element</span></span>|<span data-ttu-id="dd17a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd17a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd17a-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="dd17a-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="dd17a-128">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="dd17a-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd17a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd17a-129">See Also</span></span>  
 <span data-ttu-id="dd17a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="dd17a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="dd17a-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="dd17a-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="dd17a-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="dd17a-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dd17a-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="dd17a-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
