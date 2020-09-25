---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 0b00780dedc15fe90163145f23c57f62369c401f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198737"
---
# \<tracking>

<span data-ttu-id="93f5f-101">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="93f5f-101">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="93f5f-102">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte rastreamento [e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="93f5f-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="93f5f-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93f5f-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93f5f-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="93f5f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="93f5f-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="93f5f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93f5f-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="93f5f-106">Attributes</span></span>  

 <span data-ttu-id="93f5f-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="93f5f-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93f5f-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="93f5f-108">Child Elements</span></span>  
  
|<span data-ttu-id="93f5f-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="93f5f-109">Element</span></span>|<span data-ttu-id="93f5f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="93f5f-110">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="93f5f-111">Uma coleção de elementos de configuração definindo os participantes que assinar a acompanhar registros.</span><span class="sxs-lookup"><span data-stu-id="93f5f-111">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="93f5f-112">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="93f5f-112">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="93f5f-113">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="93f5f-113">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93f5f-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="93f5f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="93f5f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="93f5f-115">Element</span></span>|<span data-ttu-id="93f5f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="93f5f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93f5f-117">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="93f5f-117">system.ServiceModel</span></span>|<span data-ttu-id="93f5f-118">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="93f5f-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93f5f-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="93f5f-119">Remarks</span></span>  

 <span data-ttu-id="93f5f-120">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="93f5f-120">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="93f5f-121">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="93f5f-121">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="93f5f-122">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="93f5f-122">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="93f5f-123">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="93f5f-123">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="93f5f-124">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="93f5f-124">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="93f5f-125">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="93f5f-125">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f5f-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="93f5f-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="93f5f-127">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="93f5f-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
