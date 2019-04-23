---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 402b938913575adfa9125b981dc2913680f07b73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204036"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="751a2-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="751a2-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="751a2-102">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="751a2-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="751a2-103">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="751a2-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="751a2-104">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="751a2-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="751a2-105">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="751a2-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="751a2-106">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="751a2-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="751a2-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="751a2-107">\<system.serviceModel></span></span>  
<span data-ttu-id="751a2-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="751a2-108">\<tracking></span></span>  
<span data-ttu-id="751a2-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="751a2-109">\<trackingProfile></span></span>  
<span data-ttu-id="751a2-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="751a2-110">\<workflow></span></span>  
<span data-ttu-id="751a2-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="751a2-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="751a2-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="751a2-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="751a2-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="751a2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="751a2-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="751a2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="751a2-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="751a2-115">Attributes</span></span>  
 <span data-ttu-id="751a2-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="751a2-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="751a2-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="751a2-117">Child Elements</span></span>  
  
|<span data-ttu-id="751a2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="751a2-118">Element</span></span>|<span data-ttu-id="751a2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="751a2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="751a2-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="751a2-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="751a2-121">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="751a2-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="751a2-122">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="751a2-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="751a2-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="751a2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="751a2-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="751a2-124">Element</span></span>|<span data-ttu-id="751a2-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="751a2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="751a2-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="751a2-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="751a2-127">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="751a2-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="751a2-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="751a2-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="751a2-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="751a2-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="751a2-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="751a2-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
