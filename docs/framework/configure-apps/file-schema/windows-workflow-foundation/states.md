---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398613"
---
# \<states>
<span data-ttu-id="6c81c-101">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="6c81c-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="6c81c-102">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6c81c-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="6c81c-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c81c-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c81c-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c81c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6c81c-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c81c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c81c-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c81c-106">Attributes</span></span>  
 <span data-ttu-id="6c81c-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6c81c-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6c81c-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c81c-108">Child Elements</span></span>  
  
|<span data-ttu-id="6c81c-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c81c-109">Element</span></span>|<span data-ttu-id="6c81c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c81c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="6c81c-111">Um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="6c81c-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c81c-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c81c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6c81c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c81c-113">Element</span></span>|<span data-ttu-id="6c81c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c81c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="6c81c-115">Uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="6c81c-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c81c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c81c-116">Remarks</span></span>  
 <span data-ttu-id="6c81c-117">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="6c81c-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="6c81c-118">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6c81c-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="6c81c-119">Estado</span><span class="sxs-lookup"><span data-stu-id="6c81c-119">State</span></span>|<span data-ttu-id="6c81c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c81c-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6c81c-121">Anulado</span><span class="sxs-lookup"><span data-stu-id="6c81c-121">Aborted</span></span>|<span data-ttu-id="6c81c-122">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="6c81c-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="6c81c-123">Concluído</span><span class="sxs-lookup"><span data-stu-id="6c81c-123">Completed</span></span>|<span data-ttu-id="6c81c-124">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="6c81c-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="6c81c-125">Excluído</span><span class="sxs-lookup"><span data-stu-id="6c81c-125">Deleted</span></span>|<span data-ttu-id="6c81c-126">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="6c81c-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="6c81c-127">Idle</span><span class="sxs-lookup"><span data-stu-id="6c81c-127">Idle</span></span>|<span data-ttu-id="6c81c-128">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="6c81c-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="6c81c-129">Persistentes</span><span class="sxs-lookup"><span data-stu-id="6c81c-129">Persisted</span></span>|<span data-ttu-id="6c81c-130">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="6c81c-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="6c81c-131">Retomada</span><span class="sxs-lookup"><span data-stu-id="6c81c-131">Resumed</span></span>|<span data-ttu-id="6c81c-132">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="6c81c-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="6c81c-133">Iniciado</span><span class="sxs-lookup"><span data-stu-id="6c81c-133">Started</span></span>|<span data-ttu-id="6c81c-134">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="6c81c-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="6c81c-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="6c81c-135">UnhandledException</span></span>|<span data-ttu-id="6c81c-136">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="6c81c-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="6c81c-137">Descarregado</span><span class="sxs-lookup"><span data-stu-id="6c81c-137">Unloaded</span></span>|<span data-ttu-id="6c81c-138">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="6c81c-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="6c81c-139">Canceled</span><span class="sxs-lookup"><span data-stu-id="6c81c-139">Canceled</span></span>|<span data-ttu-id="6c81c-140">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="6c81c-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="6c81c-141">Suspenso</span><span class="sxs-lookup"><span data-stu-id="6c81c-141">Suspended</span></span>|<span data-ttu-id="6c81c-142">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="6c81c-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="6c81c-143">Encerrada</span><span class="sxs-lookup"><span data-stu-id="6c81c-143">Terminated</span></span>|<span data-ttu-id="6c81c-144">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="6c81c-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="6c81c-145">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="6c81c-145">Unsuspended</span></span>|<span data-ttu-id="6c81c-146">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="6c81c-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c81c-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c81c-147">Example</span></span>  
 <span data-ttu-id="6c81c-148">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="6c81c-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c81c-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c81c-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6c81c-150">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6c81c-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6c81c-151">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6c81c-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
