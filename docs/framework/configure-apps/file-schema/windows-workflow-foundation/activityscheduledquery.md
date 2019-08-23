---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: dc04405204be7c5484d47b4a3767f846b11abf9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945498"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="7c3f4-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="7c3f4-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="7c3f4-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7c3f4-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="7c3f4-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7c3f4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7c3f4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7c3f4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7c3f4-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="7c3f4-106">\<tracking></span></span>  
<span data-ttu-id="7c3f4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7c3f4-107">\<trackingProfile></span></span>  
<span data-ttu-id="7c3f4-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7c3f4-108">\<workflow></span></span>  
<span data-ttu-id="7c3f4-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="7c3f4-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="7c3f4-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="7c3f4-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c3f4-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c3f4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c3f4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c3f4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7c3f4-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c3f4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c3f4-114">Attributes</span></span>  
  
|<span data-ttu-id="7c3f4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7c3f4-115">Attribute</span></span>|<span data-ttu-id="7c3f4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c3f4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c3f4-117">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="7c3f4-117">activityName</span></span>|<span data-ttu-id="7c3f4-118">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="7c3f4-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="7c3f4-119">childActivityName</span></span>|<span data-ttu-id="7c3f4-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c3f4-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c3f4-121">Child Elements</span></span>  
 <span data-ttu-id="7c3f4-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c3f4-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c3f4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7c3f4-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c3f4-124">Element</span></span>|<span data-ttu-id="7c3f4-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c3f4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c3f4-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="7c3f4-126">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="7c3f4-127">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7c3f4-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c3f4-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c3f4-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7c3f4-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7c3f4-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7c3f4-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7c3f4-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
