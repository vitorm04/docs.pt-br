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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 457cc3aaa921016e553eb40bcee72af5de3c7179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="7467f-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7467f-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="7467f-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7467f-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7467f-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="7467f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="7467f-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7467f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7467f-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7467f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7467f-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="7467f-107">\<tracking></span></span>  
<span data-ttu-id="7467f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7467f-108">\<trackingProfile></span></span>  
<span data-ttu-id="7467f-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="7467f-109">\<workflow></span></span>  
<span data-ttu-id="7467f-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="7467f-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7467f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7467f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7467f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7467f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7467f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7467f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7467f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7467f-114">Attributes</span></span>  
 <span data-ttu-id="7467f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7467f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7467f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7467f-116">Child Elements</span></span>  
  
|<span data-ttu-id="7467f-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="7467f-117">Element</span></span>|<span data-ttu-id="7467f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7467f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7467f-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="7467f-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="7467f-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="7467f-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7467f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7467f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7467f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="7467f-122">Element</span></span>|<span data-ttu-id="7467f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7467f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7467f-124">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="7467f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7467f-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="7467f-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7467f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7467f-126">See Also</span></span>  
 [<span data-ttu-id="7467f-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7467f-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7467f-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7467f-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
