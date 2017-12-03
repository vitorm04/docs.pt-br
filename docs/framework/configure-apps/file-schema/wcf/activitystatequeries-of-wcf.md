---
title: '&lt;activityStateQueries&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ec6cb2d077f95f53a2ee0daf8e2819ae91cb13b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="ee7ab-102">&lt;activityStateQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="ee7ab-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="ee7ab-103">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ee7ab-104">Por exemplo, convém manter o controle de toda vez que a atividade "Enviar email" é concluído em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ee7ab-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ee7ab-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="ee7ab-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ee7ab-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="ee7ab-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-108">\<system.serviceModel></span></span>  
<span data-ttu-id="ee7ab-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-109">\<tracking></span></span>  
<span data-ttu-id="ee7ab-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-110">\<trackingProfile></span></span>  
<span data-ttu-id="ee7ab-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-111">\<workflow></span></span>  
<span data-ttu-id="ee7ab-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee7ab-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee7ab-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee7ab-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ee7ab-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ee7ab-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee7ab-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="ee7ab-116">Attributes</span></span>  
 <span data-ttu-id="ee7ab-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee7ab-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ee7ab-118">Child Elements</span></span>  
  
|<span data-ttu-id="ee7ab-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee7ab-119">Element</span></span>|<span data-ttu-id="ee7ab-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee7ab-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee7ab-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="ee7ab-122">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ee7ab-123">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee7ab-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ee7ab-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ee7ab-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee7ab-125">Element</span></span>|<span data-ttu-id="ee7ab-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee7ab-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee7ab-127">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ee7ab-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee7ab-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee7ab-129">See Also</span></span>  
 <span data-ttu-id="ee7ab-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="ee7ab-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="ee7ab-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ee7ab-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="ee7ab-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ee7ab-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ee7ab-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ee7ab-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
