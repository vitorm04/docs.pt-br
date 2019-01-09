---
title: '&lt;customTrackingQueries&gt; de WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: f75c6bf50d30da5a136137c858a5cd96ce0783ff
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150078"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="6002a-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="6002a-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="6002a-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="6002a-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6002a-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6002a-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="6002a-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6002a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="6002a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6002a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6002a-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="6002a-107">\<tracking></span></span>  
<span data-ttu-id="6002a-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="6002a-108">\<profiles></span></span>  
<span data-ttu-id="6002a-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6002a-109">\<trackingProfile></span></span>  
<span data-ttu-id="6002a-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6002a-110">\<workflow></span></span>  
<span data-ttu-id="6002a-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="6002a-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6002a-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6002a-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6002a-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6002a-113">Attributes and elements</span></span>

<span data-ttu-id="6002a-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6002a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6002a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="6002a-115">Attributes</span></span>

<span data-ttu-id="6002a-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6002a-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6002a-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6002a-117">Child elements</span></span>
  
|<span data-ttu-id="6002a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="6002a-118">Element</span></span>|<span data-ttu-id="6002a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="6002a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6002a-120">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="6002a-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="6002a-121">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="6002a-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6002a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6002a-122">Parent elements</span></span>  
  
|<span data-ttu-id="6002a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="6002a-123">Element</span></span>|<span data-ttu-id="6002a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="6002a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6002a-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6002a-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6002a-126">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6002a-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6002a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6002a-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="6002a-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6002a-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="6002a-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6002a-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
