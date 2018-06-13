---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: aa1e7ff4d53cbd40b168c3cc800a23dbcddc28f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755884"
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="1d164-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="1d164-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="1d164-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="1d164-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="1d164-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1d164-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="1d164-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1d164-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1d164-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d164-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1d164-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="1d164-107">\<tracking></span></span>  
<span data-ttu-id="1d164-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1d164-108">\<trackingProfile></span></span>  
<span data-ttu-id="1d164-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="1d164-109">\<workflow></span></span>  
<span data-ttu-id="1d164-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="1d164-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d164-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d164-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d164-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d164-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1d164-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d164-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d164-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d164-114">Attributes</span></span>  
 <span data-ttu-id="1d164-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1d164-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d164-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d164-116">Child Elements</span></span>  
  
|<span data-ttu-id="1d164-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d164-117">Element</span></span>|<span data-ttu-id="1d164-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d164-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d164-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="1d164-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="1d164-120">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="1d164-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d164-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d164-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1d164-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d164-122">Element</span></span>|<span data-ttu-id="1d164-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d164-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d164-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="1d164-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1d164-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="1d164-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d164-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d164-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="1d164-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1d164-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1d164-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="1d164-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
