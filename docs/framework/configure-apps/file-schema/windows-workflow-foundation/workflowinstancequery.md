---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 6fe02cfea91633da41c8ebc7d8a78dd005ad3f4a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080898"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="7544a-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7544a-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="7544a-102">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="7544a-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="7544a-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7544a-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7544a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7544a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7544a-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="7544a-105">\<tracking></span></span>  
<span data-ttu-id="7544a-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7544a-106">\<trackingProfile></span></span>  
<span data-ttu-id="7544a-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7544a-107">\<workflow></span></span>  
<span data-ttu-id="7544a-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7544a-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="7544a-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7544a-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7544a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7544a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7544a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7544a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7544a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7544a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7544a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="7544a-113">Attributes</span></span>  
 <span data-ttu-id="7544a-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7544a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7544a-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7544a-115">Child Elements</span></span>  
  
|<span data-ttu-id="7544a-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="7544a-116">Element</span></span>|<span data-ttu-id="7544a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7544a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7544a-118">\<states></span><span class="sxs-lookup"><span data-stu-id="7544a-118">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="7544a-119">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="7544a-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7544a-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7544a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7544a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="7544a-121">Element</span></span>|<span data-ttu-id="7544a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="7544a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7544a-123">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7544a-123">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="7544a-124">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="7544a-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7544a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7544a-125">Remarks</span></span>  
 <span data-ttu-id="7544a-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="7544a-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="7544a-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7544a-127">Example</span></span>  
 <span data-ttu-id="7544a-128">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="7544a-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7544a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7544a-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7544a-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7544a-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7544a-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7544a-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
