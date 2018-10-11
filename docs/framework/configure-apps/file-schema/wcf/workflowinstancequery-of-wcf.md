---
title: '&lt;workflowInstanceQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: bb4b3e37bd8e8e4f47fd7a0cd6d493d985c2536e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087629"
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="a371c-102">&lt;workflowInstanceQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="a371c-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="a371c-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="a371c-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="a371c-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a371c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="a371c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a371c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a371c-106">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="a371c-106">\<tracking></span></span>  
<span data-ttu-id="a371c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a371c-107">\<trackingProfile></span></span>  
<span data-ttu-id="a371c-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a371c-108">\<workflow></span></span>  
<span data-ttu-id="a371c-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="a371c-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="a371c-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="a371c-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a371c-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a371c-111">Syntax</span></span>  
  
```xml
<tracking>
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
</tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a371c-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a371c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a371c-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a371c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a371c-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="a371c-114">Attributes</span></span>  
 <span data-ttu-id="a371c-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a371c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a371c-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a371c-116">Child Elements</span></span>  
  
|<span data-ttu-id="a371c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="a371c-117">Element</span></span>|<span data-ttu-id="a371c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a371c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a371c-119">\<estados ></span><span class="sxs-lookup"><span data-stu-id="a371c-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="a371c-120">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="a371c-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a371c-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a371c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a371c-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a371c-122">Element</span></span>|<span data-ttu-id="a371c-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a371c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a371c-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="a371c-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="a371c-125">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="a371c-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a371c-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="a371c-126">Remarks</span></span>  
 <span data-ttu-id="a371c-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="a371c-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="a371c-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a371c-128">Example</span></span>  
 <span data-ttu-id="a371c-129">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="a371c-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a371c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a371c-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="a371c-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a371c-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a371c-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a371c-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
