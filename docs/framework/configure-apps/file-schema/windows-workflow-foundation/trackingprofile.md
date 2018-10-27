---
title: '&lt;trackingProfile&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8ab3c0c30c193d176febbf832274a54b214b5458
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047963"
---
# <a name="lttrackingprofilegt"></a><span data-ttu-id="2be6a-102">&lt;trackingProfile&gt;</span><span class="sxs-lookup"><span data-stu-id="2be6a-102">&lt;trackingProfile&gt;</span></span>
<span data-ttu-id="2be6a-103">Representa uma seção de configuração para a criação de uma assinatura para controlar os registros em um participante de rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2be6a-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="2be6a-104">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2be6a-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="2be6a-105">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="2be6a-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="2be6a-106">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2be6a-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2be6a-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2be6a-107">\<system.serviceModel></span></span>  
<span data-ttu-id="2be6a-108">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="2be6a-108">\<tracking></span></span>  
<span data-ttu-id="2be6a-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2be6a-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be6a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2be6a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2be6a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2be6a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2be6a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2be6a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2be6a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="2be6a-113">Attributes</span></span>  
  
|<span data-ttu-id="2be6a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="2be6a-114">Attribute</span></span>|<span data-ttu-id="2be6a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2be6a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2be6a-116">name</span><span class="sxs-lookup"><span data-stu-id="2be6a-116">name</span></span>|<span data-ttu-id="2be6a-117">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2be6a-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2be6a-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2be6a-118">Child Elements</span></span>  
  
|<span data-ttu-id="2be6a-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2be6a-119">Element</span></span>|<span data-ttu-id="2be6a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2be6a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2be6a-121">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="2be6a-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="2be6a-122">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2be6a-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2be6a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2be6a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2be6a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="2be6a-124">Element</span></span>|<span data-ttu-id="2be6a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2be6a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2be6a-126">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="2be6a-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="2be6a-127">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2be6a-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2be6a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2be6a-128">Remarks</span></span>  
 <span data-ttu-id="2be6a-129">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2be6a-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="2be6a-130">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2be6a-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="2be6a-131">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="2be6a-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="2be6a-132">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o tempo de execução de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="2be6a-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="2be6a-133">Existem alguns tipos de consulta que permitem que você se inscrever em classes diferentes de <xref:System.Activities.Tracking.TrackingRecord> objetos.</span><span class="sxs-lookup"><span data-stu-id="2be6a-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="2be6a-134">Para obter uma lista completa de consultas, consulte [ \<participantes >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) e [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="2be6a-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="2be6a-135">O exemplo a seguir mostra um perfil de rastreamento em um arquivo de configuração que permite que um participante de rastreamento assinar os `Started` e `Completed` eventos de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2be6a-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2be6a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2be6a-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="2be6a-137">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2be6a-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2be6a-138">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="2be6a-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
