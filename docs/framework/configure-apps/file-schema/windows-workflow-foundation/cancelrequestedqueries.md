---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 989d6e99457108336c38fb1eece4c9ac2444c974
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271493"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="e19f7-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="e19f7-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="e19f7-102">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e19f7-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e19f7-103">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="e19f7-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="e19f7-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e19f7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e19f7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e19f7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e19f7-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="e19f7-106">\<tracking></span></span>  
<span data-ttu-id="e19f7-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e19f7-107">\<trackingProfile></span></span>  
<span data-ttu-id="e19f7-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e19f7-108">\<workflow></span></span>  
<span data-ttu-id="e19f7-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="e19f7-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e19f7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e19f7-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e19f7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e19f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e19f7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e19f7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e19f7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e19f7-113">Attributes</span></span>  
 <span data-ttu-id="e19f7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e19f7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e19f7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e19f7-115">Child Elements</span></span>  
  
|<span data-ttu-id="e19f7-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="e19f7-116">Element</span></span>|<span data-ttu-id="e19f7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="e19f7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e19f7-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="e19f7-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="e19f7-119">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="e19f7-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e19f7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e19f7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e19f7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e19f7-121">Element</span></span>|<span data-ttu-id="e19f7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e19f7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e19f7-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e19f7-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e19f7-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="e19f7-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e19f7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e19f7-125">See also</span></span>
- [<span data-ttu-id="e19f7-126">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e19f7-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e19f7-127">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e19f7-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
