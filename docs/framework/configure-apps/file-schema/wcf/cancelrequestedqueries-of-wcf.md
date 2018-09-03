---
title: '&lt;cancelRequestedQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: c9266d9ce1f6a61c4468fd95467e76730b966249
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480620"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="30a63-102">&lt;cancelRequestedQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="30a63-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="30a63-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="30a63-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="30a63-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="30a63-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="30a63-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="30a63-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="30a63-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30a63-106">\<system.serviceModel></span></span>  
<span data-ttu-id="30a63-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="30a63-107">\<tracking></span></span>  
<span data-ttu-id="30a63-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="30a63-108">\<trackingProfile></span></span>  
<span data-ttu-id="30a63-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="30a63-109">\<workflow></span></span>  
<span data-ttu-id="30a63-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="30a63-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a63-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30a63-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30a63-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30a63-112">Attributes and Elements</span></span>  
 <span data-ttu-id="30a63-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30a63-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30a63-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="30a63-114">Attributes</span></span>  
 <span data-ttu-id="30a63-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="30a63-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="30a63-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30a63-116">Child Elements</span></span>  
  
|<span data-ttu-id="30a63-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="30a63-117">Element</span></span>|<span data-ttu-id="30a63-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="30a63-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30a63-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="30a63-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="30a63-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="30a63-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30a63-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30a63-121">Parent Elements</span></span>  
  
|<span data-ttu-id="30a63-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="30a63-122">Element</span></span>|<span data-ttu-id="30a63-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="30a63-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30a63-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="30a63-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="30a63-125">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> propriedade.</span><span class="sxs-lookup"><span data-stu-id="30a63-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30a63-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30a63-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="30a63-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="30a63-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="30a63-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="30a63-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
