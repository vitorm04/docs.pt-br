---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 9ddb3f1d070531d76201c0b9b5e71f14e2fac496
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377463"
---
# <a name="activitystatequery"></a><span data-ttu-id="dff82-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="dff82-101">\<activityStateQuery></span></span>
<span data-ttu-id="dff82-102">Representa uma consulta que é usada para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dff82-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="dff82-103">Por exemplo, você talvez queira manter o controle de toda vez que a atividade de "Enviar email" termina dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dff82-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="dff82-104">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="dff82-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="dff82-105">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="dff82-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="dff82-106">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dff82-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="dff82-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dff82-107">\<system.serviceModel></span></span>  
<span data-ttu-id="dff82-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="dff82-108">\<tracking></span></span>  
<span data-ttu-id="dff82-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dff82-109">\<trackingProfile></span></span>  
<span data-ttu-id="dff82-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="dff82-110">\<workflow></span></span>  
<span data-ttu-id="dff82-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="dff82-111">\<activityStateQueries></span></span>  
<span data-ttu-id="dff82-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="dff82-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff82-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dff82-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dff82-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dff82-114">Attributes and Elements</span></span>  
 <span data-ttu-id="dff82-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dff82-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dff82-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="dff82-116">Attributes</span></span>  
  
|<span data-ttu-id="dff82-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="dff82-117">Attribute</span></span>|<span data-ttu-id="dff82-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dff82-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dff82-119">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="dff82-119">activityName</span></span>|<span data-ttu-id="dff82-120">Uma cadeia de caracteres que especifica o nome da atividade para filtrar <xref:System.Activities.Tracking.ActivityStateRecord> instâncias no.</span><span class="sxs-lookup"><span data-stu-id="dff82-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dff82-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dff82-121">Child Elements</span></span>  
  
|<span data-ttu-id="dff82-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="dff82-122">Element</span></span>|<span data-ttu-id="dff82-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="dff82-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dff82-124">\<arguments></span><span class="sxs-lookup"><span data-stu-id="dff82-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="dff82-125">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="dff82-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="dff82-126">\<states></span><span class="sxs-lookup"><span data-stu-id="dff82-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="dff82-127">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="dff82-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="dff82-128">\<states></span><span class="sxs-lookup"><span data-stu-id="dff82-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="dff82-129">Uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="dff82-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dff82-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dff82-130">Parent Elements</span></span>  
  
|<span data-ttu-id="dff82-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="dff82-131">Element</span></span>|<span data-ttu-id="dff82-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="dff82-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dff82-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="dff82-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="dff82-134">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="dff82-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="dff82-135">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="dff82-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dff82-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="dff82-136">Remarks</span></span>  
 <span data-ttu-id="dff82-137">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dff82-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="dff82-138">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="dff82-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="dff82-139">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dff82-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="dff82-140">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="dff82-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="dff82-141">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="dff82-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dff82-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dff82-142">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dff82-143">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="dff82-143">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dff82-144">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="dff82-144">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
