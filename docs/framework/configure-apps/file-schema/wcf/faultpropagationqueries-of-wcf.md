---
title: '&lt;faultPropagationQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 77a38f8474b5e2ac8634d6ea91bc80c6044ff3ed
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144958"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="85f3f-102">&lt;faultPropagationQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="85f3f-102">&lt;faultPropagationQueries&gt; of WCF</span></span>

<span data-ttu-id="85f3f-103">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="85f3f-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="85f3f-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="85f3f-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="85f3f-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="85f3f-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="85f3f-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="85f3f-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="85f3f-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="85f3f-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="85f3f-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="85f3f-108">\<system.serviceModel></span></span>  
<span data-ttu-id="85f3f-109">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="85f3f-109">\<tracking></span></span>  
<span data-ttu-id="85f3f-110">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="85f3f-110">\<profiles></span></span>  
<span data-ttu-id="85f3f-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="85f3f-111">\<trackingProfile></span></span>  
<span data-ttu-id="85f3f-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="85f3f-112">\<workflow></span></span>  
<span data-ttu-id="85f3f-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="85f3f-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f3f-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85f3f-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85f3f-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="85f3f-115">Attributes and elements</span></span>

<span data-ttu-id="85f3f-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="85f3f-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="85f3f-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="85f3f-117">Attributes</span></span>

<span data-ttu-id="85f3f-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="85f3f-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="85f3f-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="85f3f-119">Child elements</span></span>

|<span data-ttu-id="85f3f-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="85f3f-120">Element</span></span>|<span data-ttu-id="85f3f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="85f3f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85f3f-122">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="85f3f-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="85f3f-123">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="85f3f-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="85f3f-124">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="85f3f-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85f3f-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="85f3f-125">Parent elements</span></span>  
  
|<span data-ttu-id="85f3f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="85f3f-126">Element</span></span>|<span data-ttu-id="85f3f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="85f3f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85f3f-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="85f3f-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="85f3f-129">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="85f3f-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85f3f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85f3f-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="85f3f-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="85f3f-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="85f3f-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="85f3f-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
