---
title: '&lt;controle&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b7b0d04681d137e1f63e9a10b09fabd746e5554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttrackinggt"></a><span data-ttu-id="8f525-102">&lt;controle&gt;</span><span class="sxs-lookup"><span data-stu-id="8f525-102">&lt;tracking&gt;</span></span>
<span data-ttu-id="8f525-103">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f525-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="8f525-104">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configurar rastreamento para um fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8f525-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="8f525-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8f525-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8f525-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="8f525-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f525-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f525-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f525-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f525-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8f525-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f525-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f525-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f525-110">Attributes</span></span>  
 <span data-ttu-id="8f525-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8f525-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f525-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f525-112">Child Elements</span></span>  
  
|<span data-ttu-id="8f525-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f525-113">Element</span></span>|<span data-ttu-id="8f525-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f525-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f525-115">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="8f525-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="8f525-116">Uma coleção de elementos de configuração definindo participantes que se inscrever para rastrear registros.</span><span class="sxs-lookup"><span data-stu-id="8f525-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="8f525-117">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="8f525-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="8f525-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8f525-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="8f525-119">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f525-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f525-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f525-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8f525-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f525-121">Element</span></span>|<span data-ttu-id="8f525-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f525-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f525-123">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8f525-123">system.ServiceModel</span></span>|<span data-ttu-id="8f525-124">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f525-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f525-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f525-125">Remarks</span></span>  
 <span data-ttu-id="8f525-126">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f525-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="8f525-127">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="8f525-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="8f525-128">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="8f525-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="8f525-129">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f525-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="8f525-130">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8f525-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="8f525-131">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f525-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f525-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f525-132">See Also</span></span>  
 <span data-ttu-id="8f525-133"><xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8f525-133"><xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8f525-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8f525-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
