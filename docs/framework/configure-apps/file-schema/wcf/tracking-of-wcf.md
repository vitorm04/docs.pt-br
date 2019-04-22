---
title: <tracking> do WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: 4aac9f28de746e2a75a079cbaf774f01f4a08fca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135818"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="b88e1-102">\<Acompanhamento > do WCF</span><span class="sxs-lookup"><span data-stu-id="b88e1-102">\<tracking> of WCF</span></span>
<span data-ttu-id="b88e1-103">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b88e1-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="b88e1-104">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [Configurando o rastreamento para um fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b88e1-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="b88e1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b88e1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b88e1-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b88e1-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88e1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b88e1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
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
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b88e1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b88e1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b88e1-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b88e1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b88e1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b88e1-110">Attributes</span></span>  
 <span data-ttu-id="b88e1-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b88e1-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b88e1-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b88e1-112">Child Elements</span></span>  
  
|<span data-ttu-id="b88e1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b88e1-113">Element</span></span>|<span data-ttu-id="b88e1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88e1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b88e1-115">\<participants></span><span class="sxs-lookup"><span data-stu-id="b88e1-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="b88e1-116">Uma coleção de elementos de configuração definindo os participantes que assinar a acompanhar registros.</span><span class="sxs-lookup"><span data-stu-id="b88e1-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="b88e1-117">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="b88e1-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="b88e1-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b88e1-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="b88e1-119">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b88e1-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b88e1-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b88e1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b88e1-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b88e1-121">Element</span></span>|<span data-ttu-id="b88e1-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88e1-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b88e1-123">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b88e1-123">system.ServiceModel</span></span>|<span data-ttu-id="b88e1-124">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b88e1-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b88e1-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b88e1-125">Remarks</span></span>  
 <span data-ttu-id="b88e1-126">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b88e1-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="b88e1-127">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="b88e1-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="b88e1-128">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="b88e1-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="b88e1-129">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b88e1-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="b88e1-130">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b88e1-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="b88e1-131">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b88e1-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88e1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b88e1-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="b88e1-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b88e1-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
