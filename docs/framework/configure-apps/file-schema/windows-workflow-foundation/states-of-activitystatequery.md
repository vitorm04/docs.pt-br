---
title: <states> de <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 50827577374859133e6c673e8850e145b4ccab73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947429"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="30b1b-102">\<> de Estados \<de > de activityStateQuery</span><span class="sxs-lookup"><span data-stu-id="30b1b-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="30b1b-103">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="30b1b-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="30b1b-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="30b1b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="30b1b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30b1b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="30b1b-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="30b1b-106">\<tracking></span></span>  
<span data-ttu-id="30b1b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="30b1b-107">\<trackingProfile></span></span>  
<span data-ttu-id="30b1b-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="30b1b-108">\<workflow></span></span>  
<span data-ttu-id="30b1b-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="30b1b-109">\<activityStateQueries></span></span>  
<span data-ttu-id="30b1b-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="30b1b-110">\<activityStateQuery></span></span>  
<span data-ttu-id="30b1b-111">\<> de Estados</span><span class="sxs-lookup"><span data-stu-id="30b1b-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b1b-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30b1b-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30b1b-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30b1b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="30b1b-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30b1b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30b1b-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="30b1b-115">Attributes</span></span>  
 <span data-ttu-id="30b1b-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="30b1b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="30b1b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30b1b-117">Child Elements</span></span>  
  
|<span data-ttu-id="30b1b-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="30b1b-118">Element</span></span>|<span data-ttu-id="30b1b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="30b1b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30b1b-120">\<state></span><span class="sxs-lookup"><span data-stu-id="30b1b-120">\<state></span></span>](state-of-states.md)|<span data-ttu-id="30b1b-121">Um elemento de configuração que contém os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="30b1b-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30b1b-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30b1b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="30b1b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="30b1b-123">Element</span></span>|<span data-ttu-id="30b1b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="30b1b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30b1b-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="30b1b-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="30b1b-126">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="30b1b-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="30b1b-127">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="30b1b-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30b1b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="30b1b-128">Remarks</span></span>  
 <span data-ttu-id="30b1b-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="30b1b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="30b1b-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="30b1b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="30b1b-131">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="30b1b-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="30b1b-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="30b1b-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="30b1b-133">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="30b1b-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30b1b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30b1b-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="30b1b-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="30b1b-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="30b1b-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="30b1b-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
