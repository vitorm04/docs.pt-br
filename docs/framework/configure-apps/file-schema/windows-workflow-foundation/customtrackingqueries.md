---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 429940b2ed69d8be497626f634a21adca540b529
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945848"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="971e9-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="971e9-101">\<customTrackingQueries></span></span>
<span data-ttu-id="971e9-102">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="971e9-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="971e9-103">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="971e9-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="971e9-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="971e9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="971e9-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="971e9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="971e9-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="971e9-106">\<tracking></span></span>  
<span data-ttu-id="971e9-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="971e9-107">\<trackingProfile></span></span>  
<span data-ttu-id="971e9-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="971e9-108">\<workflow></span></span>  
<span data-ttu-id="971e9-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="971e9-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="971e9-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="971e9-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="971e9-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="971e9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="971e9-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="971e9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="971e9-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="971e9-113">Attributes</span></span>  
 <span data-ttu-id="971e9-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="971e9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="971e9-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="971e9-115">Child Elements</span></span>  
  
|<span data-ttu-id="971e9-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="971e9-116">Element</span></span>|<span data-ttu-id="971e9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="971e9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="971e9-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="971e9-118">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="971e9-119">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="971e9-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="971e9-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="971e9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="971e9-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="971e9-121">Element</span></span>|<span data-ttu-id="971e9-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="971e9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="971e9-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="971e9-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="971e9-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="971e9-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="971e9-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="971e9-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="971e9-126">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="971e9-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="971e9-127">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="971e9-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
