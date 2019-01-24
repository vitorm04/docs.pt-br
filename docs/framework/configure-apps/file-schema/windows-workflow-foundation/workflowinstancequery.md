---
title: '&lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: bef9ddcee2e373f4588d6aed06b7c51e4c6ed4b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662043"
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="4ad27-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="4ad27-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="4ad27-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="4ad27-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="4ad27-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4ad27-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4ad27-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ad27-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4ad27-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="4ad27-106">\<tracking></span></span>  
<span data-ttu-id="4ad27-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4ad27-107">\<trackingProfile></span></span>  
<span data-ttu-id="4ad27-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4ad27-108">\<workflow></span></span>  
<span data-ttu-id="4ad27-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="4ad27-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="4ad27-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4ad27-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad27-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ad27-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ad27-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4ad27-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4ad27-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4ad27-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ad27-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4ad27-114">Attributes</span></span>  
 <span data-ttu-id="4ad27-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4ad27-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ad27-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4ad27-116">Child Elements</span></span>  
  
|<span data-ttu-id="4ad27-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4ad27-117">Element</span></span>|<span data-ttu-id="4ad27-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ad27-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad27-119">\<states></span><span class="sxs-lookup"><span data-stu-id="4ad27-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="4ad27-120">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="4ad27-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ad27-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4ad27-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4ad27-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4ad27-122">Element</span></span>|<span data-ttu-id="4ad27-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ad27-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad27-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="4ad27-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="4ad27-125">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="4ad27-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad27-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ad27-126">Remarks</span></span>  
 <span data-ttu-id="4ad27-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="4ad27-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4ad27-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ad27-128">Example</span></span>  
 <span data-ttu-id="4ad27-129">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="4ad27-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ad27-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ad27-130">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4ad27-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4ad27-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4ad27-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4ad27-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
