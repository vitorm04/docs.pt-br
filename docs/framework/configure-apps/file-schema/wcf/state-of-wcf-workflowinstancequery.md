---
title: <state>do WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 99387a8f60e96beb2ec7706d9abf4bb6ae84b868
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938216"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="76a72-102">\<Estado > do WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="76a72-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="76a72-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="76a72-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="76a72-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="76a72-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="76a72-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="76a72-105">\<system.serviceModel></span></span>  
<span data-ttu-id="76a72-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="76a72-106">\<tracking></span></span>  
<span data-ttu-id="76a72-107">\<perfis ></span><span class="sxs-lookup"><span data-stu-id="76a72-107">\<profiles></span></span>  
<span data-ttu-id="76a72-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="76a72-108">\<trackingProfile></span></span>  
<span data-ttu-id="76a72-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="76a72-109">\<workflow></span></span>  
<span data-ttu-id="76a72-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="76a72-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="76a72-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="76a72-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="76a72-112">\<> de Estados</span><span class="sxs-lookup"><span data-stu-id="76a72-112">\<states></span></span>  
<span data-ttu-id="76a72-113">\<state></span><span class="sxs-lookup"><span data-stu-id="76a72-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a72-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76a72-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76a72-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="76a72-115">Attributes and elements</span></span>

<span data-ttu-id="76a72-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="76a72-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="76a72-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="76a72-117">Attributes</span></span>

|<span data-ttu-id="76a72-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="76a72-118">Attribute</span></span>|<span data-ttu-id="76a72-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="76a72-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="76a72-120">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="76a72-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76a72-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="76a72-121">Child elements</span></span>

<span data-ttu-id="76a72-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="76a72-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76a72-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="76a72-123">Parent elements</span></span>

|<span data-ttu-id="76a72-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="76a72-124">Element</span></span>|<span data-ttu-id="76a72-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="76a72-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76a72-126">\<states></span><span class="sxs-lookup"><span data-stu-id="76a72-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="76a72-127">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="76a72-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76a72-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="76a72-128">Remarks</span></span>  

<span data-ttu-id="76a72-129">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="76a72-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="76a72-130">Os valores de estado possíveis são descritos na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="76a72-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="76a72-131">Estado</span><span class="sxs-lookup"><span data-stu-id="76a72-131">State</span></span>|<span data-ttu-id="76a72-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="76a72-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76a72-133">Anulado</span><span class="sxs-lookup"><span data-stu-id="76a72-133">Aborted</span></span>|<span data-ttu-id="76a72-134">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="76a72-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="76a72-135">Concluído</span><span class="sxs-lookup"><span data-stu-id="76a72-135">Completed</span></span>|<span data-ttu-id="76a72-136">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="76a72-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="76a72-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="76a72-137">Deleted</span></span>|<span data-ttu-id="76a72-138">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="76a72-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="76a72-139">Ocioso</span><span class="sxs-lookup"><span data-stu-id="76a72-139">Idle</span></span>|<span data-ttu-id="76a72-140">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="76a72-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="76a72-141">Persistentes</span><span class="sxs-lookup"><span data-stu-id="76a72-141">Persisted</span></span>|<span data-ttu-id="76a72-142">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="76a72-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="76a72-143">Retomada</span><span class="sxs-lookup"><span data-stu-id="76a72-143">Resumed</span></span>|<span data-ttu-id="76a72-144">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="76a72-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="76a72-145">Introdução</span><span class="sxs-lookup"><span data-stu-id="76a72-145">Started</span></span>|<span data-ttu-id="76a72-146">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="76a72-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="76a72-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="76a72-147">UnhandledException</span></span>|<span data-ttu-id="76a72-148">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="76a72-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="76a72-149">Descarregado</span><span class="sxs-lookup"><span data-stu-id="76a72-149">Unloaded</span></span>|<span data-ttu-id="76a72-150">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="76a72-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="76a72-151">Cancelado</span><span class="sxs-lookup"><span data-stu-id="76a72-151">Canceled</span></span>|<span data-ttu-id="76a72-152">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="76a72-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="76a72-153">Suspenso</span><span class="sxs-lookup"><span data-stu-id="76a72-153">Suspended</span></span>|<span data-ttu-id="76a72-154">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="76a72-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="76a72-155">Encerrada</span><span class="sxs-lookup"><span data-stu-id="76a72-155">Terminated</span></span>|<span data-ttu-id="76a72-156">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="76a72-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="76a72-157">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="76a72-157">Unsuspended</span></span>|<span data-ttu-id="76a72-158">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="76a72-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76a72-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76a72-159">Example</span></span>

<span data-ttu-id="76a72-160">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="76a72-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="76a72-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76a72-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="76a72-162">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="76a72-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="76a72-163">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="76a72-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
