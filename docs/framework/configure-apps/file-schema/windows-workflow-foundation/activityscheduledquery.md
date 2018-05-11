---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0822d0ce7dd82ff396596a0ed2431a5f2084ad8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="b30aa-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b30aa-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="b30aa-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b30aa-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b30aa-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="b30aa-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="b30aa-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b30aa-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b30aa-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b30aa-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b30aa-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="b30aa-107">\<tracking></span></span>  
<span data-ttu-id="b30aa-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b30aa-108">\<trackingProfile></span></span>  
<span data-ttu-id="b30aa-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b30aa-109">\<workflow></span></span>  
<span data-ttu-id="b30aa-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="b30aa-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="b30aa-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b30aa-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b30aa-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b30aa-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b30aa-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b30aa-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b30aa-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b30aa-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b30aa-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b30aa-115">Attributes</span></span>  
  
|<span data-ttu-id="b30aa-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b30aa-116">Attribute</span></span>|<span data-ttu-id="b30aa-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b30aa-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b30aa-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="b30aa-118">activityName</span></span>|<span data-ttu-id="b30aa-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="b30aa-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b30aa-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b30aa-120">childActivityName</span></span>|<span data-ttu-id="b30aa-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="b30aa-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b30aa-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b30aa-122">Child Elements</span></span>  
 <span data-ttu-id="b30aa-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b30aa-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b30aa-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b30aa-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b30aa-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b30aa-125">Element</span></span>|<span data-ttu-id="b30aa-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b30aa-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b30aa-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b30aa-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="b30aa-128">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b30aa-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b30aa-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b30aa-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="b30aa-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b30aa-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b30aa-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b30aa-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
