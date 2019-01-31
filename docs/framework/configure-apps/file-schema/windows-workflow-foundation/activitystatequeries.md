---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: ad41c1afec0b46a404f8f24882587c1dfeb68a80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267801"
---
# <a name="activitystatequeries"></a><span data-ttu-id="c4ee1-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="c4ee1-101">\<activityStateQueries></span></span>
<span data-ttu-id="c4ee1-102">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="c4ee1-103">Por exemplo, você talvez queira manter o controle de toda vez que a atividade de "Enviar email" termina dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="c4ee1-104">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="c4ee1-105">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="c4ee1-106">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c4ee1-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c4ee1-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c4ee1-107">\<system.serviceModel></span></span>  
<span data-ttu-id="c4ee1-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c4ee1-108">\<tracking></span></span>  
<span data-ttu-id="c4ee1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c4ee1-109">\<trackingProfile></span></span>  
<span data-ttu-id="c4ee1-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c4ee1-110">\<workflow></span></span>  
<span data-ttu-id="c4ee1-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="c4ee1-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ee1-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4ee1-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4ee1-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c4ee1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c4ee1-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4ee1-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="c4ee1-115">Attributes</span></span>  
 <span data-ttu-id="c4ee1-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4ee1-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c4ee1-117">Child Elements</span></span>  
  
|<span data-ttu-id="c4ee1-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4ee1-118">Element</span></span>|<span data-ttu-id="c4ee1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4ee1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4ee1-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="c4ee1-120">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="c4ee1-121">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c4ee1-122">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4ee1-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c4ee1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c4ee1-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4ee1-124">Element</span></span>|<span data-ttu-id="c4ee1-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4ee1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4ee1-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c4ee1-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c4ee1-127">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c4ee1-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4ee1-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4ee1-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c4ee1-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c4ee1-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c4ee1-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c4ee1-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
