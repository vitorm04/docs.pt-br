---
title: '&lt;faultPropagationQueries&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e122e8c6194545a02f6db429d550eabed5d49b27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="36eb9-102">&lt;faultPropagationQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="36eb9-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="36eb9-103">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="36eb9-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="36eb9-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="36eb9-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="36eb9-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="36eb9-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="36eb9-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="36eb9-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="36eb9-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="36eb9-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="36eb9-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="36eb9-108">\<system.serviceModel></span></span>  
<span data-ttu-id="36eb9-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="36eb9-109">\<tracking></span></span>  
<span data-ttu-id="36eb9-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="36eb9-110">\<trackingProfile></span></span>  
<span data-ttu-id="36eb9-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="36eb9-111">\<workflow></span></span>  
<span data-ttu-id="36eb9-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="36eb9-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36eb9-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36eb9-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36eb9-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="36eb9-114">Attributes and Elements</span></span>  
 <span data-ttu-id="36eb9-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="36eb9-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36eb9-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="36eb9-116">Attributes</span></span>  
 <span data-ttu-id="36eb9-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="36eb9-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36eb9-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="36eb9-118">Child Elements</span></span>  
  
|<span data-ttu-id="36eb9-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="36eb9-119">Element</span></span>|<span data-ttu-id="36eb9-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="36eb9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36eb9-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="36eb9-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="36eb9-122">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="36eb9-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="36eb9-123">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="36eb9-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36eb9-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="36eb9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="36eb9-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="36eb9-125">Element</span></span>|<span data-ttu-id="36eb9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="36eb9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36eb9-127">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="36eb9-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="36eb9-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="36eb9-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36eb9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36eb9-129">See Also</span></span>  
 <span data-ttu-id="36eb9-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="36eb9-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="36eb9-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="36eb9-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="36eb9-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="36eb9-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="36eb9-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="36eb9-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
