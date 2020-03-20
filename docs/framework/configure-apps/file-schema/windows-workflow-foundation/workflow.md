---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151852"
---
# <a name="workflow"></a><span data-ttu-id="b7787-101">\<> de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7787-101">\<workflow></span></span>
<span data-ttu-id="b7787-102">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b7787-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b7787-103">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte Perfis de [rastreamento e rastreamento de fluxo](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) [de](../../../windows-workflow-foundation/tracking-profiles.md)trabalho .</span><span class="sxs-lookup"><span data-stu-id="b7787-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b7787-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7787-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7787-105">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b7787-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b7787-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="b7787-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="b7787-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="b7787-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="b7787-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de fluxo de trabalho**</span><span class="sxs-lookup"><span data-stu-id="b7787-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7787-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7787-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7787-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7787-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7787-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7787-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7787-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7787-112">Attributes</span></span>  
  
|<span data-ttu-id="b7787-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7787-113">Attribute</span></span>|<span data-ttu-id="b7787-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7787-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7787-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b7787-115">activityDefinitionId</span></span>|<span data-ttu-id="b7787-116">Uma cadeia de caracteres que especifica a ID de definição de atividade do fluxo de trabalho que estão sendo controlada.</span><span class="sxs-lookup"><span data-stu-id="b7787-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7787-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7787-117">Child Elements</span></span>  
  
|<span data-ttu-id="b7787-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7787-118">Element</span></span>|<span data-ttu-id="b7787-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7787-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7787-120">\<atividades>agendadas</span><span class="sxs-lookup"><span data-stu-id="b7787-120">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="b7787-121">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b7787-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b7787-122">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="b7787-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="b7787-123">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b7787-123">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="b7787-124">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7787-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b7787-125">Por exemplo, você pode querer acompanhar cada vez que a atividade "Enviar e-mail" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7787-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b7787-126">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="b7787-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="b7787-127">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="b7787-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="b7787-128">\<>dede marcas de marca</span><span class="sxs-lookup"><span data-stu-id="b7787-128">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="b7787-129">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7787-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b7787-130">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="b7787-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="b7787-131">\<cancelarConsultas solicitadas></span><span class="sxs-lookup"><span data-stu-id="b7787-131">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="b7787-132">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b7787-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b7787-133">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="b7787-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="b7787-134">\<>de rastreamento personalizado</span><span class="sxs-lookup"><span data-stu-id="b7787-134">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="b7787-135">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="b7787-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="b7787-136">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b7787-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="b7787-137">\<falhasPropagaçãoQueries></span><span class="sxs-lookup"><span data-stu-id="b7787-137">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="b7787-138">Representa uma coleção de consultas que são usadas para rastrear o manuseio de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b7787-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b7787-139">Esse evento ocorre cada vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="b7787-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b7787-140">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b7787-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b7787-141">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="b7787-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="b7787-142">\<fluxo de trabalhoInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="b7787-142">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="b7787-143">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="b7787-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7787-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7787-144">Parent Elements</span></span>  
  
|<span data-ttu-id="b7787-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7787-145">Element</span></span>|<span data-ttu-id="b7787-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7787-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7787-147">\<>de rastreamentoPerfil</span><span class="sxs-lookup"><span data-stu-id="b7787-147">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="b7787-148">Representa uma seção de configuração para criar uma assinatura para controlar os registros em um participante de rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7787-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="b7787-149">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em runtime.</span><span class="sxs-lookup"><span data-stu-id="b7787-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="b7787-150">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="b7787-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7787-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7787-151">Remarks</span></span>  
 <span data-ttu-id="b7787-152">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho específico é alterado em runtime.</span><span class="sxs-lookup"><span data-stu-id="b7787-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="b7787-153">A instância de fluxo de trabalho que estão sendo rastreada é identificada por este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="b7787-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="b7787-154">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7787-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="b7787-155">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="b7787-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="b7787-156">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o runtime de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="b7787-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="b7787-157">Existem alguns tipos de consulta que permitem que você se inscrever em classes diferentes de registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b7787-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="b7787-158">Para obter uma lista completa de consultas, consulte a lista de [elementos](../../../windows-workflow-foundation/tracking-profiles.md)filho deste tópico e perfis de rastreamento .</span><span class="sxs-lookup"><span data-stu-id="b7787-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b7787-159">O exemplo a seguir mostra um perfil de rastreamento em `Started` um `Completed` arquivo de configuração que permite que um participante de rastreamento se inscreva nos eventos do fluxo de trabalho e do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7787-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7787-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7787-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="b7787-161">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7787-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b7787-162">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b7787-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
