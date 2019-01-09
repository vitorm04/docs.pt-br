---
title: '&lt;estado&gt; do WCF, &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 168a6980e955f602ee60bff26461f06cb16c836a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145919"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="22ab7-102">&lt;estado&gt; do WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="22ab7-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="22ab7-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="22ab7-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="22ab7-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="22ab7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="22ab7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="22ab7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="22ab7-106">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="22ab7-106">\<tracking></span></span>  
<span data-ttu-id="22ab7-107">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="22ab7-107">\<profiles></span></span>  
<span data-ttu-id="22ab7-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="22ab7-108">\<trackingProfile></span></span>  
<span data-ttu-id="22ab7-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="22ab7-109">\<workflow></span></span>  
<span data-ttu-id="22ab7-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="22ab7-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="22ab7-111">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="22ab7-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="22ab7-112">\<estados ></span><span class="sxs-lookup"><span data-stu-id="22ab7-112">\<states></span></span>  
<span data-ttu-id="22ab7-113">\<estado ></span><span class="sxs-lookup"><span data-stu-id="22ab7-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ab7-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22ab7-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22ab7-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="22ab7-115">Attributes and elements</span></span>

<span data-ttu-id="22ab7-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="22ab7-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="22ab7-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="22ab7-117">Attributes</span></span>

|<span data-ttu-id="22ab7-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="22ab7-118">Attribute</span></span>|<span data-ttu-id="22ab7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="22ab7-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="22ab7-120">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="22ab7-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22ab7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="22ab7-121">Child elements</span></span>

<span data-ttu-id="22ab7-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="22ab7-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22ab7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="22ab7-123">Parent elements</span></span>

|<span data-ttu-id="22ab7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="22ab7-124">Element</span></span>|<span data-ttu-id="22ab7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="22ab7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22ab7-126">\<estados ></span><span class="sxs-lookup"><span data-stu-id="22ab7-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="22ab7-127">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="22ab7-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22ab7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="22ab7-128">Remarks</span></span>  

<span data-ttu-id="22ab7-129">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="22ab7-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="22ab7-130">Estado de possíveis valores é descritos na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="22ab7-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="22ab7-131">Estado</span><span class="sxs-lookup"><span data-stu-id="22ab7-131">State</span></span>|<span data-ttu-id="22ab7-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="22ab7-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22ab7-133">Anulado</span><span class="sxs-lookup"><span data-stu-id="22ab7-133">Aborted</span></span>|<span data-ttu-id="22ab7-134">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="22ab7-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="22ab7-135">Concluído</span><span class="sxs-lookup"><span data-stu-id="22ab7-135">Completed</span></span>|<span data-ttu-id="22ab7-136">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="22ab7-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="22ab7-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="22ab7-137">Deleted</span></span>|<span data-ttu-id="22ab7-138">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="22ab7-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="22ab7-139">Ocioso</span><span class="sxs-lookup"><span data-stu-id="22ab7-139">Idle</span></span>|<span data-ttu-id="22ab7-140">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="22ab7-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="22ab7-141">Persistentes</span><span class="sxs-lookup"><span data-stu-id="22ab7-141">Persisted</span></span>|<span data-ttu-id="22ab7-142">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="22ab7-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="22ab7-143">Retomada</span><span class="sxs-lookup"><span data-stu-id="22ab7-143">Resumed</span></span>|<span data-ttu-id="22ab7-144">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="22ab7-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="22ab7-145">Introdução</span><span class="sxs-lookup"><span data-stu-id="22ab7-145">Started</span></span>|<span data-ttu-id="22ab7-146">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="22ab7-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="22ab7-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="22ab7-147">UnhandledException</span></span>|<span data-ttu-id="22ab7-148">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="22ab7-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="22ab7-149">Descarregado</span><span class="sxs-lookup"><span data-stu-id="22ab7-149">Unloaded</span></span>|<span data-ttu-id="22ab7-150">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="22ab7-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="22ab7-151">Cancelado</span><span class="sxs-lookup"><span data-stu-id="22ab7-151">Canceled</span></span>|<span data-ttu-id="22ab7-152">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="22ab7-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="22ab7-153">Suspenso</span><span class="sxs-lookup"><span data-stu-id="22ab7-153">Suspended</span></span>|<span data-ttu-id="22ab7-154">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="22ab7-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="22ab7-155">Encerrada</span><span class="sxs-lookup"><span data-stu-id="22ab7-155">Terminated</span></span>|<span data-ttu-id="22ab7-156">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="22ab7-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="22ab7-157">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="22ab7-157">Unsuspended</span></span>|<span data-ttu-id="22ab7-158">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="22ab7-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="22ab7-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22ab7-159">Example</span></span>

<span data-ttu-id="22ab7-160">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="22ab7-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="22ab7-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22ab7-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="22ab7-162">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="22ab7-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="22ab7-163">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="22ab7-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
