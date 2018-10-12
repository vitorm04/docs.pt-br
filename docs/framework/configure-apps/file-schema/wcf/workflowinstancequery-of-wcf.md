---
title: '&lt;workflowInstanceQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 447564e46e5e74432802341d9f63adbb72667ab4
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123300"
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="3bdc6-102">&lt;workflowInstanceQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="3bdc6-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>

<span data-ttu-id="3bdc6-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="3bdc6-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="3bdc6-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3bdc6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3bdc6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3bdc6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3bdc6-106">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="3bdc6-106">\<tracking></span></span>  
<span data-ttu-id="3bdc6-107">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="3bdc6-107">\<profiles></span></span>  
<span data-ttu-id="3bdc6-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3bdc6-108">\<trackingProfile></span></span>  
<span data-ttu-id="3bdc6-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3bdc6-109">\<workflow></span></span>  
<span data-ttu-id="3bdc6-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="3bdc6-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="3bdc6-111">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="3bdc6-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdc6-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bdc6-112">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3bdc6-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3bdc6-113">Attributes and elements</span></span>  

<span data-ttu-id="3bdc6-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3bdc6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bdc6-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="3bdc6-115">Attributes</span></span>  

<span data-ttu-id="3bdc6-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3bdc6-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3bdc6-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3bdc6-117">Child elements</span></span>  
  
|<span data-ttu-id="3bdc6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bdc6-118">Element</span></span>|<span data-ttu-id="3bdc6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bdc6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bdc6-120">\<estados ></span><span class="sxs-lookup"><span data-stu-id="3bdc6-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="3bdc6-121">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="3bdc6-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3bdc6-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3bdc6-122">Parent elements</span></span>  
  
|<span data-ttu-id="3bdc6-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bdc6-123">Element</span></span>|<span data-ttu-id="3bdc6-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bdc6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bdc6-125">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="3bdc6-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="3bdc6-126">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="3bdc6-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bdc6-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bdc6-127">Remarks</span></span>  

<span data-ttu-id="3bdc6-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="3bdc6-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="3bdc6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bdc6-129">Example</span></span>  

<span data-ttu-id="3bdc6-130">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="3bdc6-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bdc6-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bdc6-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3bdc6-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3bdc6-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3bdc6-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3bdc6-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
