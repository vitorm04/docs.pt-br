---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: fa96cb374204ffbdb4c0fcd353c70b6e27ef7481
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263804"
---
# <a name="tracking"></a><span data-ttu-id="ec968-101">\<tracking></span><span class="sxs-lookup"><span data-stu-id="ec968-101">\<tracking></span></span>
<span data-ttu-id="ec968-102">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec968-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="ec968-103">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [Configurando o rastreamento para um fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ec968-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="ec968-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ec968-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ec968-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="ec968-105">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec968-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec968-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec968-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec968-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ec968-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec968-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec968-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec968-109">Attributes</span></span>  
 <span data-ttu-id="ec968-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ec968-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec968-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec968-111">Child Elements</span></span>  
  
|<span data-ttu-id="ec968-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec968-112">Element</span></span>|<span data-ttu-id="ec968-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec968-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec968-114">\<participants></span><span class="sxs-lookup"><span data-stu-id="ec968-114">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="ec968-115">Uma coleção de elementos de configuração definindo os participantes que assinar a acompanhar registros.</span><span class="sxs-lookup"><span data-stu-id="ec968-115">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="ec968-116">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="ec968-116">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="ec968-117">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ec968-117">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="ec968-118">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec968-118">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec968-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec968-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ec968-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec968-120">Element</span></span>|<span data-ttu-id="ec968-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec968-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec968-122">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ec968-122">system.ServiceModel</span></span>|<span data-ttu-id="ec968-123">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec968-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec968-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec968-124">Remarks</span></span>  
 <span data-ttu-id="ec968-125">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec968-125">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="ec968-126">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="ec968-126">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="ec968-127">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="ec968-127">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="ec968-128">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec968-128">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="ec968-129">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ec968-129">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="ec968-130">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec968-130">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec968-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec968-131">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="ec968-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ec968-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
