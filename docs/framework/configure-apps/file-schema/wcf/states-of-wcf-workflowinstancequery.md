---
title: <states>do WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855032"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="0d5e8-102">\<states>do WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="0d5e8-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="0d5e8-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="0d5e8-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0d5e8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="0d5e8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d5e8-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d5e8-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d5e8-106">Attributes and elements</span></span>

<span data-ttu-id="0d5e8-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d5e8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d5e8-108">Attributes</span></span>  

<span data-ttu-id="0d5e8-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d5e8-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d5e8-110">Child elements</span></span>
  
|<span data-ttu-id="0d5e8-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d5e8-111">Element</span></span>|<span data-ttu-id="0d5e8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5e8-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="0d5e8-113">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-113">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d5e8-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d5e8-114">Parent elements</span></span>  
  
|<span data-ttu-id="0d5e8-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d5e8-115">Element</span></span>|<span data-ttu-id="0d5e8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5e8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="0d5e8-117">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-117">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d5e8-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d5e8-118">Remarks</span></span>

<span data-ttu-id="0d5e8-119">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="0d5e8-120">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="0d5e8-121">Estado</span><span class="sxs-lookup"><span data-stu-id="0d5e8-121">State</span></span>|<span data-ttu-id="0d5e8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5e8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0d5e8-123">Anulado</span><span class="sxs-lookup"><span data-stu-id="0d5e8-123">Aborted</span></span>|<span data-ttu-id="0d5e8-124">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="0d5e8-125">Concluído</span><span class="sxs-lookup"><span data-stu-id="0d5e8-125">Completed</span></span>|<span data-ttu-id="0d5e8-126">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="0d5e8-127">Excluído</span><span class="sxs-lookup"><span data-stu-id="0d5e8-127">Deleted</span></span>|<span data-ttu-id="0d5e8-128">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="0d5e8-129">Idle</span><span class="sxs-lookup"><span data-stu-id="0d5e8-129">Idle</span></span>|<span data-ttu-id="0d5e8-130">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="0d5e8-131">Persistentes</span><span class="sxs-lookup"><span data-stu-id="0d5e8-131">Persisted</span></span>|<span data-ttu-id="0d5e8-132">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="0d5e8-133">Retomada</span><span class="sxs-lookup"><span data-stu-id="0d5e8-133">Resumed</span></span>|<span data-ttu-id="0d5e8-134">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="0d5e8-135">Iniciado</span><span class="sxs-lookup"><span data-stu-id="0d5e8-135">Started</span></span>|<span data-ttu-id="0d5e8-136">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="0d5e8-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="0d5e8-137">UnhandledException</span></span>|<span data-ttu-id="0d5e8-138">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="0d5e8-139">Descarregado</span><span class="sxs-lookup"><span data-stu-id="0d5e8-139">Unloaded</span></span>|<span data-ttu-id="0d5e8-140">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="0d5e8-141">Canceled</span><span class="sxs-lookup"><span data-stu-id="0d5e8-141">Canceled</span></span>|<span data-ttu-id="0d5e8-142">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="0d5e8-143">Suspenso</span><span class="sxs-lookup"><span data-stu-id="0d5e8-143">Suspended</span></span>|<span data-ttu-id="0d5e8-144">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="0d5e8-145">Encerrada</span><span class="sxs-lookup"><span data-stu-id="0d5e8-145">Terminated</span></span>|<span data-ttu-id="0d5e8-146">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="0d5e8-147">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="0d5e8-147">Unsuspended</span></span>|<span data-ttu-id="0d5e8-148">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0d5e8-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d5e8-149">Example</span></span>

<span data-ttu-id="0d5e8-150">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="0d5e8-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="0d5e8-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d5e8-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0d5e8-152">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0d5e8-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0d5e8-153">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0d5e8-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
