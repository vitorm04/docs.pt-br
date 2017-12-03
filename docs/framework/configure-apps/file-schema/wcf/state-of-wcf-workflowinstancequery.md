---
title: '&lt;estado&gt; do WCF, &lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d6edb83370f36b73955ab9d619c8b956f36a007e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="adf9a-102">&lt;estado&gt; do WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="adf9a-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="adf9a-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="adf9a-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="adf9a-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="adf9a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="adf9a-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="adf9a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="adf9a-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="adf9a-106">\<tracking></span></span>  
<span data-ttu-id="adf9a-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="adf9a-107">\<trackingProfile></span></span>  
<span data-ttu-id="adf9a-108">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="adf9a-108">\<workflow></span></span>  
<span data-ttu-id="adf9a-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="adf9a-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="adf9a-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="adf9a-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="adf9a-111">\<estados ></span><span class="sxs-lookup"><span data-stu-id="adf9a-111">\<states></span></span>  
<span data-ttu-id="adf9a-112">\<estado ></span><span class="sxs-lookup"><span data-stu-id="adf9a-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf9a-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adf9a-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adf9a-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="adf9a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="adf9a-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="adf9a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adf9a-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="adf9a-116">Attributes</span></span>  
  
|<span data-ttu-id="adf9a-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="adf9a-117">Attribute</span></span>|<span data-ttu-id="adf9a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf9a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adf9a-119">name</span><span class="sxs-lookup"><span data-stu-id="adf9a-119">name</span></span>|<span data-ttu-id="adf9a-120">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="adf9a-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adf9a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="adf9a-121">Child Elements</span></span>  
 <span data-ttu-id="adf9a-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="adf9a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adf9a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="adf9a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="adf9a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="adf9a-124">Element</span></span>|<span data-ttu-id="adf9a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf9a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adf9a-126">\<estados ></span><span class="sxs-lookup"><span data-stu-id="adf9a-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="adf9a-127">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="adf9a-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adf9a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="adf9a-128">Remarks</span></span>  
 <span data-ttu-id="adf9a-129">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="adf9a-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="adf9a-130">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="adf9a-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="adf9a-131">Estado</span><span class="sxs-lookup"><span data-stu-id="adf9a-131">State</span></span>|<span data-ttu-id="adf9a-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf9a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="adf9a-133">Anulado</span><span class="sxs-lookup"><span data-stu-id="adf9a-133">Aborted</span></span>|<span data-ttu-id="adf9a-134">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="adf9a-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="adf9a-135">Concluído</span><span class="sxs-lookup"><span data-stu-id="adf9a-135">Completed</span></span>|<span data-ttu-id="adf9a-136">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="adf9a-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="adf9a-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="adf9a-137">Deleted</span></span>|<span data-ttu-id="adf9a-138">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="adf9a-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="adf9a-139">Ocioso</span><span class="sxs-lookup"><span data-stu-id="adf9a-139">Idle</span></span>|<span data-ttu-id="adf9a-140">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="adf9a-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="adf9a-141">Persistentes</span><span class="sxs-lookup"><span data-stu-id="adf9a-141">Persisted</span></span>|<span data-ttu-id="adf9a-142">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="adf9a-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="adf9a-143">Retomada</span><span class="sxs-lookup"><span data-stu-id="adf9a-143">Resumed</span></span>|<span data-ttu-id="adf9a-144">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="adf9a-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="adf9a-145">Introdução</span><span class="sxs-lookup"><span data-stu-id="adf9a-145">Started</span></span>|<span data-ttu-id="adf9a-146">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="adf9a-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="adf9a-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="adf9a-147">UnhandledException</span></span>|<span data-ttu-id="adf9a-148">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="adf9a-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="adf9a-149">Descarregado</span><span class="sxs-lookup"><span data-stu-id="adf9a-149">Unloaded</span></span>|<span data-ttu-id="adf9a-150">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="adf9a-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="adf9a-151">Cancelado</span><span class="sxs-lookup"><span data-stu-id="adf9a-151">Canceled</span></span>|<span data-ttu-id="adf9a-152">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="adf9a-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="adf9a-153">Suspenso</span><span class="sxs-lookup"><span data-stu-id="adf9a-153">Suspended</span></span>|<span data-ttu-id="adf9a-154">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="adf9a-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="adf9a-155">Encerrada</span><span class="sxs-lookup"><span data-stu-id="adf9a-155">Terminated</span></span>|<span data-ttu-id="adf9a-156">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="adf9a-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="adf9a-157">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="adf9a-157">Unsuspended</span></span>|<span data-ttu-id="adf9a-158">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="adf9a-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="adf9a-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adf9a-159">Example</span></span>  
 <span data-ttu-id="adf9a-160">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="adf9a-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adf9a-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adf9a-161">See Also</span></span>  
 <span data-ttu-id="adf9a-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="adf9a-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="adf9a-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="adf9a-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="adf9a-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="adf9a-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="adf9a-165">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="adf9a-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="adf9a-166">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="adf9a-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
