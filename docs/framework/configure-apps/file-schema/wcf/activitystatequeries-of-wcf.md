---
title: '&lt;activityStateQueries&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: b2685da4d5ede9f3d880f6627e86db79b57ee395
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="08c4c-102">&lt;activityStateQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="08c4c-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="08c4c-103">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="08c4c-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="08c4c-104">Por exemplo, convém manter o controle de toda vez que a atividade "Enviar email" é concluído em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="08c4c-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="08c4c-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="08c4c-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="08c4c-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="08c4c-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="08c4c-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="08c4c-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="08c4c-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="08c4c-108">\<system.serviceModel></span></span>  
<span data-ttu-id="08c4c-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="08c4c-109">\<tracking></span></span>  
<span data-ttu-id="08c4c-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="08c4c-110">\<trackingProfile></span></span>  
<span data-ttu-id="08c4c-111">\<workflow></span><span class="sxs-lookup"><span data-stu-id="08c4c-111">\<workflow></span></span>  
<span data-ttu-id="08c4c-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="08c4c-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c4c-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08c4c-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08c4c-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08c4c-114">Attributes and Elements</span></span>  
 <span data-ttu-id="08c4c-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08c4c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08c4c-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="08c4c-116">Attributes</span></span>  
 <span data-ttu-id="08c4c-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="08c4c-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08c4c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08c4c-118">Child Elements</span></span>  
  
|<span data-ttu-id="08c4c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="08c4c-119">Element</span></span>|<span data-ttu-id="08c4c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="08c4c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08c4c-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="08c4c-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="08c4c-122">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="08c4c-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="08c4c-123">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="08c4c-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08c4c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08c4c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="08c4c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="08c4c-125">Element</span></span>|<span data-ttu-id="08c4c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="08c4c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08c4c-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="08c4c-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="08c4c-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="08c4c-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08c4c-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08c4c-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
 <xref:System.Activities.Tracking.ActivityStateQuery>    
 [<span data-ttu-id="08c4c-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="08c4c-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="08c4c-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="08c4c-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
