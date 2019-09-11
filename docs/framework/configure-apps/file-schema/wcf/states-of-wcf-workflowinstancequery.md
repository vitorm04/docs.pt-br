---
title: <states>do WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855032"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="d9ec2-102">\<Estados > do WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="d9ec2-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="d9ec2-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="d9ec2-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d9ec2-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9ec2-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d9ec2-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="d9ec2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="d9ec2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="d9ec2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="d9ec2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="d9ec2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQueries**](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="d9ec2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQuery**](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d9ec2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="d9ec2-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de Estados**</span><span class="sxs-lookup"><span data-stu-id="d9ec2-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ec2-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9ec2-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9ec2-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9ec2-115">Attributes and elements</span></span>

<span data-ttu-id="d9ec2-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9ec2-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9ec2-117">Attributes</span></span>  

<span data-ttu-id="d9ec2-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9ec2-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9ec2-119">Child elements</span></span>
  
|<span data-ttu-id="d9ec2-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9ec2-120">Element</span></span>|<span data-ttu-id="d9ec2-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9ec2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9ec2-122">\<states></span><span class="sxs-lookup"><span data-stu-id="d9ec2-122">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="d9ec2-123">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-123">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9ec2-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9ec2-124">Parent elements</span></span>  
  
|<span data-ttu-id="d9ec2-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9ec2-125">Element</span></span>|<span data-ttu-id="d9ec2-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9ec2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9ec2-127">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="d9ec2-127">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="d9ec2-128">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-128">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9ec2-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9ec2-129">Remarks</span></span>

<span data-ttu-id="d9ec2-130">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="d9ec2-131">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-131">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="d9ec2-132">Estado</span><span class="sxs-lookup"><span data-stu-id="d9ec2-132">State</span></span>|<span data-ttu-id="d9ec2-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9ec2-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9ec2-134">Anulado</span><span class="sxs-lookup"><span data-stu-id="d9ec2-134">Aborted</span></span>|<span data-ttu-id="d9ec2-135">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d9ec2-136">Concluído</span><span class="sxs-lookup"><span data-stu-id="d9ec2-136">Completed</span></span>|<span data-ttu-id="d9ec2-137">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="d9ec2-138">Deleted</span><span class="sxs-lookup"><span data-stu-id="d9ec2-138">Deleted</span></span>|<span data-ttu-id="d9ec2-139">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="d9ec2-140">Ocioso</span><span class="sxs-lookup"><span data-stu-id="d9ec2-140">Idle</span></span>|<span data-ttu-id="d9ec2-141">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="d9ec2-142">Persistentes</span><span class="sxs-lookup"><span data-stu-id="d9ec2-142">Persisted</span></span>|<span data-ttu-id="d9ec2-143">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="d9ec2-144">Retomada</span><span class="sxs-lookup"><span data-stu-id="d9ec2-144">Resumed</span></span>|<span data-ttu-id="d9ec2-145">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="d9ec2-146">Introdução</span><span class="sxs-lookup"><span data-stu-id="d9ec2-146">Started</span></span>|<span data-ttu-id="d9ec2-147">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="d9ec2-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="d9ec2-148">UnhandledException</span></span>|<span data-ttu-id="d9ec2-149">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="d9ec2-150">Descarregado</span><span class="sxs-lookup"><span data-stu-id="d9ec2-150">Unloaded</span></span>|<span data-ttu-id="d9ec2-151">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="d9ec2-152">Cancelado</span><span class="sxs-lookup"><span data-stu-id="d9ec2-152">Canceled</span></span>|<span data-ttu-id="d9ec2-153">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="d9ec2-154">Suspenso</span><span class="sxs-lookup"><span data-stu-id="d9ec2-154">Suspended</span></span>|<span data-ttu-id="d9ec2-155">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="d9ec2-156">Encerrada</span><span class="sxs-lookup"><span data-stu-id="d9ec2-156">Terminated</span></span>|<span data-ttu-id="d9ec2-157">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="d9ec2-158">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="d9ec2-158">Unsuspended</span></span>|<span data-ttu-id="d9ec2-159">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9ec2-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9ec2-160">Example</span></span>

<span data-ttu-id="d9ec2-161">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="d9ec2-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="d9ec2-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9ec2-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d9ec2-163">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d9ec2-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d9ec2-164">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d9ec2-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
