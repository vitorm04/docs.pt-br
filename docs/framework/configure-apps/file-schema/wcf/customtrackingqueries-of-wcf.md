---
title: <customTrackingQueries> do WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 8b317cc289853902592e145e34b6e7bf5f84763b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704161"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="d7b42-102">\<customTrackingQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="d7b42-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="d7b42-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="d7b42-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d7b42-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d7b42-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d7b42-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d7b42-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="d7b42-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d7b42-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d7b42-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d7b42-107">\<tracking></span></span>  
<span data-ttu-id="d7b42-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="d7b42-108">\<profiles></span></span>  
<span data-ttu-id="d7b42-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d7b42-109">\<trackingProfile></span></span>  
<span data-ttu-id="d7b42-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d7b42-110">\<workflow></span></span>  
<span data-ttu-id="d7b42-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d7b42-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b42-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7b42-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b42-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7b42-113">Attributes and elements</span></span>

<span data-ttu-id="d7b42-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7b42-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b42-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7b42-115">Attributes</span></span>

<span data-ttu-id="d7b42-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d7b42-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="d7b42-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7b42-117">Child elements</span></span>
  
|<span data-ttu-id="d7b42-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7b42-118">Element</span></span>|<span data-ttu-id="d7b42-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7b42-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7b42-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d7b42-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="d7b42-121">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="d7b42-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b42-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7b42-122">Parent elements</span></span>  
  
|<span data-ttu-id="d7b42-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7b42-123">Element</span></span>|<span data-ttu-id="d7b42-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7b42-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7b42-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d7b42-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d7b42-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7b42-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7b42-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b42-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d7b42-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d7b42-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d7b42-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d7b42-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
