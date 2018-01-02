---
title: '&lt;activityScheduledQuery&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb421993c39e66e437a0ecbb35091532df61716
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="f0b1e-102">&lt;activityScheduledQuery&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="f0b1e-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="f0b1e-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f0b1e-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="f0b1e-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f0b1e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="f0b1e-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f0b1e-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-107">\<tracking></span></span>  
<span data-ttu-id="f0b1e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-108">\<trackingProfile></span></span>  
<span data-ttu-id="f0b1e-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-109">\<workflow></span></span>  
<span data-ttu-id="f0b1e-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="f0b1e-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0b1e-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0b1e-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0b1e-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f0b1e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f0b1e-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0b1e-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="f0b1e-115">Attributes</span></span>  
  
|<span data-ttu-id="f0b1e-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="f0b1e-116">Attribute</span></span>|<span data-ttu-id="f0b1e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0b1e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0b1e-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="f0b1e-118">activityName</span></span>|<span data-ttu-id="f0b1e-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="f0b1e-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="f0b1e-120">childActivityName</span></span>|<span data-ttu-id="f0b1e-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0b1e-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f0b1e-122">Child Elements</span></span>  
 <span data-ttu-id="f0b1e-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0b1e-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f0b1e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f0b1e-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="f0b1e-125">Element</span></span>|<span data-ttu-id="f0b1e-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0b1e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0b1e-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f0b1e-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="f0b1e-128">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f0b1e-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0b1e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0b1e-129">See Also</span></span>  
 <span data-ttu-id="f0b1e-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="f0b1e-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="f0b1e-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="f0b1e-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="f0b1e-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0b1e-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f0b1e-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f0b1e-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
