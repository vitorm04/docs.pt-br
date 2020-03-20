---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8985da7e1223ac117cf1b68227140634f9c85d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151883"
---
# <a name="trackingprofile"></a><span data-ttu-id="3a12c-101">\<> de rastreamentoperfil</span><span class="sxs-lookup"><span data-stu-id="3a12c-101">\<trackingProfile></span></span>
<span data-ttu-id="3a12c-102">Representa uma seção de configuração para criar uma assinatura para controlar os registros em um participante de rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3a12c-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="3a12c-103">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em runtime.</span><span class="sxs-lookup"><span data-stu-id="3a12c-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3a12c-104">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="3a12c-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="3a12c-105">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte Perfis de [rastreamento e rastreamento de fluxo](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) [de](../../../windows-workflow-foundation/tracking-profiles.md)trabalho .</span><span class="sxs-lookup"><span data-stu-id="3a12c-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3a12c-106">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a12c-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a12c-107">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3a12c-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="3a12c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="3a12c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="3a12c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de rastreamentoPerfil**</span><span class="sxs-lookup"><span data-stu-id="3a12c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a12c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a12c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a12c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a12c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3a12c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a12c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a12c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a12c-113">Attributes</span></span>  
  
|<span data-ttu-id="3a12c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a12c-114">Attribute</span></span>|<span data-ttu-id="3a12c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a12c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a12c-116">name</span><span class="sxs-lookup"><span data-stu-id="3a12c-116">name</span></span>|<span data-ttu-id="3a12c-117">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3a12c-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a12c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a12c-118">Child Elements</span></span>  
  
|<span data-ttu-id="3a12c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a12c-119">Element</span></span>|<span data-ttu-id="3a12c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a12c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a12c-121">\<participantes></span><span class="sxs-lookup"><span data-stu-id="3a12c-121">\<participants></span></span>](participants.md)|<span data-ttu-id="3a12c-122">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3a12c-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a12c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a12c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3a12c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a12c-124">Element</span></span>|<span data-ttu-id="3a12c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a12c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a12c-126">\<rastreando></span><span class="sxs-lookup"><span data-stu-id="3a12c-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="3a12c-127">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3a12c-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a12c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a12c-128">Remarks</span></span>  
 <span data-ttu-id="3a12c-129">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em runtime.</span><span class="sxs-lookup"><span data-stu-id="3a12c-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3a12c-130">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3a12c-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="3a12c-131">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="3a12c-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="3a12c-132">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o runtime de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="3a12c-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="3a12c-133">Existem um punhado de tipos de consulta que <xref:System.Activities.Tracking.TrackingRecord> permitem que você se inscreva em diferentes classes de objetos.</span><span class="sxs-lookup"><span data-stu-id="3a12c-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="3a12c-134">Para obter uma lista completa de consultas, consulte [ \<participantes>](participants.md) e [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="3a12c-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="3a12c-135">O exemplo a seguir mostra um perfil de rastreamento em `Started` um `Completed` arquivo de configuração que permite que um participante de rastreamento se inscreva nos eventos do fluxo de trabalho e do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3a12c-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a12c-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a12c-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="3a12c-137">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3a12c-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3a12c-138">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3a12c-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
