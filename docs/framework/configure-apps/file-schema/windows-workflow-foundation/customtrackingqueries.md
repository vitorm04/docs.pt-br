---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120075"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="712a7-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="712a7-101">\<customTrackingQueries></span></span>
<span data-ttu-id="712a7-102">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="712a7-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="712a7-103">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="712a7-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="712a7-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="712a7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="712a7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="712a7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="712a7-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="712a7-106">\<tracking></span></span>  
<span data-ttu-id="712a7-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="712a7-107">\<trackingProfile></span></span>  
<span data-ttu-id="712a7-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="712a7-108">\<workflow></span></span>  
<span data-ttu-id="712a7-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="712a7-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712a7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="712a7-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="712a7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="712a7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="712a7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="712a7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="712a7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="712a7-113">Attributes</span></span>  
 <span data-ttu-id="712a7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="712a7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="712a7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="712a7-115">Child Elements</span></span>  
  
|<span data-ttu-id="712a7-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="712a7-116">Element</span></span>|<span data-ttu-id="712a7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="712a7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="712a7-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="712a7-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="712a7-119">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="712a7-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="712a7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="712a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="712a7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="712a7-121">Element</span></span>|<span data-ttu-id="712a7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="712a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="712a7-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="712a7-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="712a7-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="712a7-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="712a7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="712a7-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="712a7-126">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="712a7-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="712a7-127">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="712a7-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
