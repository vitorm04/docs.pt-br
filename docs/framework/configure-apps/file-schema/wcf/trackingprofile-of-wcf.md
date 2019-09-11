---
title: <trackingProfile>do WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854944"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="a15a7-102">\<trackingProfile > do WCF</span><span class="sxs-lookup"><span data-stu-id="a15a7-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="a15a7-103">Representa uma seção de configuração para criar uma assinatura para registros de rastreamento de fluxo de trabalho em um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a15a7-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="a15a7-104">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a15a7-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="a15a7-105">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="a15a7-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="a15a7-106">Para obter mais informações sobre o rastreamento de fluxo de trabalho e sua configuração, consulte rastreamento de [fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a15a7-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a15a7-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a15a7-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a15a7-108">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a15a7-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a15a7-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a15a7-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a15a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="a15a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a15a7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> trackingProfile**</span><span class="sxs-lookup"><span data-stu-id="a15a7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a15a7-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a15a7-112">Syntax</span></span>  
  
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
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a15a7-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a15a7-113">Attributes and Elements</span></span>  

<span data-ttu-id="a15a7-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a15a7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a15a7-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a15a7-115">Attributes</span></span>  
  
|<span data-ttu-id="a15a7-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="a15a7-116">Attribute</span></span>|<span data-ttu-id="a15a7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a15a7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a15a7-118">name</span><span class="sxs-lookup"><span data-stu-id="a15a7-118">name</span></span>|<span data-ttu-id="a15a7-119">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a15a7-119">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a15a7-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a15a7-120">Child Elements</span></span>  
  
|<span data-ttu-id="a15a7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a15a7-121">Element</span></span>|<span data-ttu-id="a15a7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a15a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a15a7-123">\<participants></span><span class="sxs-lookup"><span data-stu-id="a15a7-123">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="a15a7-124">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a15a7-124">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a15a7-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a15a7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a15a7-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="a15a7-126">Element</span></span>|<span data-ttu-id="a15a7-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a15a7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a15a7-128">\<tracking></span><span class="sxs-lookup"><span data-stu-id="a15a7-128">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="a15a7-129">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a15a7-129">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a15a7-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="a15a7-130">Remarks</span></span>  
 <span data-ttu-id="a15a7-131">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a15a7-131">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="a15a7-132">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a15a7-132">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="a15a7-133">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="a15a7-133">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="a15a7-134">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o tempo de execução de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="a15a7-134">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="a15a7-135">Há alguns tipos de consulta que permitem que você assine diferentes classes de <xref:System.Activities.Tracking.TrackingRecord> objetos.</span><span class="sxs-lookup"><span data-stu-id="a15a7-135">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="a15a7-136">Para obter uma lista completa de consultas, consulte [ \<participantes >](../windows-workflow-foundation/participants.md) e [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a15a7-136">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="a15a7-137">O exemplo a seguir mostra um perfil de controle em um arquivo de configuração que permite que um participante de `Started` controle `Completed` assine os eventos de fluxo de trabalho e.</span><span class="sxs-lookup"><span data-stu-id="a15a7-137">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="a15a7-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a15a7-138">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="a15a7-139">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a15a7-139">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a15a7-140">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a15a7-140">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
