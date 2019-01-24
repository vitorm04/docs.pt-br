---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 7b872d933d07af329601063b3d769bc43a22007c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568667"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="390d7-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="390d7-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="390d7-103">Representa uma consulta que é usada para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="390d7-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="390d7-104">Por exemplo, você talvez queira manter o controle de toda vez que a atividade de "Enviar email" termina dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="390d7-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="390d7-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="390d7-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="390d7-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="390d7-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="390d7-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="390d7-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="390d7-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="390d7-108">\<system.serviceModel></span></span>  
<span data-ttu-id="390d7-109">\<tracking></span><span class="sxs-lookup"><span data-stu-id="390d7-109">\<tracking></span></span>  
<span data-ttu-id="390d7-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="390d7-110">\<trackingProfile></span></span>  
<span data-ttu-id="390d7-111">\<workflow></span><span class="sxs-lookup"><span data-stu-id="390d7-111">\<workflow></span></span>  
<span data-ttu-id="390d7-112">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="390d7-112">\<activityStateQueries></span></span>  
<span data-ttu-id="390d7-113">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="390d7-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390d7-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="390d7-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="390d7-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="390d7-115">Attributes and Elements</span></span>  
 <span data-ttu-id="390d7-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="390d7-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="390d7-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="390d7-117">Attributes</span></span>  
  
|<span data-ttu-id="390d7-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="390d7-118">Attribute</span></span>|<span data-ttu-id="390d7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="390d7-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="390d7-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="390d7-120">activityName</span></span>|<span data-ttu-id="390d7-121">Uma cadeia de caracteres que especifica o nome da atividade para filtrar <xref:System.Activities.Tracking.ActivityStateRecord> instâncias no.</span><span class="sxs-lookup"><span data-stu-id="390d7-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="390d7-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="390d7-122">Child Elements</span></span>  
  
|<span data-ttu-id="390d7-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="390d7-123">Element</span></span>|<span data-ttu-id="390d7-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="390d7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="390d7-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="390d7-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="390d7-126">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="390d7-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="390d7-127">\<states></span><span class="sxs-lookup"><span data-stu-id="390d7-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="390d7-128">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="390d7-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="390d7-129">\<states></span><span class="sxs-lookup"><span data-stu-id="390d7-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="390d7-130">Uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="390d7-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="390d7-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="390d7-131">Parent Elements</span></span>  
  
|<span data-ttu-id="390d7-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="390d7-132">Element</span></span>|<span data-ttu-id="390d7-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="390d7-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="390d7-134">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="390d7-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="390d7-135">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="390d7-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="390d7-136">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="390d7-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="390d7-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="390d7-137">Remarks</span></span>  
 <span data-ttu-id="390d7-138">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="390d7-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="390d7-139">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="390d7-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="390d7-140">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="390d7-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="390d7-141">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="390d7-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="390d7-142">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="390d7-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="390d7-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="390d7-143">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="390d7-144">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="390d7-144">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="390d7-145">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="390d7-145">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
