---
title: '&lt;customTrackingQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a7a69b481da7315c8d26b00c171d030f77d9b63
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="0a01e-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="0a01e-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="0a01e-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="0a01e-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0a01e-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a01e-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="0a01e-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0a01e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="0a01e-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0a01e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0a01e-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="0a01e-107">\<tracking></span></span>  
<span data-ttu-id="0a01e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="0a01e-108">\<trackingProfile></span></span>  
<span data-ttu-id="0a01e-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="0a01e-109">\<workflow></span></span>  
<span data-ttu-id="0a01e-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="0a01e-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a01e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a01e-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a01e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a01e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0a01e-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0a01e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a01e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a01e-114">Attributes</span></span>  
 <span data-ttu-id="0a01e-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0a01e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0a01e-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a01e-116">Child Elements</span></span>  
  
|<span data-ttu-id="0a01e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a01e-117">Element</span></span>|<span data-ttu-id="0a01e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a01e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a01e-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="0a01e-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="0a01e-120">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="0a01e-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a01e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a01e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0a01e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a01e-122">Element</span></span>|<span data-ttu-id="0a01e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a01e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a01e-124">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="0a01e-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="0a01e-125">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0a01e-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a01e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a01e-126">See Also</span></span>  
 <span data-ttu-id="0a01e-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0a01e-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="0a01e-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0a01e-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="0a01e-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0a01e-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="0a01e-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0a01e-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
