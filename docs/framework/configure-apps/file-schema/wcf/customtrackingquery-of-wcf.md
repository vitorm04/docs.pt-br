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
ms.workload: dotnet
ms.openlocfilehash: 27637abceb23a54e784afbcc2e0517db51542b53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="f4414-102">&lt;customTrackingQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="f4414-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="f4414-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="f4414-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f4414-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f4414-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="f4414-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f4414-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="f4414-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f4414-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f4414-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="f4414-107">\<tracking></span></span>  
<span data-ttu-id="f4414-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f4414-108">\<trackingProfile></span></span>  
<span data-ttu-id="f4414-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="f4414-109">\<workflow></span></span>  
<span data-ttu-id="f4414-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="f4414-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="f4414-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="f4414-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4414-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4414-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4414-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f4414-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f4414-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f4414-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4414-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4414-115">Attributes</span></span>  
  
|<span data-ttu-id="f4414-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="f4414-116">Attribute</span></span>|<span data-ttu-id="f4414-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4414-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4414-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="f4414-118">activityName</span></span>|<span data-ttu-id="f4414-119">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f4414-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="f4414-120">name</span><span class="sxs-lookup"><span data-stu-id="f4414-120">name</span></span>|<span data-ttu-id="f4414-121">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="f4414-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4414-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f4414-122">Child Elements</span></span>  
 <span data-ttu-id="f4414-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f4414-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4414-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f4414-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f4414-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4414-125">Element</span></span>|<span data-ttu-id="f4414-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4414-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4414-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="f4414-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="f4414-128">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="f4414-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4414-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4414-129">See Also</span></span>  
 <span data-ttu-id="f4414-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f4414-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="f4414-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f4414-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f4414-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f4414-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f4414-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f4414-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
