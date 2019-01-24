---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 757bbe500ec3edccef465b7ff23b2c974e4a5011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598835"
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="21140-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="21140-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="21140-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="21140-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="21140-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="21140-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="21140-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="21140-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="21140-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="21140-106">\<system.serviceModel></span></span>  
<span data-ttu-id="21140-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="21140-107">\<tracking></span></span>  
<span data-ttu-id="21140-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="21140-108">\<trackingProfile></span></span>  
<span data-ttu-id="21140-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="21140-109">\<workflow></span></span>  
<span data-ttu-id="21140-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="21140-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21140-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21140-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21140-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="21140-112">Attributes and Elements</span></span>  
 <span data-ttu-id="21140-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="21140-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21140-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="21140-114">Attributes</span></span>  
 <span data-ttu-id="21140-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="21140-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21140-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="21140-116">Child Elements</span></span>  
  
|<span data-ttu-id="21140-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="21140-117">Element</span></span>|<span data-ttu-id="21140-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="21140-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21140-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="21140-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="21140-120">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="21140-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21140-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="21140-121">Parent Elements</span></span>  
  
|<span data-ttu-id="21140-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="21140-122">Element</span></span>|<span data-ttu-id="21140-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="21140-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21140-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="21140-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="21140-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="21140-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21140-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21140-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="21140-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="21140-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="21140-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="21140-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
