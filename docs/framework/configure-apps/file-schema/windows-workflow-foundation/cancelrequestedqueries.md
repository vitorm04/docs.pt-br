---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163157"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="73fbc-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="73fbc-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="73fbc-102">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="73fbc-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="73fbc-103">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="73fbc-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="73fbc-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="73fbc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="73fbc-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="73fbc-105">\<system.serviceModel></span></span>  
<span data-ttu-id="73fbc-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="73fbc-106">\<tracking></span></span>  
<span data-ttu-id="73fbc-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="73fbc-107">\<trackingProfile></span></span>  
<span data-ttu-id="73fbc-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="73fbc-108">\<workflow></span></span>  
<span data-ttu-id="73fbc-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="73fbc-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fbc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73fbc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73fbc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73fbc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73fbc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="73fbc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73fbc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="73fbc-113">Attributes</span></span>  
 <span data-ttu-id="73fbc-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="73fbc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73fbc-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73fbc-115">Child Elements</span></span>  
  
|<span data-ttu-id="73fbc-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="73fbc-116">Element</span></span>|<span data-ttu-id="73fbc-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="73fbc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73fbc-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="73fbc-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="73fbc-119">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="73fbc-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73fbc-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="73fbc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="73fbc-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="73fbc-121">Element</span></span>|<span data-ttu-id="73fbc-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="73fbc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73fbc-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="73fbc-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="73fbc-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="73fbc-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73fbc-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73fbc-125">See also</span></span>

- [<span data-ttu-id="73fbc-126">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="73fbc-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="73fbc-127">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="73fbc-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
