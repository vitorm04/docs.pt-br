---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 2199e66342c6fa3afca9d8ccd3b620560b123ede
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260834"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="6be29-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="6be29-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="6be29-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6be29-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="6be29-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="6be29-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="6be29-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6be29-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6be29-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6be29-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6be29-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="6be29-106">\<tracking></span></span>  
<span data-ttu-id="6be29-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6be29-107">\<trackingProfile></span></span>  
<span data-ttu-id="6be29-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6be29-108">\<workflow></span></span>  
<span data-ttu-id="6be29-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="6be29-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="6be29-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="6be29-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6be29-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6be29-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6be29-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6be29-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6be29-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6be29-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6be29-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6be29-114">Attributes</span></span>  
  
|<span data-ttu-id="6be29-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="6be29-115">Attribute</span></span>|<span data-ttu-id="6be29-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6be29-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6be29-117">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="6be29-117">activityName</span></span>|<span data-ttu-id="6be29-118">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="6be29-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="6be29-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="6be29-119">childActivityName</span></span>|<span data-ttu-id="6be29-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="6be29-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6be29-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6be29-121">Child Elements</span></span>  
 <span data-ttu-id="6be29-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6be29-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6be29-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6be29-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6be29-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6be29-124">Element</span></span>|<span data-ttu-id="6be29-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6be29-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6be29-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="6be29-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="6be29-127">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6be29-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6be29-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6be29-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6be29-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6be29-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6be29-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6be29-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
