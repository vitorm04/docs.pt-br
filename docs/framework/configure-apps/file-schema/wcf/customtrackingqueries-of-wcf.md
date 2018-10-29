---
title: '&lt;customTrackingQueries&gt; de WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 060e2b5c8efd51f6245a39bd9562a69f0111fd41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202218"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="8890c-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="8890c-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="8890c-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="8890c-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="8890c-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8890c-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="8890c-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8890c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="8890c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8890c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8890c-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="8890c-107">\<tracking></span></span>  
<span data-ttu-id="8890c-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="8890c-108">\<profiles></span></span>  
<span data-ttu-id="8890c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8890c-109">\<trackingProfile></span></span>  
<span data-ttu-id="8890c-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="8890c-110">\<workflow></span></span>  
<span data-ttu-id="8890c-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8890c-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8890c-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8890c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8890c-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8890c-113">Attributes and elements</span></span>

<span data-ttu-id="8890c-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8890c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8890c-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="8890c-115">Attributes</span></span>

<span data-ttu-id="8890c-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8890c-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="8890c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8890c-117">Child elements</span></span>
  
|<span data-ttu-id="8890c-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="8890c-118">Element</span></span>|<span data-ttu-id="8890c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8890c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8890c-120">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8890c-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="8890c-121">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="8890c-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8890c-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8890c-122">Parent elements</span></span>  
  
|<span data-ttu-id="8890c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="8890c-123">Element</span></span>|<span data-ttu-id="8890c-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="8890c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8890c-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="8890c-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8890c-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="8890c-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8890c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8890c-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="8890c-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8890c-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="8890c-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8890c-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
