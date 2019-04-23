---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 30cb2efa4c00c8b292a8ace6a03306d6ac76a7f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073116"
---
# <a name="states"></a><span data-ttu-id="3cd6d-101">\<states></span><span class="sxs-lookup"><span data-stu-id="3cd6d-101">\<states></span></span>
<span data-ttu-id="3cd6d-102">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="3cd6d-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3cd6d-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3cd6d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3cd6d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3cd6d-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3cd6d-105">\<tracking></span></span>  
<span data-ttu-id="3cd6d-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3cd6d-106">\<trackingProfile></span></span>  
<span data-ttu-id="3cd6d-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3cd6d-107">\<workflow></span></span>  
<span data-ttu-id="3cd6d-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="3cd6d-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="3cd6d-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="3cd6d-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="3cd6d-110">\<states></span><span class="sxs-lookup"><span data-stu-id="3cd6d-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd6d-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3cd6d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cd6d-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3cd6d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3cd6d-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cd6d-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="3cd6d-114">Attributes</span></span>  
 <span data-ttu-id="3cd6d-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3cd6d-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3cd6d-116">Child Elements</span></span>  
  
|<span data-ttu-id="3cd6d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cd6d-117">Element</span></span>|<span data-ttu-id="3cd6d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cd6d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cd6d-119">\<state></span><span class="sxs-lookup"><span data-stu-id="3cd6d-119">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="3cd6d-120">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3cd6d-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3cd6d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3cd6d-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cd6d-122">Element</span></span>|<span data-ttu-id="3cd6d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cd6d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cd6d-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="3cd6d-124">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="3cd6d-125">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cd6d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="3cd6d-126">Remarks</span></span>  
 <span data-ttu-id="3cd6d-127">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="3cd6d-128">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="3cd6d-129">Estado</span><span class="sxs-lookup"><span data-stu-id="3cd6d-129">State</span></span>|<span data-ttu-id="3cd6d-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cd6d-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3cd6d-131">Anulado</span><span class="sxs-lookup"><span data-stu-id="3cd6d-131">Aborted</span></span>|<span data-ttu-id="3cd6d-132">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="3cd6d-133">Concluído</span><span class="sxs-lookup"><span data-stu-id="3cd6d-133">Completed</span></span>|<span data-ttu-id="3cd6d-134">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="3cd6d-135">Deleted</span><span class="sxs-lookup"><span data-stu-id="3cd6d-135">Deleted</span></span>|<span data-ttu-id="3cd6d-136">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="3cd6d-137">Ocioso</span><span class="sxs-lookup"><span data-stu-id="3cd6d-137">Idle</span></span>|<span data-ttu-id="3cd6d-138">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="3cd6d-139">Persistentes</span><span class="sxs-lookup"><span data-stu-id="3cd6d-139">Persisted</span></span>|<span data-ttu-id="3cd6d-140">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="3cd6d-141">Retomada</span><span class="sxs-lookup"><span data-stu-id="3cd6d-141">Resumed</span></span>|<span data-ttu-id="3cd6d-142">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="3cd6d-143">Introdução</span><span class="sxs-lookup"><span data-stu-id="3cd6d-143">Started</span></span>|<span data-ttu-id="3cd6d-144">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="3cd6d-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="3cd6d-145">UnhandledException</span></span>|<span data-ttu-id="3cd6d-146">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="3cd6d-147">Descarregado</span><span class="sxs-lookup"><span data-stu-id="3cd6d-147">Unloaded</span></span>|<span data-ttu-id="3cd6d-148">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="3cd6d-149">Cancelado</span><span class="sxs-lookup"><span data-stu-id="3cd6d-149">Canceled</span></span>|<span data-ttu-id="3cd6d-150">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="3cd6d-151">Suspenso</span><span class="sxs-lookup"><span data-stu-id="3cd6d-151">Suspended</span></span>|<span data-ttu-id="3cd6d-152">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="3cd6d-153">Encerrada</span><span class="sxs-lookup"><span data-stu-id="3cd6d-153">Terminated</span></span>|<span data-ttu-id="3cd6d-154">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="3cd6d-155">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="3cd6d-155">Unsuspended</span></span>|<span data-ttu-id="3cd6d-156">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3cd6d-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3cd6d-157">Example</span></span>  
 <span data-ttu-id="3cd6d-158">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="3cd6d-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cd6d-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cd6d-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3cd6d-160">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3cd6d-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3cd6d-161">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3cd6d-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
