---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397508"
---
# \<workflowInstanceQuery>
<span data-ttu-id="8d43e-101">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="8d43e-101">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="8d43e-102">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8d43e-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="8d43e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d43e-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d43e-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d43e-104">Attributes and Elements</span></span>  
 <span data-ttu-id="8d43e-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d43e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d43e-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d43e-106">Attributes</span></span>  
 <span data-ttu-id="8d43e-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8d43e-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d43e-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d43e-108">Child Elements</span></span>  
  
|<span data-ttu-id="8d43e-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d43e-109">Element</span></span>|<span data-ttu-id="8d43e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d43e-110">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="8d43e-111">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="8d43e-111">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d43e-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d43e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8d43e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d43e-113">Element</span></span>|<span data-ttu-id="8d43e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d43e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="8d43e-115">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="8d43e-115">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d43e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d43e-116">Remarks</span></span>  
 <span data-ttu-id="8d43e-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="8d43e-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="8d43e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d43e-118">Example</span></span>  
 <span data-ttu-id="8d43e-119">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="8d43e-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d43e-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d43e-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8d43e-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d43e-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8d43e-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8d43e-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
