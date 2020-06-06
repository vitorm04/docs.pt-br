---
title: <tracking>do WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399428"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="47f1c-102">\<tracking>do WCF</span><span class="sxs-lookup"><span data-stu-id="47f1c-102">\<tracking> of WCF</span></span>
<span data-ttu-id="47f1c-103">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47f1c-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="47f1c-104">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte rastreamento [e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="47f1c-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="47f1c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47f1c-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47f1c-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="47f1c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="47f1c-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="47f1c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47f1c-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="47f1c-108">Attributes</span></span>  
 <span data-ttu-id="47f1c-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="47f1c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="47f1c-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47f1c-110">Child Elements</span></span>  
  
|<span data-ttu-id="47f1c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="47f1c-111">Element</span></span>|<span data-ttu-id="47f1c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="47f1c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="47f1c-113">Uma coleção de elementos de configuração definindo os participantes que assinar a acompanhar registros.</span><span class="sxs-lookup"><span data-stu-id="47f1c-113">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="47f1c-114">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="47f1c-114">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="47f1c-115">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47f1c-115">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47f1c-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="47f1c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="47f1c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="47f1c-117">Element</span></span>|<span data-ttu-id="47f1c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="47f1c-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47f1c-119">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="47f1c-119">system.ServiceModel</span></span>|<span data-ttu-id="47f1c-120">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47f1c-120">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47f1c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="47f1c-121">Remarks</span></span>  
 <span data-ttu-id="47f1c-122">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47f1c-122">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="47f1c-123">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="47f1c-123">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="47f1c-124">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="47f1c-124">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="47f1c-125">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47f1c-125">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="47f1c-126">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="47f1c-126">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="47f1c-127">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47f1c-127">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f1c-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="47f1c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="47f1c-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="47f1c-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
