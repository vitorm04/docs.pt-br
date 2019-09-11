---
title: <state>do WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854956"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="b370c-102">\<Estado > do WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="b370c-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="b370c-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="b370c-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="b370c-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b370c-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b370c-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b370c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="b370c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="b370c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="b370c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="b370c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="b370c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQueries**](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="b370c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQuery**](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="b370c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de Estados**](states-of-wcf-workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="b370c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)</span></span>\
<span data-ttu-id="b370c-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Estado >**</span><span class="sxs-lookup"><span data-stu-id="b370c-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b370c-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b370c-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b370c-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b370c-116">Attributes and elements</span></span>

<span data-ttu-id="b370c-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b370c-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="b370c-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="b370c-118">Attributes</span></span>

|<span data-ttu-id="b370c-119">Atributo</span><span class="sxs-lookup"><span data-stu-id="b370c-119">Attribute</span></span>|<span data-ttu-id="b370c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b370c-120">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="b370c-121">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="b370c-121">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b370c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b370c-122">Child elements</span></span>

<span data-ttu-id="b370c-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b370c-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b370c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b370c-124">Parent elements</span></span>

|<span data-ttu-id="b370c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b370c-125">Element</span></span>|<span data-ttu-id="b370c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b370c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b370c-127">\<states></span><span class="sxs-lookup"><span data-stu-id="b370c-127">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="b370c-128">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="b370c-128">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b370c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="b370c-129">Remarks</span></span>  

<span data-ttu-id="b370c-130">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="b370c-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="b370c-131">Os valores de estado possíveis são descritos na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="b370c-131">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="b370c-132">Estado</span><span class="sxs-lookup"><span data-stu-id="b370c-132">State</span></span>|<span data-ttu-id="b370c-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="b370c-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b370c-134">Anulado</span><span class="sxs-lookup"><span data-stu-id="b370c-134">Aborted</span></span>|<span data-ttu-id="b370c-135">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="b370c-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b370c-136">Concluído</span><span class="sxs-lookup"><span data-stu-id="b370c-136">Completed</span></span>|<span data-ttu-id="b370c-137">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="b370c-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="b370c-138">Deleted</span><span class="sxs-lookup"><span data-stu-id="b370c-138">Deleted</span></span>|<span data-ttu-id="b370c-139">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="b370c-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="b370c-140">Ocioso</span><span class="sxs-lookup"><span data-stu-id="b370c-140">Idle</span></span>|<span data-ttu-id="b370c-141">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="b370c-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="b370c-142">Persistentes</span><span class="sxs-lookup"><span data-stu-id="b370c-142">Persisted</span></span>|<span data-ttu-id="b370c-143">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="b370c-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="b370c-144">Retomada</span><span class="sxs-lookup"><span data-stu-id="b370c-144">Resumed</span></span>|<span data-ttu-id="b370c-145">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="b370c-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="b370c-146">Introdução</span><span class="sxs-lookup"><span data-stu-id="b370c-146">Started</span></span>|<span data-ttu-id="b370c-147">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="b370c-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="b370c-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="b370c-148">UnhandledException</span></span>|<span data-ttu-id="b370c-149">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="b370c-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="b370c-150">Descarregado</span><span class="sxs-lookup"><span data-stu-id="b370c-150">Unloaded</span></span>|<span data-ttu-id="b370c-151">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="b370c-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="b370c-152">Cancelado</span><span class="sxs-lookup"><span data-stu-id="b370c-152">Canceled</span></span>|<span data-ttu-id="b370c-153">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="b370c-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="b370c-154">Suspenso</span><span class="sxs-lookup"><span data-stu-id="b370c-154">Suspended</span></span>|<span data-ttu-id="b370c-155">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="b370c-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="b370c-156">Encerrada</span><span class="sxs-lookup"><span data-stu-id="b370c-156">Terminated</span></span>|<span data-ttu-id="b370c-157">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="b370c-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="b370c-158">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="b370c-158">Unsuspended</span></span>|<span data-ttu-id="b370c-159">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="b370c-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b370c-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b370c-160">Example</span></span>

<span data-ttu-id="b370c-161">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="b370c-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="b370c-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b370c-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b370c-163">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b370c-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b370c-164">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b370c-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
