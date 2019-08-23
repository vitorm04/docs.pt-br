---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947401"
---
# <a name="states"></a><span data-ttu-id="4987a-101">\<> de Estados</span><span class="sxs-lookup"><span data-stu-id="4987a-101">\<states></span></span>
<span data-ttu-id="4987a-102">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="4987a-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="4987a-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4987a-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4987a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4987a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4987a-105">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="4987a-105">\<tracking></span></span>  
<span data-ttu-id="4987a-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4987a-106">\<trackingProfile></span></span>  
<span data-ttu-id="4987a-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4987a-107">\<workflow></span></span>  
<span data-ttu-id="4987a-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="4987a-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="4987a-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4987a-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="4987a-110">\<> de Estados</span><span class="sxs-lookup"><span data-stu-id="4987a-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4987a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4987a-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4987a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4987a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4987a-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4987a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4987a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4987a-114">Attributes</span></span>  
 <span data-ttu-id="4987a-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4987a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4987a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4987a-116">Child Elements</span></span>  
  
|<span data-ttu-id="4987a-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4987a-117">Element</span></span>|<span data-ttu-id="4987a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4987a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4987a-119">\<state></span><span class="sxs-lookup"><span data-stu-id="4987a-119">\<state></span></span>](states.md)|<span data-ttu-id="4987a-120">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="4987a-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4987a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4987a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4987a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4987a-122">Element</span></span>|<span data-ttu-id="4987a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4987a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4987a-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4987a-124">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="4987a-125">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="4987a-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4987a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4987a-126">Remarks</span></span>  
 <span data-ttu-id="4987a-127">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="4987a-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="4987a-128">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4987a-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="4987a-129">Estado</span><span class="sxs-lookup"><span data-stu-id="4987a-129">State</span></span>|<span data-ttu-id="4987a-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="4987a-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4987a-131">Anulado</span><span class="sxs-lookup"><span data-stu-id="4987a-131">Aborted</span></span>|<span data-ttu-id="4987a-132">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="4987a-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="4987a-133">Concluído</span><span class="sxs-lookup"><span data-stu-id="4987a-133">Completed</span></span>|<span data-ttu-id="4987a-134">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="4987a-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="4987a-135">Deleted</span><span class="sxs-lookup"><span data-stu-id="4987a-135">Deleted</span></span>|<span data-ttu-id="4987a-136">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="4987a-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="4987a-137">Ocioso</span><span class="sxs-lookup"><span data-stu-id="4987a-137">Idle</span></span>|<span data-ttu-id="4987a-138">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="4987a-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="4987a-139">Persistentes</span><span class="sxs-lookup"><span data-stu-id="4987a-139">Persisted</span></span>|<span data-ttu-id="4987a-140">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="4987a-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="4987a-141">Retomada</span><span class="sxs-lookup"><span data-stu-id="4987a-141">Resumed</span></span>|<span data-ttu-id="4987a-142">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="4987a-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="4987a-143">Introdução</span><span class="sxs-lookup"><span data-stu-id="4987a-143">Started</span></span>|<span data-ttu-id="4987a-144">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="4987a-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="4987a-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="4987a-145">UnhandledException</span></span>|<span data-ttu-id="4987a-146">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="4987a-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="4987a-147">Descarregado</span><span class="sxs-lookup"><span data-stu-id="4987a-147">Unloaded</span></span>|<span data-ttu-id="4987a-148">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="4987a-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="4987a-149">Cancelado</span><span class="sxs-lookup"><span data-stu-id="4987a-149">Canceled</span></span>|<span data-ttu-id="4987a-150">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="4987a-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="4987a-151">Suspenso</span><span class="sxs-lookup"><span data-stu-id="4987a-151">Suspended</span></span>|<span data-ttu-id="4987a-152">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="4987a-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="4987a-153">Encerrada</span><span class="sxs-lookup"><span data-stu-id="4987a-153">Terminated</span></span>|<span data-ttu-id="4987a-154">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="4987a-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="4987a-155">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="4987a-155">Unsuspended</span></span>|<span data-ttu-id="4987a-156">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="4987a-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4987a-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4987a-157">Example</span></span>  
 <span data-ttu-id="4987a-158">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="4987a-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4987a-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4987a-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4987a-160">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4987a-160">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4987a-161">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4987a-161">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
