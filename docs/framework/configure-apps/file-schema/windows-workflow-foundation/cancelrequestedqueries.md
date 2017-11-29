---
title: '&lt;cancelRequestedQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b3699985095fca59d5817a31c52b29fe7609a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="7b7ca-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7b7ca-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="7b7ca-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7b7ca-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7b7ca-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="7b7ca-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="7b7ca-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7b7ca-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7b7ca-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7b7ca-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-107">\<tracking></span></span>  
<span data-ttu-id="7b7ca-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-108">\<trackingProfile></span></span>  
<span data-ttu-id="7b7ca-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-109">\<workflow></span></span>  
<span data-ttu-id="7b7ca-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7ca-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b7ca-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b7ca-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7b7ca-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7b7ca-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7b7ca-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b7ca-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b7ca-114">Attributes</span></span>  
 <span data-ttu-id="7b7ca-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7b7ca-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b7ca-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b7ca-116">Child Elements</span></span>  
  
|<span data-ttu-id="7b7ca-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b7ca-117">Element</span></span>|<span data-ttu-id="7b7ca-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b7ca-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b7ca-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="7b7ca-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="7b7ca-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b7ca-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7b7ca-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7b7ca-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b7ca-122">Element</span></span>|<span data-ttu-id="7b7ca-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b7ca-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b7ca-124">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="7b7ca-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7b7ca-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b7ca-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b7ca-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b7ca-126">See Also</span></span>  
 [<span data-ttu-id="7b7ca-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7b7ca-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7b7ca-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7b7ca-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
