---
title: '&lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: eb8b84f70025df3a8a8ac96f61dec6755eb3a364
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757834"
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="80b93-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="80b93-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="80b93-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="80b93-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="80b93-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="80b93-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="80b93-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="80b93-105">\<system.serviceModel></span></span>  
<span data-ttu-id="80b93-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="80b93-106">\<tracking></span></span>  
<span data-ttu-id="80b93-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="80b93-107">\<trackingProfile></span></span>  
<span data-ttu-id="80b93-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="80b93-108">\<workflow></span></span>  
<span data-ttu-id="80b93-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="80b93-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="80b93-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="80b93-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80b93-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80b93-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80b93-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80b93-112">Attributes and Elements</span></span>  
 <span data-ttu-id="80b93-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="80b93-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80b93-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="80b93-114">Attributes</span></span>  
 <span data-ttu-id="80b93-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="80b93-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80b93-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80b93-116">Child Elements</span></span>  
  
|<span data-ttu-id="80b93-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="80b93-117">Element</span></span>|<span data-ttu-id="80b93-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="80b93-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80b93-119">\<estados ></span><span class="sxs-lookup"><span data-stu-id="80b93-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="80b93-120">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="80b93-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80b93-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80b93-121">Parent Elements</span></span>  
  
|<span data-ttu-id="80b93-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="80b93-122">Element</span></span>|<span data-ttu-id="80b93-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="80b93-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80b93-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="80b93-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="80b93-125">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="80b93-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80b93-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="80b93-126">Remarks</span></span>  
 <span data-ttu-id="80b93-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="80b93-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="80b93-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80b93-128">Example</span></span>  
 <span data-ttu-id="80b93-129">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="80b93-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80b93-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80b93-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="80b93-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="80b93-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="80b93-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="80b93-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
