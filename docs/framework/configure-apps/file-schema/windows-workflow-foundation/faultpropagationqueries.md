---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 5fd6ffc9560247089c7fbb60b0e5a7d3a417ea6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="75da7-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="75da7-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="75da7-103">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="75da7-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="75da7-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="75da7-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="75da7-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="75da7-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="75da7-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="75da7-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="75da7-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="75da7-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="75da7-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="75da7-108">\<system.serviceModel></span></span>  
<span data-ttu-id="75da7-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="75da7-109">\<tracking></span></span>  
<span data-ttu-id="75da7-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="75da7-110">\<trackingProfile></span></span>  
<span data-ttu-id="75da7-111">\<workflow></span><span class="sxs-lookup"><span data-stu-id="75da7-111">\<workflow></span></span>  
<span data-ttu-id="75da7-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="75da7-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75da7-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75da7-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75da7-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="75da7-114">Attributes and Elements</span></span>  
 <span data-ttu-id="75da7-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="75da7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75da7-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="75da7-116">Attributes</span></span>  
 <span data-ttu-id="75da7-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="75da7-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="75da7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="75da7-118">Child Elements</span></span>  
  
|<span data-ttu-id="75da7-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="75da7-119">Element</span></span>|<span data-ttu-id="75da7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="75da7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75da7-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="75da7-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="75da7-122">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="75da7-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="75da7-123">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="75da7-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75da7-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="75da7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="75da7-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="75da7-125">Element</span></span>|<span data-ttu-id="75da7-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="75da7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75da7-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="75da7-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="75da7-128">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="75da7-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75da7-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75da7-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="75da7-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="75da7-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="75da7-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="75da7-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
