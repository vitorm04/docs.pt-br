---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398646"
---
# <a name="state"></a><span data-ttu-id="a46ee-101">\<state></span><span class="sxs-lookup"><span data-stu-id="a46ee-101">\<state></span></span>
<span data-ttu-id="a46ee-102">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="a46ee-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="a46ee-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a46ee-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a46ee-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a46ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a46ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="a46ee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="a46ee-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQueries**](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="a46ee-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQuery**](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="a46ee-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de Estados**](states.md)</span><span class="sxs-lookup"><span data-stu-id="a46ee-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)</span></span>\
<span data-ttu-id="a46ee-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Estado >**</span><span class="sxs-lookup"><span data-stu-id="a46ee-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a46ee-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a46ee-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a46ee-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a46ee-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a46ee-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a46ee-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a46ee-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="a46ee-116">Attributes</span></span>  
  
|<span data-ttu-id="a46ee-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="a46ee-117">Attribute</span></span>|<span data-ttu-id="a46ee-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a46ee-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a46ee-119">name</span><span class="sxs-lookup"><span data-stu-id="a46ee-119">name</span></span>|<span data-ttu-id="a46ee-120">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="a46ee-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a46ee-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a46ee-121">Child Elements</span></span>  
 <span data-ttu-id="a46ee-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a46ee-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a46ee-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a46ee-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a46ee-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="a46ee-124">Element</span></span>|<span data-ttu-id="a46ee-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="a46ee-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a46ee-126">\<states></span><span class="sxs-lookup"><span data-stu-id="a46ee-126">\<states></span></span>](states.md)|<span data-ttu-id="a46ee-127">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="a46ee-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a46ee-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a46ee-128">Remarks</span></span>  
 <span data-ttu-id="a46ee-129">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="a46ee-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="a46ee-130">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a46ee-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="a46ee-131">Estado</span><span class="sxs-lookup"><span data-stu-id="a46ee-131">State</span></span>|<span data-ttu-id="a46ee-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="a46ee-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a46ee-133">Anulado</span><span class="sxs-lookup"><span data-stu-id="a46ee-133">Aborted</span></span>|<span data-ttu-id="a46ee-134">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="a46ee-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a46ee-135">Concluído</span><span class="sxs-lookup"><span data-stu-id="a46ee-135">Completed</span></span>|<span data-ttu-id="a46ee-136">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="a46ee-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="a46ee-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="a46ee-137">Deleted</span></span>|<span data-ttu-id="a46ee-138">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="a46ee-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="a46ee-139">Ocioso</span><span class="sxs-lookup"><span data-stu-id="a46ee-139">Idle</span></span>|<span data-ttu-id="a46ee-140">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="a46ee-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a46ee-141">Persistentes</span><span class="sxs-lookup"><span data-stu-id="a46ee-141">Persisted</span></span>|<span data-ttu-id="a46ee-142">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="a46ee-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="a46ee-143">Retomada</span><span class="sxs-lookup"><span data-stu-id="a46ee-143">Resumed</span></span>|<span data-ttu-id="a46ee-144">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="a46ee-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="a46ee-145">Introdução</span><span class="sxs-lookup"><span data-stu-id="a46ee-145">Started</span></span>|<span data-ttu-id="a46ee-146">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="a46ee-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="a46ee-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="a46ee-147">UnhandledException</span></span>|<span data-ttu-id="a46ee-148">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="a46ee-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="a46ee-149">Descarregado</span><span class="sxs-lookup"><span data-stu-id="a46ee-149">Unloaded</span></span>|<span data-ttu-id="a46ee-150">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="a46ee-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="a46ee-151">Cancelado</span><span class="sxs-lookup"><span data-stu-id="a46ee-151">Canceled</span></span>|<span data-ttu-id="a46ee-152">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="a46ee-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="a46ee-153">Suspenso</span><span class="sxs-lookup"><span data-stu-id="a46ee-153">Suspended</span></span>|<span data-ttu-id="a46ee-154">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="a46ee-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="a46ee-155">Encerrada</span><span class="sxs-lookup"><span data-stu-id="a46ee-155">Terminated</span></span>|<span data-ttu-id="a46ee-156">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="a46ee-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="a46ee-157">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="a46ee-157">Unsuspended</span></span>|<span data-ttu-id="a46ee-158">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="a46ee-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a46ee-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a46ee-159">Example</span></span>  
 <span data-ttu-id="a46ee-160">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="a46ee-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a46ee-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a46ee-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a46ee-162">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a46ee-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a46ee-163">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a46ee-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
