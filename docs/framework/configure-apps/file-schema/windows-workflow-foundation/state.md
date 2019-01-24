---
title: '&lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 8e381671d9282218a4e5bf0ae979bec79c7cfe78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523045"
---
# <a name="ltstategt"></a><span data-ttu-id="3ad16-102">&lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="3ad16-102">&lt;state&gt;</span></span>
<span data-ttu-id="3ad16-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="3ad16-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="3ad16-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3ad16-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3ad16-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ad16-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3ad16-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3ad16-106">\<tracking></span></span>  
<span data-ttu-id="3ad16-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3ad16-107">\<trackingProfile></span></span>  
<span data-ttu-id="3ad16-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3ad16-108">\<workflow></span></span>  
<span data-ttu-id="3ad16-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="3ad16-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="3ad16-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="3ad16-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="3ad16-111">\<states></span><span class="sxs-lookup"><span data-stu-id="3ad16-111">\<states></span></span>  
<span data-ttu-id="3ad16-112">\<state></span><span class="sxs-lookup"><span data-stu-id="3ad16-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ad16-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ad16-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ad16-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3ad16-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3ad16-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3ad16-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ad16-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ad16-116">Attributes</span></span>  
  
|<span data-ttu-id="3ad16-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="3ad16-117">Attribute</span></span>|<span data-ttu-id="3ad16-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ad16-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ad16-119">name</span><span class="sxs-lookup"><span data-stu-id="3ad16-119">name</span></span>|<span data-ttu-id="3ad16-120">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="3ad16-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ad16-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3ad16-121">Child Elements</span></span>  
 <span data-ttu-id="3ad16-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3ad16-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ad16-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ad16-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3ad16-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ad16-124">Element</span></span>|<span data-ttu-id="3ad16-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ad16-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ad16-126">\<states></span><span class="sxs-lookup"><span data-stu-id="3ad16-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="3ad16-127">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="3ad16-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ad16-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ad16-128">Remarks</span></span>  
 <span data-ttu-id="3ad16-129">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="3ad16-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="3ad16-130">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3ad16-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="3ad16-131">Estado</span><span class="sxs-lookup"><span data-stu-id="3ad16-131">State</span></span>|<span data-ttu-id="3ad16-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ad16-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ad16-133">Anulado</span><span class="sxs-lookup"><span data-stu-id="3ad16-133">Aborted</span></span>|<span data-ttu-id="3ad16-134">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="3ad16-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="3ad16-135">Concluído</span><span class="sxs-lookup"><span data-stu-id="3ad16-135">Completed</span></span>|<span data-ttu-id="3ad16-136">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="3ad16-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="3ad16-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="3ad16-137">Deleted</span></span>|<span data-ttu-id="3ad16-138">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="3ad16-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="3ad16-139">Ocioso</span><span class="sxs-lookup"><span data-stu-id="3ad16-139">Idle</span></span>|<span data-ttu-id="3ad16-140">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="3ad16-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="3ad16-141">Persistentes</span><span class="sxs-lookup"><span data-stu-id="3ad16-141">Persisted</span></span>|<span data-ttu-id="3ad16-142">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="3ad16-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="3ad16-143">Retomada</span><span class="sxs-lookup"><span data-stu-id="3ad16-143">Resumed</span></span>|<span data-ttu-id="3ad16-144">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="3ad16-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="3ad16-145">Introdução</span><span class="sxs-lookup"><span data-stu-id="3ad16-145">Started</span></span>|<span data-ttu-id="3ad16-146">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="3ad16-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="3ad16-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="3ad16-147">UnhandledException</span></span>|<span data-ttu-id="3ad16-148">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="3ad16-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="3ad16-149">Descarregado</span><span class="sxs-lookup"><span data-stu-id="3ad16-149">Unloaded</span></span>|<span data-ttu-id="3ad16-150">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="3ad16-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="3ad16-151">Cancelado</span><span class="sxs-lookup"><span data-stu-id="3ad16-151">Canceled</span></span>|<span data-ttu-id="3ad16-152">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="3ad16-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="3ad16-153">Suspenso</span><span class="sxs-lookup"><span data-stu-id="3ad16-153">Suspended</span></span>|<span data-ttu-id="3ad16-154">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="3ad16-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="3ad16-155">Encerrada</span><span class="sxs-lookup"><span data-stu-id="3ad16-155">Terminated</span></span>|<span data-ttu-id="3ad16-156">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="3ad16-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="3ad16-157">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="3ad16-157">Unsuspended</span></span>|<span data-ttu-id="3ad16-158">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="3ad16-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3ad16-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ad16-159">Example</span></span>  
 <span data-ttu-id="3ad16-160">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="3ad16-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ad16-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ad16-161">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3ad16-162">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3ad16-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3ad16-163">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3ad16-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
