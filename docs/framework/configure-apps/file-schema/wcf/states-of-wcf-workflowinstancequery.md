---
title: '&lt;estados&gt; do WCF, &lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb2a277759904a415316e29ba8151f7c1a0f475d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="c7f58-102">&lt;estados&gt; do WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="c7f58-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="c7f58-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="c7f58-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="c7f58-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c7f58-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="c7f58-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c7f58-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c7f58-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="c7f58-106">\<tracking></span></span>  
<span data-ttu-id="c7f58-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c7f58-107">\<trackingProfile></span></span>  
<span data-ttu-id="c7f58-108">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="c7f58-108">\<workflow></span></span>  
<span data-ttu-id="c7f58-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="c7f58-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="c7f58-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="c7f58-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="c7f58-111">\<estados ></span><span class="sxs-lookup"><span data-stu-id="c7f58-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f58-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7f58-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7f58-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c7f58-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c7f58-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c7f58-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7f58-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="c7f58-115">Attributes</span></span>  
 <span data-ttu-id="c7f58-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c7f58-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7f58-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c7f58-117">Child Elements</span></span>  
  
|<span data-ttu-id="c7f58-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7f58-118">Element</span></span>|<span data-ttu-id="c7f58-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7f58-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7f58-120">\<estados ></span><span class="sxs-lookup"><span data-stu-id="c7f58-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="c7f58-121">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="c7f58-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7f58-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c7f58-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c7f58-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7f58-123">Element</span></span>|<span data-ttu-id="c7f58-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7f58-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7f58-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="c7f58-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="c7f58-126">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="c7f58-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7f58-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7f58-127">Remarks</span></span>  
 <span data-ttu-id="c7f58-128">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="c7f58-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="c7f58-129">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7f58-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="c7f58-130">Estado</span><span class="sxs-lookup"><span data-stu-id="c7f58-130">State</span></span>|<span data-ttu-id="c7f58-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7f58-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c7f58-132">Anulado</span><span class="sxs-lookup"><span data-stu-id="c7f58-132">Aborted</span></span>|<span data-ttu-id="c7f58-133">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="c7f58-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c7f58-134">Concluído</span><span class="sxs-lookup"><span data-stu-id="c7f58-134">Completed</span></span>|<span data-ttu-id="c7f58-135">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="c7f58-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="c7f58-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="c7f58-136">Deleted</span></span>|<span data-ttu-id="c7f58-137">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="c7f58-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="c7f58-138">Ocioso</span><span class="sxs-lookup"><span data-stu-id="c7f58-138">Idle</span></span>|<span data-ttu-id="c7f58-139">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="c7f58-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="c7f58-140">Persistentes</span><span class="sxs-lookup"><span data-stu-id="c7f58-140">Persisted</span></span>|<span data-ttu-id="c7f58-141">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="c7f58-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="c7f58-142">Retomada</span><span class="sxs-lookup"><span data-stu-id="c7f58-142">Resumed</span></span>|<span data-ttu-id="c7f58-143">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="c7f58-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c7f58-144">Introdução</span><span class="sxs-lookup"><span data-stu-id="c7f58-144">Started</span></span>|<span data-ttu-id="c7f58-145">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="c7f58-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="c7f58-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="c7f58-146">UnhandledException</span></span>|<span data-ttu-id="c7f58-147">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="c7f58-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="c7f58-148">Descarregado</span><span class="sxs-lookup"><span data-stu-id="c7f58-148">Unloaded</span></span>|<span data-ttu-id="c7f58-149">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="c7f58-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="c7f58-150">Cancelado</span><span class="sxs-lookup"><span data-stu-id="c7f58-150">Canceled</span></span>|<span data-ttu-id="c7f58-151">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="c7f58-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="c7f58-152">Suspenso</span><span class="sxs-lookup"><span data-stu-id="c7f58-152">Suspended</span></span>|<span data-ttu-id="c7f58-153">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="c7f58-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="c7f58-154">Encerrada</span><span class="sxs-lookup"><span data-stu-id="c7f58-154">Terminated</span></span>|<span data-ttu-id="c7f58-155">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="c7f58-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="c7f58-156">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="c7f58-156">Unsuspended</span></span>|<span data-ttu-id="c7f58-157">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="c7f58-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7f58-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7f58-158">Example</span></span>  
 <span data-ttu-id="c7f58-159">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="c7f58-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7f58-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7f58-160">See Also</span></span>  
 <span data-ttu-id="c7f58-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c7f58-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c7f58-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c7f58-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c7f58-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c7f58-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="c7f58-164">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c7f58-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c7f58-165">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c7f58-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
