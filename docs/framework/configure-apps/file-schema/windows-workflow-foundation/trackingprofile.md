---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8b8cfe95a646563642e7425fdb4b5257cafa466f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947294"
---
# <a name="trackingprofile"></a><span data-ttu-id="b5562-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b5562-101">\<trackingProfile></span></span>
<span data-ttu-id="b5562-102">Representa uma seção de configuração para criar uma assinatura para registros de rastreamento de fluxo de trabalho em um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b5562-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="b5562-103">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b5562-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="b5562-104">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="b5562-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="b5562-105">Para obter mais informações sobre o rastreamento de fluxo de trabalho e sua configuração, consulte rastreamento de [fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b5562-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b5562-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b5562-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b5562-107">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="b5562-107">\<tracking></span></span>  
<span data-ttu-id="b5562-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b5562-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5562-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5562-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5562-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b5562-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b5562-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b5562-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5562-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5562-112">Attributes</span></span>  
  
|<span data-ttu-id="b5562-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b5562-113">Attribute</span></span>|<span data-ttu-id="b5562-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5562-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5562-115">name</span><span class="sxs-lookup"><span data-stu-id="b5562-115">name</span></span>|<span data-ttu-id="b5562-116">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b5562-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5562-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b5562-117">Child Elements</span></span>  
  
|<span data-ttu-id="b5562-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5562-118">Element</span></span>|<span data-ttu-id="b5562-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5562-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5562-120">\<participants></span><span class="sxs-lookup"><span data-stu-id="b5562-120">\<participants></span></span>](participants.md)|<span data-ttu-id="b5562-121">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b5562-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5562-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b5562-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b5562-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5562-123">Element</span></span>|<span data-ttu-id="b5562-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5562-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5562-125">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b5562-125">\<tracking></span></span>](tracking.md)|<span data-ttu-id="b5562-126">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b5562-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5562-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5562-127">Remarks</span></span>  
 <span data-ttu-id="b5562-128">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b5562-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="b5562-129">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b5562-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="b5562-130">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="b5562-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="b5562-131">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o tempo de execução de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="b5562-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="b5562-132">Há alguns tipos de consulta que permitem que você assine diferentes classes de <xref:System.Activities.Tracking.TrackingRecord> objetos.</span><span class="sxs-lookup"><span data-stu-id="b5562-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="b5562-133">Para obter uma lista completa de consultas, consulte [ \<participantes >](participants.md) e [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="b5562-133">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="b5562-134">O exemplo a seguir mostra um perfil de controle em um arquivo de configuração que permite que um participante de `Started` controle `Completed` assine os eventos de fluxo de trabalho e.</span><span class="sxs-lookup"><span data-stu-id="b5562-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5562-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5562-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="b5562-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b5562-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b5562-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b5562-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
