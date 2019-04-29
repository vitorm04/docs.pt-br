---
title: <states> de <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: fa3736fc13f6f40f52d15b8257b7a79f4179d738
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796949"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="14dfb-102">\<estados > do \<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="14dfb-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="14dfb-103">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="14dfb-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="14dfb-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="14dfb-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="14dfb-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="14dfb-105">\<system.serviceModel></span></span>  
<span data-ttu-id="14dfb-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="14dfb-106">\<tracking></span></span>  
<span data-ttu-id="14dfb-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="14dfb-107">\<trackingProfile></span></span>  
<span data-ttu-id="14dfb-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="14dfb-108">\<workflow></span></span>  
<span data-ttu-id="14dfb-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="14dfb-109">\<activityStateQueries></span></span>  
<span data-ttu-id="14dfb-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="14dfb-110">\<activityStateQuery></span></span>  
<span data-ttu-id="14dfb-111">\<states></span><span class="sxs-lookup"><span data-stu-id="14dfb-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14dfb-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14dfb-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14dfb-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="14dfb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="14dfb-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="14dfb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14dfb-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="14dfb-115">Attributes</span></span>  
 <span data-ttu-id="14dfb-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="14dfb-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14dfb-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="14dfb-117">Child Elements</span></span>  
  
|<span data-ttu-id="14dfb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="14dfb-118">Element</span></span>|<span data-ttu-id="14dfb-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="14dfb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14dfb-120">\<state></span><span class="sxs-lookup"><span data-stu-id="14dfb-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="14dfb-121">Um elemento de configuração que contém os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="14dfb-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14dfb-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="14dfb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="14dfb-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="14dfb-123">Element</span></span>|<span data-ttu-id="14dfb-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="14dfb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14dfb-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="14dfb-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="14dfb-126">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="14dfb-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="14dfb-127">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="14dfb-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14dfb-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="14dfb-128">Remarks</span></span>  
 <span data-ttu-id="14dfb-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="14dfb-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="14dfb-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="14dfb-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="14dfb-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="14dfb-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="14dfb-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="14dfb-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="14dfb-133">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="14dfb-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14dfb-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14dfb-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="14dfb-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="14dfb-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="14dfb-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="14dfb-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
