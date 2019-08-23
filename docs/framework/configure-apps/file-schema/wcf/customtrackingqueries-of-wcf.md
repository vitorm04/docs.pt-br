---
title: <customTrackingQueries>do WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: abc0c7dfb426338ec6bca61b0a4b87754bb63588
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925934"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="392f1-102">\<customTrackingQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="392f1-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="392f1-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="392f1-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="392f1-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="392f1-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="392f1-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="392f1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="392f1-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="392f1-106">\<system.serviceModel></span></span>  
<span data-ttu-id="392f1-107">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="392f1-107">\<tracking></span></span>  
<span data-ttu-id="392f1-108">\<perfis ></span><span class="sxs-lookup"><span data-stu-id="392f1-108">\<profiles></span></span>  
<span data-ttu-id="392f1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="392f1-109">\<trackingProfile></span></span>  
<span data-ttu-id="392f1-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="392f1-110">\<workflow></span></span>  
<span data-ttu-id="392f1-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="392f1-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="392f1-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="392f1-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="392f1-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="392f1-113">Attributes and elements</span></span>

<span data-ttu-id="392f1-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="392f1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="392f1-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="392f1-115">Attributes</span></span>

<span data-ttu-id="392f1-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="392f1-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="392f1-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="392f1-117">Child elements</span></span>
  
|<span data-ttu-id="392f1-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="392f1-118">Element</span></span>|<span data-ttu-id="392f1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="392f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="392f1-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="392f1-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="392f1-121">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="392f1-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="392f1-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="392f1-122">Parent elements</span></span>  
  
|<span data-ttu-id="392f1-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="392f1-123">Element</span></span>|<span data-ttu-id="392f1-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="392f1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="392f1-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="392f1-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="392f1-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="392f1-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="392f1-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="392f1-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="392f1-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="392f1-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="392f1-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="392f1-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
