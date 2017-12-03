---
title: '&lt;trackingProfile&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ba89ec0959f14d27c542eda66cc1da37c42a4e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="lttrackingprofilegt-of-wcf"></a><span data-ttu-id="6029e-102">&lt;trackingProfile&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="6029e-102">&lt;trackingProfile&gt; of WCF</span></span>
<span data-ttu-id="6029e-103">Representa uma seção de configuração para criar uma assinatura para rastrear registros em um participante de rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6029e-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="6029e-104">Um perfil de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6029e-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="6029e-105">As consultas definidas no perfil de rastreamento seção definem os tipos de eventos que são retornados pela assinatura.</span><span class="sxs-lookup"><span data-stu-id="6029e-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="6029e-106">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6029e-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="6029e-107">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6029e-107">\<system.serviceModel></span></span>  
<span data-ttu-id="6029e-108">\<controle ></span><span class="sxs-lookup"><span data-stu-id="6029e-108">\<tracking></span></span>  
<span data-ttu-id="6029e-109">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6029e-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6029e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6029e-110">Syntax</span></span>  
  
```xml
   <system.serviceModel>  <tracking>      <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>    
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6029e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6029e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6029e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6029e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6029e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="6029e-113">Attributes</span></span>  
  
|<span data-ttu-id="6029e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="6029e-114">Attribute</span></span>|<span data-ttu-id="6029e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6029e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6029e-116">name</span><span class="sxs-lookup"><span data-stu-id="6029e-116">name</span></span>|<span data-ttu-id="6029e-117">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6029e-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6029e-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6029e-118">Child Elements</span></span>  
  
|<span data-ttu-id="6029e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="6029e-119">Element</span></span>|<span data-ttu-id="6029e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="6029e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6029e-121">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="6029e-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="6029e-122">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6029e-122">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6029e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6029e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6029e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6029e-124">Element</span></span>|<span data-ttu-id="6029e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6029e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6029e-126">\<controle ></span><span class="sxs-lookup"><span data-stu-id="6029e-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="6029e-127">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6029e-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6029e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6029e-128">Remarks</span></span>  
 <span data-ttu-id="6029e-129">Perfis de rastreamento contém consultas de rastreamento que permitem um participante de rastreamento assinar eventos de fluxo de trabalho que são emitidos quando o estado de uma instância de fluxo de trabalho é alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6029e-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="6029e-130">Dependendo dos requisitos de monitoramento que você pode escrever um perfil que é muito simples, que assina a um pequeno conjunto de alterações de estado de alto nível em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6029e-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="6029e-131">Por outro lado, você pode criar um perfil muito específico cujos eventos resultantes são ricos reconstruir um fluxo de execução detalhado mais adiante.</span><span class="sxs-lookup"><span data-stu-id="6029e-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="6029e-132">Controlando os perfis são estruturados como as assinaturas declarativas para controlar os registros que permitem que você possa ver o tempo de execução de fluxo de trabalho para o controle específico registro.</span><span class="sxs-lookup"><span data-stu-id="6029e-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="6029e-133">Há uma série de tipos de consulta que permitem que você se inscrever para diferentes classes de objetos de TrackingRecord HYPERLINK "http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord (VS.100).aspx".</span><span class="sxs-lookup"><span data-stu-id="6029e-133">There are a handful of query types that allow you subscribe to different classes of  HYPERLINK "http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord(VS.100).aspx" TrackingRecord objects.</span></span> <span data-ttu-id="6029e-134">Para obter uma lista completa de consultas, consulte [ \<participantes >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) e [controle perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="6029e-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="6029e-135">O exemplo a seguir mostra um perfil de rastreamento em um arquivo de configuração que permite que um participante de rastreamento assinar o `Started` e `Completed` eventos de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6029e-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6029e-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6029e-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="6029e-137">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6029e-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6029e-138">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6029e-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
