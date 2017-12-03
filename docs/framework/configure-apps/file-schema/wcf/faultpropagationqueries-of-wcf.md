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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 771908114f4f4e1cc2588e39e7f3d811c336a05a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="686da-102">&lt;faultPropagationQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="686da-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="686da-103">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="686da-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="686da-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="686da-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="686da-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="686da-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="686da-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="686da-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="686da-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="686da-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="686da-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="686da-108">\<system.serviceModel></span></span>  
<span data-ttu-id="686da-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="686da-109">\<tracking></span></span>  
<span data-ttu-id="686da-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="686da-110">\<trackingProfile></span></span>  
<span data-ttu-id="686da-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="686da-111">\<workflow></span></span>  
<span data-ttu-id="686da-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="686da-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686da-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="686da-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="686da-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="686da-114">Attributes and Elements</span></span>  
 <span data-ttu-id="686da-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="686da-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="686da-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="686da-116">Attributes</span></span>  
 <span data-ttu-id="686da-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="686da-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="686da-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="686da-118">Child Elements</span></span>  
  
|<span data-ttu-id="686da-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="686da-119">Element</span></span>|<span data-ttu-id="686da-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="686da-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="686da-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="686da-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="686da-122">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="686da-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="686da-123">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="686da-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="686da-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="686da-124">Parent Elements</span></span>  
  
|<span data-ttu-id="686da-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="686da-125">Element</span></span>|<span data-ttu-id="686da-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="686da-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="686da-127">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="686da-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="686da-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="686da-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="686da-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="686da-129">See Also</span></span>  
 <span data-ttu-id="686da-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="686da-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="686da-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="686da-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="686da-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="686da-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="686da-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="686da-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
