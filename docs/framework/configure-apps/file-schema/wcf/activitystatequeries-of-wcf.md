---
title: '&lt;activityStateQueries&gt; do WCF'
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 2dabfdd248006de60b5e84e739f78e03f364dde3
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146180"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="313b1-102">&lt;activityStateQueries&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="313b1-102">&lt;activityStateQueries&gt; of WCF</span></span>

<span data-ttu-id="313b1-103">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="313b1-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="313b1-104">Por exemplo, você talvez queira manter o controle de toda vez que a atividade de "Enviar email" termina dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="313b1-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="313b1-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="313b1-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="313b1-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="313b1-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="313b1-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="313b1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="313b1-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="313b1-108">\<system.serviceModel></span></span>  
<span data-ttu-id="313b1-109">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="313b1-109">\<tracking></span></span>  
<span data-ttu-id="313b1-110">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="313b1-110">\<profiles></span></span>  
<span data-ttu-id="313b1-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="313b1-111">\<trackingProfile></span></span>  
<span data-ttu-id="313b1-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="313b1-112">\<workflow></span></span>  
<span data-ttu-id="313b1-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="313b1-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="313b1-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="313b1-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="313b1-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="313b1-115">Attributes and elements</span></span>

<span data-ttu-id="313b1-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="313b1-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="313b1-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="313b1-117">Attributes</span></span>  

<span data-ttu-id="313b1-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="313b1-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="313b1-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="313b1-119">Child elements</span></span>

|<span data-ttu-id="313b1-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="313b1-120">Element</span></span>|<span data-ttu-id="313b1-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="313b1-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="313b1-122">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="313b1-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="313b1-123">Uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="313b1-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="313b1-124">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="313b1-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="313b1-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="313b1-125">Parent elements</span></span>

|<span data-ttu-id="313b1-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="313b1-126">Element</span></span>|<span data-ttu-id="313b1-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="313b1-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="313b1-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="313b1-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="313b1-129">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="313b1-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="313b1-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="313b1-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
- <xref:System.Activities.Tracking.ActivityStateQuery>    
- [<span data-ttu-id="313b1-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="313b1-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="313b1-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="313b1-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
