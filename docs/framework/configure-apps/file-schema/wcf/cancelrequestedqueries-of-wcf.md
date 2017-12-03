---
title: '&lt;cancelRequestedQueries&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be3c02bdf0d51006d7df3b382541b704f71f2463
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="05657-102">&lt;cancelRequestedQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="05657-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="05657-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="05657-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="05657-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="05657-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="05657-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="05657-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="05657-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="05657-106">\<system.serviceModel></span></span>  
<span data-ttu-id="05657-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="05657-107">\<tracking></span></span>  
<span data-ttu-id="05657-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="05657-108">\<trackingProfile></span></span>  
<span data-ttu-id="05657-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="05657-109">\<workflow></span></span>  
<span data-ttu-id="05657-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="05657-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05657-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05657-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05657-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="05657-112">Attributes and Elements</span></span>  
 <span data-ttu-id="05657-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="05657-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05657-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="05657-114">Attributes</span></span>  
 <span data-ttu-id="05657-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="05657-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05657-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="05657-116">Child Elements</span></span>  
  
|<span data-ttu-id="05657-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="05657-117">Element</span></span>|<span data-ttu-id="05657-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="05657-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05657-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="05657-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="05657-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="05657-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05657-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="05657-121">Parent Elements</span></span>  
  
|<span data-ttu-id="05657-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="05657-122">Element</span></span>|<span data-ttu-id="05657-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="05657-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05657-124">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="05657-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="05657-125">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="05657-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05657-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05657-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="05657-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="05657-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="05657-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="05657-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
