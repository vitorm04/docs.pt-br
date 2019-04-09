---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 6f1a9474f3f12005df364a6fb84dc63aa1b68e04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108154"
---
# <a name="state"></a><span data-ttu-id="52eef-101">\<state></span><span class="sxs-lookup"><span data-stu-id="52eef-101">\<state></span></span>
<span data-ttu-id="52eef-102">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="52eef-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="52eef-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="52eef-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="52eef-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="52eef-104">\<system.serviceModel></span></span>  
<span data-ttu-id="52eef-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="52eef-105">\<tracking></span></span>  
<span data-ttu-id="52eef-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="52eef-106">\<trackingProfile></span></span>  
<span data-ttu-id="52eef-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="52eef-107">\<workflow></span></span>  
<span data-ttu-id="52eef-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="52eef-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="52eef-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="52eef-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="52eef-110">\<states></span><span class="sxs-lookup"><span data-stu-id="52eef-110">\<states></span></span>  
<span data-ttu-id="52eef-111">\<state></span><span class="sxs-lookup"><span data-stu-id="52eef-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52eef-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52eef-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52eef-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="52eef-113">Attributes and Elements</span></span>  
 <span data-ttu-id="52eef-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="52eef-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52eef-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="52eef-115">Attributes</span></span>  
  
|<span data-ttu-id="52eef-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="52eef-116">Attribute</span></span>|<span data-ttu-id="52eef-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="52eef-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52eef-118">name</span><span class="sxs-lookup"><span data-stu-id="52eef-118">name</span></span>|<span data-ttu-id="52eef-119">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="52eef-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52eef-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="52eef-120">Child Elements</span></span>  
 <span data-ttu-id="52eef-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="52eef-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52eef-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="52eef-122">Parent Elements</span></span>  
  
|<span data-ttu-id="52eef-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="52eef-123">Element</span></span>|<span data-ttu-id="52eef-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="52eef-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52eef-125">\<states></span><span class="sxs-lookup"><span data-stu-id="52eef-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="52eef-126">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="52eef-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52eef-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="52eef-127">Remarks</span></span>  
 <span data-ttu-id="52eef-128">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="52eef-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="52eef-129">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="52eef-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="52eef-130">Estado</span><span class="sxs-lookup"><span data-stu-id="52eef-130">State</span></span>|<span data-ttu-id="52eef-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="52eef-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="52eef-132">Anulado</span><span class="sxs-lookup"><span data-stu-id="52eef-132">Aborted</span></span>|<span data-ttu-id="52eef-133">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="52eef-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="52eef-134">Concluído</span><span class="sxs-lookup"><span data-stu-id="52eef-134">Completed</span></span>|<span data-ttu-id="52eef-135">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="52eef-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="52eef-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="52eef-136">Deleted</span></span>|<span data-ttu-id="52eef-137">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="52eef-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="52eef-138">Ocioso</span><span class="sxs-lookup"><span data-stu-id="52eef-138">Idle</span></span>|<span data-ttu-id="52eef-139">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="52eef-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="52eef-140">Persistentes</span><span class="sxs-lookup"><span data-stu-id="52eef-140">Persisted</span></span>|<span data-ttu-id="52eef-141">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="52eef-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="52eef-142">Retomada</span><span class="sxs-lookup"><span data-stu-id="52eef-142">Resumed</span></span>|<span data-ttu-id="52eef-143">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="52eef-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="52eef-144">Introdução</span><span class="sxs-lookup"><span data-stu-id="52eef-144">Started</span></span>|<span data-ttu-id="52eef-145">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="52eef-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="52eef-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="52eef-146">UnhandledException</span></span>|<span data-ttu-id="52eef-147">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="52eef-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="52eef-148">Descarregado</span><span class="sxs-lookup"><span data-stu-id="52eef-148">Unloaded</span></span>|<span data-ttu-id="52eef-149">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="52eef-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="52eef-150">Cancelado</span><span class="sxs-lookup"><span data-stu-id="52eef-150">Canceled</span></span>|<span data-ttu-id="52eef-151">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="52eef-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="52eef-152">Suspenso</span><span class="sxs-lookup"><span data-stu-id="52eef-152">Suspended</span></span>|<span data-ttu-id="52eef-153">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="52eef-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="52eef-154">Encerrada</span><span class="sxs-lookup"><span data-stu-id="52eef-154">Terminated</span></span>|<span data-ttu-id="52eef-155">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="52eef-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="52eef-156">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="52eef-156">Unsuspended</span></span>|<span data-ttu-id="52eef-157">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="52eef-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="52eef-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52eef-158">Example</span></span>  
 <span data-ttu-id="52eef-159">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="52eef-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52eef-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52eef-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="52eef-161">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="52eef-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="52eef-162">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="52eef-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
