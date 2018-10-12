---
title: '&lt;trackingProfile&gt; de WCF'
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: a11086ef07a2a605f3889bc4077d25e0b7748e5e
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120908"
---
# <a name="lttrackingprofilegt-of-wcf"></a><span data-ttu-id="2a8e5-102">&lt;trackingProfile&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="2a8e5-102">&lt;trackingProfile&gt; of WCF</span></span>
<span data-ttu-id="2a8e5-103">Representa uma seção de configuração para a criação de uma assinatura para controlar os registros em um participante de rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="2a8e5-104">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="2a8e5-105">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="2a8e5-106">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2a8e5-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="2a8e5-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2a8e5-107">\<system.serviceModel></span></span>  
<span data-ttu-id="2a8e5-108">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="2a8e5-108">\<tracking></span></span>  
<span data-ttu-id="2a8e5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2a8e5-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a8e5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a8e5-110">Syntax</span></span>  
  
```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String" />
          </activityScheduledQueries>
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
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String" 
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a8e5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a8e5-111">Attributes and Elements</span></span>  

<span data-ttu-id="2a8e5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a8e5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a8e5-113">Attributes</span></span>  
  
|<span data-ttu-id="2a8e5-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a8e5-114">Attribute</span></span>|<span data-ttu-id="2a8e5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8e5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a8e5-116">name</span><span class="sxs-lookup"><span data-stu-id="2a8e5-116">name</span></span>|<span data-ttu-id="2a8e5-117">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a8e5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a8e5-118">Child Elements</span></span>  
  
|<span data-ttu-id="2a8e5-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a8e5-119">Element</span></span>|<span data-ttu-id="2a8e5-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8e5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a8e5-121">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="2a8e5-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="2a8e5-122">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a8e5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a8e5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2a8e5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a8e5-124">Element</span></span>|<span data-ttu-id="2a8e5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a8e5-126">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="2a8e5-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="2a8e5-127">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a8e5-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a8e5-128">Remarks</span></span>  
 <span data-ttu-id="2a8e5-129">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="2a8e5-130">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="2a8e5-131">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="2a8e5-132">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o tempo de execução de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="2a8e5-133">Existem alguns tipos de consulta que permitem que você se inscrever em classes diferentes de <xref:System.Activities.Tracking.TrackingRecord> objetos.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="2a8e5-134">Para obter uma lista completa de consultas, consulte [ \<participantes >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) e [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2a8e5-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="2a8e5-135">O exemplo a seguir mostra um perfil de rastreamento em um arquivo de configuração que permite que um participante de rastreamento assinar os `Started` e `Completed` eventos de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2a8e5-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml
<system.serviceModel>
  <tracking>
    <profiles>
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
  
## <a name="see-also"></a><span data-ttu-id="2a8e5-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a8e5-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
- <xref:System.Activities.Tracking.TrackingProfile>  
- [<span data-ttu-id="2a8e5-137">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2a8e5-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="2a8e5-138">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="2a8e5-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
