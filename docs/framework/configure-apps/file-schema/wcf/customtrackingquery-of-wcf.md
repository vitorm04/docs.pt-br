---
title: '&lt;customTrackingQuery&gt; of WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 350ebbd0cc7be66f27ed2f70e1369e249267f359
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="3a734-102">&lt;customTrackingQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="3a734-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="3a734-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="3a734-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="3a734-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3a734-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="3a734-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3a734-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="3a734-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3a734-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3a734-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="3a734-107">\<tracking></span></span>  
<span data-ttu-id="3a734-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="3a734-108">\<trackingProfile></span></span>  
<span data-ttu-id="3a734-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="3a734-109">\<workflow></span></span>  
<span data-ttu-id="3a734-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="3a734-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="3a734-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="3a734-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a734-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a734-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a734-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a734-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3a734-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a734-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a734-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a734-115">Attributes</span></span>  
  
|<span data-ttu-id="3a734-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a734-116">Attribute</span></span>|<span data-ttu-id="3a734-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a734-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a734-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="3a734-118">activityName</span></span>|<span data-ttu-id="3a734-119">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3a734-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="3a734-120">name</span><span class="sxs-lookup"><span data-stu-id="3a734-120">name</span></span>|<span data-ttu-id="3a734-121">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="3a734-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a734-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a734-122">Child Elements</span></span>  
 <span data-ttu-id="3a734-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3a734-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a734-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a734-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3a734-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a734-125">Element</span></span>|<span data-ttu-id="3a734-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a734-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a734-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="3a734-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="3a734-128">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="3a734-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a734-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a734-129">See Also</span></span>  
 <span data-ttu-id="3a734-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3a734-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="3a734-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3a734-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="3a734-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3a734-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="3a734-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3a734-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
