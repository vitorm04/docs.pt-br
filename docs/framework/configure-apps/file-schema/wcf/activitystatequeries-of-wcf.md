---
title: '&lt;activityStateQueries&gt; do WCF'
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 081dc297912ed5735dd51111936b85b61f463d2d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123235"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="916a2-102">&lt;activityStateQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="916a2-102">&lt;activityStateQueries&gt; of WCF</span></span>

<span data-ttu-id="916a2-103">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="916a2-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="916a2-104">Por exemplo, você talvez queira manter o controle de toda vez que a atividade de "Enviar email" termina dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="916a2-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="916a2-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="916a2-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="916a2-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="916a2-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="916a2-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="916a2-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="916a2-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="916a2-108">\<system.serviceModel></span></span>  
<span data-ttu-id="916a2-109">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="916a2-109">\<tracking></span></span>  
<span data-ttu-id="916a2-110">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="916a2-110">\<profiles></span></span>  
<span data-ttu-id="916a2-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="916a2-111">\<trackingProfile></span></span>  
<span data-ttu-id="916a2-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="916a2-112">\<workflow></span></span>  
<span data-ttu-id="916a2-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="916a2-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="916a2-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="916a2-114">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="916a2-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="916a2-115">Attributes and elements</span></span>

<span data-ttu-id="916a2-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="916a2-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="916a2-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="916a2-117">Attributes</span></span>  

<span data-ttu-id="916a2-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="916a2-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="916a2-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="916a2-119">Child elements</span></span>

|<span data-ttu-id="916a2-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="916a2-120">Element</span></span>|<span data-ttu-id="916a2-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="916a2-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="916a2-122">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="916a2-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="916a2-123">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="916a2-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="916a2-124">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="916a2-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="916a2-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="916a2-125">Parent elements</span></span>

|<span data-ttu-id="916a2-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="916a2-126">Element</span></span>|<span data-ttu-id="916a2-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="916a2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="916a2-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="916a2-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="916a2-129">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="916a2-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="916a2-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="916a2-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
- <xref:System.Activities.Tracking.ActivityStateQuery>    
- [<span data-ttu-id="916a2-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="916a2-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="916a2-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="916a2-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
