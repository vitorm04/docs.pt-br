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
ms.openlocfilehash: 260b77789df6a03b640895ed158c94bfd1533f9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="50bf9-102">&lt;activityScheduledQuery&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="50bf9-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="50bf9-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="50bf9-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="50bf9-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="50bf9-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="50bf9-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="50bf9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="50bf9-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="50bf9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="50bf9-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="50bf9-107">\<tracking></span></span>  
<span data-ttu-id="50bf9-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="50bf9-108">\<trackingProfile></span></span>  
<span data-ttu-id="50bf9-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="50bf9-109">\<workflow></span></span>  
<span data-ttu-id="50bf9-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="50bf9-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="50bf9-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="50bf9-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50bf9-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50bf9-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50bf9-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="50bf9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="50bf9-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="50bf9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50bf9-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="50bf9-115">Attributes</span></span>  
  
|<span data-ttu-id="50bf9-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="50bf9-116">Attribute</span></span>|<span data-ttu-id="50bf9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="50bf9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50bf9-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="50bf9-118">activityName</span></span>|<span data-ttu-id="50bf9-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="50bf9-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="50bf9-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="50bf9-120">childActivityName</span></span>|<span data-ttu-id="50bf9-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="50bf9-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50bf9-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="50bf9-122">Child Elements</span></span>  
 <span data-ttu-id="50bf9-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="50bf9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50bf9-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="50bf9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="50bf9-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="50bf9-125">Element</span></span>|<span data-ttu-id="50bf9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="50bf9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50bf9-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="50bf9-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="50bf9-128">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="50bf9-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50bf9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50bf9-129">See Also</span></span>  
 <span data-ttu-id="50bf9-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="50bf9-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="50bf9-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="50bf9-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="50bf9-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="50bf9-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="50bf9-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="50bf9-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
