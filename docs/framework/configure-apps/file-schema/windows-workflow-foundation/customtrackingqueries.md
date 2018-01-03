---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84c9635b37c592b4d82635deb58880d81d2fb5cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="062d1-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="062d1-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="062d1-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="062d1-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="062d1-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="062d1-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="062d1-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="062d1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="062d1-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="062d1-106">\<system.serviceModel></span></span>  
<span data-ttu-id="062d1-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="062d1-107">\<tracking></span></span>  
<span data-ttu-id="062d1-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="062d1-108">\<trackingProfile></span></span>  
<span data-ttu-id="062d1-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="062d1-109">\<workflow></span></span>  
<span data-ttu-id="062d1-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="062d1-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="062d1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="062d1-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="062d1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="062d1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="062d1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="062d1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="062d1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="062d1-114">Attributes</span></span>  
 <span data-ttu-id="062d1-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="062d1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="062d1-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="062d1-116">Child Elements</span></span>  
  
|<span data-ttu-id="062d1-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="062d1-117">Element</span></span>|<span data-ttu-id="062d1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="062d1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="062d1-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="062d1-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="062d1-120">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="062d1-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="062d1-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="062d1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="062d1-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="062d1-122">Element</span></span>|<span data-ttu-id="062d1-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="062d1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="062d1-124">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="062d1-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="062d1-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="062d1-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="062d1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="062d1-126">See Also</span></span>  
 <span data-ttu-id="062d1-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="062d1-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="062d1-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="062d1-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="062d1-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="062d1-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="062d1-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="062d1-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
