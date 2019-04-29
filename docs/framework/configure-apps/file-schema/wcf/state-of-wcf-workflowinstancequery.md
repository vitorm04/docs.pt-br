---
title: <state> of WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 1615c83ffe0735d9e55e822f2651da41d02b1610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757957"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="d9667-102">\<estado > do WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="d9667-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="d9667-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="d9667-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="d9667-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d9667-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d9667-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d9667-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d9667-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d9667-106">\<tracking></span></span>  
<span data-ttu-id="d9667-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="d9667-107">\<profiles></span></span>  
<span data-ttu-id="d9667-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d9667-108">\<trackingProfile></span></span>  
<span data-ttu-id="d9667-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d9667-109">\<workflow></span></span>  
<span data-ttu-id="d9667-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="d9667-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="d9667-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="d9667-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="d9667-112">\<states></span><span class="sxs-lookup"><span data-stu-id="d9667-112">\<states></span></span>  
<span data-ttu-id="d9667-113">\<state></span><span class="sxs-lookup"><span data-stu-id="d9667-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9667-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9667-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9667-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9667-115">Attributes and elements</span></span>

<span data-ttu-id="d9667-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9667-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="d9667-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9667-117">Attributes</span></span>

|<span data-ttu-id="d9667-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="d9667-118">Attribute</span></span>|<span data-ttu-id="d9667-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9667-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d9667-120">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="d9667-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9667-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9667-121">Child elements</span></span>

<span data-ttu-id="d9667-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d9667-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9667-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9667-123">Parent elements</span></span>

|<span data-ttu-id="d9667-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9667-124">Element</span></span>|<span data-ttu-id="d9667-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9667-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9667-126">\<states></span><span class="sxs-lookup"><span data-stu-id="d9667-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="d9667-127">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="d9667-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9667-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9667-128">Remarks</span></span>  

<span data-ttu-id="d9667-129">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="d9667-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="d9667-130">Estado de possíveis valores é descritos na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="d9667-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="d9667-131">Estado</span><span class="sxs-lookup"><span data-stu-id="d9667-131">State</span></span>|<span data-ttu-id="d9667-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9667-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9667-133">Anulado</span><span class="sxs-lookup"><span data-stu-id="d9667-133">Aborted</span></span>|<span data-ttu-id="d9667-134">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="d9667-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d9667-135">Concluído</span><span class="sxs-lookup"><span data-stu-id="d9667-135">Completed</span></span>|<span data-ttu-id="d9667-136">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="d9667-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="d9667-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="d9667-137">Deleted</span></span>|<span data-ttu-id="d9667-138">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="d9667-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="d9667-139">Ocioso</span><span class="sxs-lookup"><span data-stu-id="d9667-139">Idle</span></span>|<span data-ttu-id="d9667-140">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="d9667-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="d9667-141">Persistentes</span><span class="sxs-lookup"><span data-stu-id="d9667-141">Persisted</span></span>|<span data-ttu-id="d9667-142">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="d9667-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="d9667-143">Retomada</span><span class="sxs-lookup"><span data-stu-id="d9667-143">Resumed</span></span>|<span data-ttu-id="d9667-144">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="d9667-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="d9667-145">Introdução</span><span class="sxs-lookup"><span data-stu-id="d9667-145">Started</span></span>|<span data-ttu-id="d9667-146">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="d9667-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="d9667-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="d9667-147">UnhandledException</span></span>|<span data-ttu-id="d9667-148">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="d9667-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="d9667-149">Descarregado</span><span class="sxs-lookup"><span data-stu-id="d9667-149">Unloaded</span></span>|<span data-ttu-id="d9667-150">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="d9667-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="d9667-151">Cancelado</span><span class="sxs-lookup"><span data-stu-id="d9667-151">Canceled</span></span>|<span data-ttu-id="d9667-152">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="d9667-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="d9667-153">Suspenso</span><span class="sxs-lookup"><span data-stu-id="d9667-153">Suspended</span></span>|<span data-ttu-id="d9667-154">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="d9667-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="d9667-155">Encerrada</span><span class="sxs-lookup"><span data-stu-id="d9667-155">Terminated</span></span>|<span data-ttu-id="d9667-156">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="d9667-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="d9667-157">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="d9667-157">Unsuspended</span></span>|<span data-ttu-id="d9667-158">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="d9667-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9667-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9667-159">Example</span></span>

<span data-ttu-id="d9667-160">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="d9667-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="d9667-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9667-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d9667-162">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d9667-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d9667-163">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d9667-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
