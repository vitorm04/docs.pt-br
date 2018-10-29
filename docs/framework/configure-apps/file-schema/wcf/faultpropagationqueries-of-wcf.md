---
title: '&lt;faultPropagationQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 1db99a8d80fad5c0eca93777d87047b43371d048
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202114"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="3be28-102">&lt;faultPropagationQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="3be28-102">&lt;faultPropagationQueries&gt; of WCF</span></span>

<span data-ttu-id="3be28-103">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="3be28-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3be28-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="3be28-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="3be28-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="3be28-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="3be28-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="3be28-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="3be28-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3be28-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3be28-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3be28-108">\<system.serviceModel></span></span>  
<span data-ttu-id="3be28-109">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="3be28-109">\<tracking></span></span>  
<span data-ttu-id="3be28-110">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="3be28-110">\<profiles></span></span>  
<span data-ttu-id="3be28-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3be28-111">\<trackingProfile></span></span>  
<span data-ttu-id="3be28-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3be28-112">\<workflow></span></span>  
<span data-ttu-id="3be28-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="3be28-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be28-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3be28-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="3be28-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3be28-115">Attributes and elements</span></span>

<span data-ttu-id="3be28-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3be28-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="3be28-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="3be28-117">Attributes</span></span>

<span data-ttu-id="3be28-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3be28-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="3be28-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3be28-119">Child elements</span></span>

|<span data-ttu-id="3be28-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3be28-120">Element</span></span>|<span data-ttu-id="3be28-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3be28-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3be28-122">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="3be28-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="3be28-123">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="3be28-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3be28-124">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="3be28-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3be28-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3be28-125">Parent elements</span></span>  
  
|<span data-ttu-id="3be28-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="3be28-126">Element</span></span>|<span data-ttu-id="3be28-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="3be28-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3be28-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3be28-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="3be28-129">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="3be28-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3be28-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3be28-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3be28-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3be28-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3be28-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3be28-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
