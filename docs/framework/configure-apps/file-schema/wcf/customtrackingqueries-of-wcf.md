---
title: '&lt;customTrackingQueries&gt; de WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: f4f6186aa51ef1656f31fb0035f58a07e5c2447b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700787"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="0d8a8-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="0d8a8-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="0d8a8-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="0d8a8-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0d8a8-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0d8a8-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="0d8a8-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0d8a8-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="0d8a8-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0d8a8-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0d8a8-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="0d8a8-107">\<tracking></span></span>  
<span data-ttu-id="0d8a8-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="0d8a8-108">\<profiles></span></span>  
<span data-ttu-id="0d8a8-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0d8a8-109">\<trackingProfile></span></span>  
<span data-ttu-id="0d8a8-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0d8a8-110">\<workflow></span></span>  
<span data-ttu-id="0d8a8-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="0d8a8-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8a8-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d8a8-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d8a8-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d8a8-113">Attributes and elements</span></span>

<span data-ttu-id="0d8a8-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d8a8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d8a8-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d8a8-115">Attributes</span></span>

<span data-ttu-id="0d8a8-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d8a8-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="0d8a8-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d8a8-117">Child elements</span></span>
  
|<span data-ttu-id="0d8a8-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d8a8-118">Element</span></span>|<span data-ttu-id="0d8a8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d8a8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d8a8-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="0d8a8-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="0d8a8-121">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="0d8a8-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d8a8-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d8a8-122">Parent elements</span></span>  
  
|<span data-ttu-id="0d8a8-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d8a8-123">Element</span></span>|<span data-ttu-id="0d8a8-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d8a8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d8a8-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0d8a8-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="0d8a8-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d8a8-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d8a8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d8a8-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0d8a8-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0d8a8-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0d8a8-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0d8a8-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
