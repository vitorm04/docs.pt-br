---
title: '&lt;cancelRequestedQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 9cf2761bdab36d95b5077e36174565659230b512
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145439"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="6b0b9-102">&lt;cancelRequestedQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="6b0b9-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="6b0b9-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6b0b9-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6b0b9-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="6b0b9-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="6b0b9-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6b0b9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6b0b9-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6b0b9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6b0b9-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="6b0b9-107">\<tracking></span></span>  
<span data-ttu-id="6b0b9-108">\<perfis > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6b0b9-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="6b0b9-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6b0b9-109">\<workflow></span></span>  
<span data-ttu-id="6b0b9-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="6b0b9-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0b9-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b0b9-111">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b0b9-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6b0b9-112">Attributes and elements</span></span>  

<span data-ttu-id="6b0b9-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6b0b9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b0b9-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6b0b9-114">Attributes</span></span>

<span data-ttu-id="6b0b9-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6b0b9-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6b0b9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6b0b9-116">Child elements</span></span>
  
|<span data-ttu-id="6b0b9-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b0b9-117">Element</span></span>|<span data-ttu-id="6b0b9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b0b9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b0b9-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6b0b9-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="6b0b9-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="6b0b9-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b0b9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6b0b9-121">Parent elements</span></span>  
  
|<span data-ttu-id="6b0b9-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b0b9-122">Element</span></span>|<span data-ttu-id="6b0b9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b0b9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b0b9-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6b0b9-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6b0b9-125">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6b0b9-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b0b9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b0b9-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="6b0b9-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6b0b9-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6b0b9-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6b0b9-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
