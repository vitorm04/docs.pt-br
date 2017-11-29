---
title: '&lt;workflowInstanceQuery&gt; of WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 413e341c31b5312d2d772a901965c3917d05e44f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="4f2fe-102">&lt;workflowInstanceQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="4f2fe-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="4f2fe-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="4f2fe-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="4f2fe-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4f2fe-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="4f2fe-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4f2fe-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-106">\<tracking></span></span>  
<span data-ttu-id="4f2fe-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-107">\<trackingProfile></span></span>  
<span data-ttu-id="4f2fe-108">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-108">\<workflow></span></span>  
<span data-ttu-id="4f2fe-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="4f2fe-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2fe-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f2fe-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f2fe-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f2fe-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f2fe-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f2fe-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f2fe-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f2fe-114">Attributes</span></span>  
 <span data-ttu-id="4f2fe-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4f2fe-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f2fe-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f2fe-116">Child Elements</span></span>  
  
|<span data-ttu-id="4f2fe-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f2fe-117">Element</span></span>|<span data-ttu-id="4f2fe-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f2fe-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f2fe-119">\<estados ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="4f2fe-120">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="4f2fe-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f2fe-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f2fe-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4f2fe-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f2fe-122">Element</span></span>|<span data-ttu-id="4f2fe-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f2fe-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f2fe-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="4f2fe-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="4f2fe-125">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="4f2fe-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f2fe-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f2fe-126">Remarks</span></span>  
 <span data-ttu-id="4f2fe-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="4f2fe-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4f2fe-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f2fe-128">Example</span></span>  
 <span data-ttu-id="4f2fe-129">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="4f2fe-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f2fe-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f2fe-130">See Also</span></span>  
 <span data-ttu-id="4f2fe-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4f2fe-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4f2fe-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4f2fe-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="4f2fe-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f2fe-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4f2fe-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4f2fe-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
