---
title: <tracking>do WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399428"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="084d9-102">\<acompanhamento de > do WCF</span><span class="sxs-lookup"><span data-stu-id="084d9-102">\<tracking> of WCF</span></span>
<span data-ttu-id="084d9-103">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="084d9-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="084d9-104">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte rastreamento [e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="084d9-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="084d9-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="084d9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="084d9-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="084d9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="084d9-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<acompanhamento de >**</span><span class="sxs-lookup"><span data-stu-id="084d9-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="084d9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="084d9-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="084d9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="084d9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="084d9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="084d9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="084d9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="084d9-111">Attributes</span></span>  
 <span data-ttu-id="084d9-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="084d9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="084d9-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="084d9-113">Child Elements</span></span>  
  
|<span data-ttu-id="084d9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="084d9-114">Element</span></span>|<span data-ttu-id="084d9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="084d9-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="084d9-116">\<participants></span><span class="sxs-lookup"><span data-stu-id="084d9-116">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="084d9-117">Uma coleção de elementos de configuração que define os participantes que assinam os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="084d9-117">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="084d9-118">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="084d9-118">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="084d9-119">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="084d9-119">\<trackingProfile></span></span>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="084d9-120">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="084d9-120">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="084d9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="084d9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="084d9-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="084d9-122">Element</span></span>|<span data-ttu-id="084d9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="084d9-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="084d9-124">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="084d9-124">system.ServiceModel</span></span>|<span data-ttu-id="084d9-125">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="084d9-125">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="084d9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="084d9-126">Remarks</span></span>  
 <span data-ttu-id="084d9-127">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="084d9-127">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="084d9-128">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="084d9-128">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="084d9-129">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="084d9-129">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="084d9-130">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="084d9-130">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="084d9-131">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="084d9-131">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="084d9-132">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="084d9-132">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084d9-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="084d9-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="084d9-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="084d9-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
