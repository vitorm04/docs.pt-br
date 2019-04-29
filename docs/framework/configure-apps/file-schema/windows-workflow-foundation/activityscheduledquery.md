---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: d49c6d933a09dce5d657746358f1a5f716ab639b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790410"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="241e7-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="241e7-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="241e7-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="241e7-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="241e7-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="241e7-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="241e7-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="241e7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="241e7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="241e7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="241e7-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="241e7-106">\<tracking></span></span>  
<span data-ttu-id="241e7-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="241e7-107">\<trackingProfile></span></span>  
<span data-ttu-id="241e7-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="241e7-108">\<workflow></span></span>  
<span data-ttu-id="241e7-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="241e7-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="241e7-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="241e7-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="241e7-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="241e7-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="241e7-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="241e7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="241e7-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="241e7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="241e7-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="241e7-114">Attributes</span></span>  
  
|<span data-ttu-id="241e7-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="241e7-115">Attribute</span></span>|<span data-ttu-id="241e7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="241e7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="241e7-117">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="241e7-117">activityName</span></span>|<span data-ttu-id="241e7-118">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="241e7-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="241e7-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="241e7-119">childActivityName</span></span>|<span data-ttu-id="241e7-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="241e7-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="241e7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="241e7-121">Child Elements</span></span>  
 <span data-ttu-id="241e7-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="241e7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="241e7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="241e7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="241e7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="241e7-124">Element</span></span>|<span data-ttu-id="241e7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="241e7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="241e7-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="241e7-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="241e7-127">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="241e7-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="241e7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="241e7-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="241e7-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="241e7-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="241e7-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="241e7-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
