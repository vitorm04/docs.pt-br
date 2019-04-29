---
title: <states> of WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: fad6f9c8871f79e4a1e26c893eed86ba168f6d01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757944"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="84bb7-102">\<estados > do WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="84bb7-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="84bb7-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="84bb7-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="84bb7-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="84bb7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="84bb7-105">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="84bb7-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="84bb7-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="84bb7-106">\<profiles></span></span>  
<span data-ttu-id="84bb7-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="84bb7-107">\<trackingProfile></span></span>  
<span data-ttu-id="84bb7-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="84bb7-108">\<workflow></span></span>  
<span data-ttu-id="84bb7-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="84bb7-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="84bb7-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="84bb7-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="84bb7-111">\<states></span><span class="sxs-lookup"><span data-stu-id="84bb7-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84bb7-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84bb7-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84bb7-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84bb7-113">Attributes and elements</span></span>

<span data-ttu-id="84bb7-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84bb7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84bb7-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="84bb7-115">Attributes</span></span>  

<span data-ttu-id="84bb7-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="84bb7-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84bb7-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84bb7-117">Child elements</span></span>
  
|<span data-ttu-id="84bb7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="84bb7-118">Element</span></span>|<span data-ttu-id="84bb7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="84bb7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84bb7-120">\<states></span><span class="sxs-lookup"><span data-stu-id="84bb7-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="84bb7-121">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="84bb7-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84bb7-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84bb7-122">Parent elements</span></span>  
  
|<span data-ttu-id="84bb7-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="84bb7-123">Element</span></span>|<span data-ttu-id="84bb7-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="84bb7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84bb7-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="84bb7-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="84bb7-126">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="84bb7-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84bb7-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="84bb7-127">Remarks</span></span>

<span data-ttu-id="84bb7-128">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="84bb7-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="84bb7-129">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="84bb7-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="84bb7-130">Estado</span><span class="sxs-lookup"><span data-stu-id="84bb7-130">State</span></span>|<span data-ttu-id="84bb7-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="84bb7-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84bb7-132">Anulado</span><span class="sxs-lookup"><span data-stu-id="84bb7-132">Aborted</span></span>|<span data-ttu-id="84bb7-133">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="84bb7-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="84bb7-134">Concluído</span><span class="sxs-lookup"><span data-stu-id="84bb7-134">Completed</span></span>|<span data-ttu-id="84bb7-135">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="84bb7-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="84bb7-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="84bb7-136">Deleted</span></span>|<span data-ttu-id="84bb7-137">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="84bb7-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="84bb7-138">Ocioso</span><span class="sxs-lookup"><span data-stu-id="84bb7-138">Idle</span></span>|<span data-ttu-id="84bb7-139">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="84bb7-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="84bb7-140">Persistentes</span><span class="sxs-lookup"><span data-stu-id="84bb7-140">Persisted</span></span>|<span data-ttu-id="84bb7-141">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="84bb7-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="84bb7-142">Retomada</span><span class="sxs-lookup"><span data-stu-id="84bb7-142">Resumed</span></span>|<span data-ttu-id="84bb7-143">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="84bb7-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="84bb7-144">Introdução</span><span class="sxs-lookup"><span data-stu-id="84bb7-144">Started</span></span>|<span data-ttu-id="84bb7-145">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="84bb7-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="84bb7-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="84bb7-146">UnhandledException</span></span>|<span data-ttu-id="84bb7-147">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="84bb7-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="84bb7-148">Descarregado</span><span class="sxs-lookup"><span data-stu-id="84bb7-148">Unloaded</span></span>|<span data-ttu-id="84bb7-149">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="84bb7-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="84bb7-150">Cancelado</span><span class="sxs-lookup"><span data-stu-id="84bb7-150">Canceled</span></span>|<span data-ttu-id="84bb7-151">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="84bb7-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="84bb7-152">Suspenso</span><span class="sxs-lookup"><span data-stu-id="84bb7-152">Suspended</span></span>|<span data-ttu-id="84bb7-153">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="84bb7-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="84bb7-154">Encerrada</span><span class="sxs-lookup"><span data-stu-id="84bb7-154">Terminated</span></span>|<span data-ttu-id="84bb7-155">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="84bb7-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="84bb7-156">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="84bb7-156">Unsuspended</span></span>|<span data-ttu-id="84bb7-157">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="84bb7-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="84bb7-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84bb7-158">Example</span></span>

<span data-ttu-id="84bb7-159">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="84bb7-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="84bb7-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84bb7-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="84bb7-161">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="84bb7-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="84bb7-162">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="84bb7-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
