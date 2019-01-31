---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: b9ce2dec4936d9481cca70c1612387c9c1351de1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281990"
---
# <a name="workflow"></a><span data-ttu-id="c060a-101">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c060a-101">\<workflow></span></span>
<span data-ttu-id="c060a-102">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c060a-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="c060a-103">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c060a-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c060a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c060a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c060a-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c060a-105">\<tracking></span></span>  
<span data-ttu-id="c060a-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c060a-106">\<trackingProfile></span></span>  
<span data-ttu-id="c060a-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c060a-107">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c060a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c060a-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c060a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c060a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c060a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c060a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c060a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c060a-111">Attributes</span></span>  
  
|<span data-ttu-id="c060a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c060a-112">Attribute</span></span>|<span data-ttu-id="c060a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c060a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c060a-114">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c060a-114">activityDefinitionId</span></span>|<span data-ttu-id="c060a-115">Uma cadeia de caracteres que especifica a ID de definição de atividade do fluxo de trabalho que estão sendo controlada.</span><span class="sxs-lookup"><span data-stu-id="c060a-115">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c060a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c060a-116">Child Elements</span></span>  
  
|<span data-ttu-id="c060a-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c060a-117">Element</span></span>|<span data-ttu-id="c060a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c060a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c060a-119">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-119">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="c060a-120">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c060a-120">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c060a-121">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="c060a-121">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="c060a-122">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-122">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="c060a-123">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c060a-123">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="c060a-124">Por exemplo, você talvez queira manter o controle de toda vez que a atividade de "Enviar email" termina dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c060a-124">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="c060a-125">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="c060a-125">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="c060a-126">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="c060a-126">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="c060a-127">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-127">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="c060a-128">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c060a-128">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c060a-129">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="c060a-129">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="c060a-130">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-130">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="c060a-131">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c060a-131">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c060a-132">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="c060a-132">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="c060a-133">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-133">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="c060a-134">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="c060a-134">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c060a-135">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c060a-135">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="c060a-136">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-136">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="c060a-137">Representa uma coleção de consultas que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="c060a-137">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c060a-138">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="c060a-138">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c060a-139">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="c060a-139">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c060a-140">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="c060a-140">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="c060a-141">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="c060a-141">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="c060a-142">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="c060a-142">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c060a-143">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c060a-143">Parent Elements</span></span>  
  
|<span data-ttu-id="c060a-144">Elemento</span><span class="sxs-lookup"><span data-stu-id="c060a-144">Element</span></span>|<span data-ttu-id="c060a-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="c060a-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c060a-146">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c060a-146">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="c060a-147">Representa uma seção de configuração para a criação de uma assinatura para controlar os registros em um participante de rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c060a-147">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="c060a-148">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c060a-148">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="c060a-149">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="c060a-149">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c060a-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="c060a-150">Remarks</span></span>  
 <span data-ttu-id="c060a-151">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho específico é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c060a-151">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="c060a-152">A instância de fluxo de trabalho que estão sendo rastreada é identificada por este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="c060a-152">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="c060a-153">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c060a-153">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="c060a-154">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="c060a-154">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="c060a-155">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o tempo de execução de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="c060a-155">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="c060a-156">Existem alguns tipos de consulta que permitem que você se inscrever em classes diferentes de registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c060a-156">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="c060a-157">Para obter uma lista completa de consultas, consulte a lista de elementos filho deste tópico e [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c060a-157">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="c060a-158">O exemplo a seguir mostra um perfil de rastreamento em um arquivo de configuração que permite que um participante de rastreamento assinar os `Started` e `Completed` eventos de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c060a-158">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c060a-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c060a-159">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="c060a-160">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c060a-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c060a-161">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c060a-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
