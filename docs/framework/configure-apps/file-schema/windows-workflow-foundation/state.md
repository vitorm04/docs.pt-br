---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398646"
---
# \<state>
<span data-ttu-id="1b4ec-101">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="1b4ec-102">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1b4ec-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="1b4ec-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b4ec-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b4ec-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1b4ec-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1b4ec-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b4ec-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="1b4ec-106">Attributes</span></span>  
  
|<span data-ttu-id="1b4ec-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="1b4ec-107">Attribute</span></span>|<span data-ttu-id="1b4ec-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b4ec-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b4ec-109">name</span><span class="sxs-lookup"><span data-stu-id="1b4ec-109">name</span></span>|<span data-ttu-id="1b4ec-110">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b4ec-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1b4ec-111">Child Elements</span></span>  
 <span data-ttu-id="1b4ec-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b4ec-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1b4ec-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1b4ec-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1b4ec-114">Element</span></span>|<span data-ttu-id="1b4ec-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b4ec-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="1b4ec-116">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b4ec-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b4ec-117">Remarks</span></span>  
 <span data-ttu-id="1b4ec-118">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="1b4ec-119">Estado de possíveis valores é descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="1b4ec-120">Estado</span><span class="sxs-lookup"><span data-stu-id="1b4ec-120">State</span></span>|<span data-ttu-id="1b4ec-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b4ec-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b4ec-122">Anulado</span><span class="sxs-lookup"><span data-stu-id="1b4ec-122">Aborted</span></span>|<span data-ttu-id="1b4ec-123">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1b4ec-124">Concluído</span><span class="sxs-lookup"><span data-stu-id="1b4ec-124">Completed</span></span>|<span data-ttu-id="1b4ec-125">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1b4ec-126">Excluído</span><span class="sxs-lookup"><span data-stu-id="1b4ec-126">Deleted</span></span>|<span data-ttu-id="1b4ec-127">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1b4ec-128">Idle</span><span class="sxs-lookup"><span data-stu-id="1b4ec-128">Idle</span></span>|<span data-ttu-id="1b4ec-129">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1b4ec-130">Persistentes</span><span class="sxs-lookup"><span data-stu-id="1b4ec-130">Persisted</span></span>|<span data-ttu-id="1b4ec-131">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1b4ec-132">Retomada</span><span class="sxs-lookup"><span data-stu-id="1b4ec-132">Resumed</span></span>|<span data-ttu-id="1b4ec-133">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1b4ec-134">Iniciado</span><span class="sxs-lookup"><span data-stu-id="1b4ec-134">Started</span></span>|<span data-ttu-id="1b4ec-135">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1b4ec-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="1b4ec-136">UnhandledException</span></span>|<span data-ttu-id="1b4ec-137">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1b4ec-138">Descarregado</span><span class="sxs-lookup"><span data-stu-id="1b4ec-138">Unloaded</span></span>|<span data-ttu-id="1b4ec-139">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1b4ec-140">Canceled</span><span class="sxs-lookup"><span data-stu-id="1b4ec-140">Canceled</span></span>|<span data-ttu-id="1b4ec-141">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1b4ec-142">Suspenso</span><span class="sxs-lookup"><span data-stu-id="1b4ec-142">Suspended</span></span>|<span data-ttu-id="1b4ec-143">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1b4ec-144">Encerrada</span><span class="sxs-lookup"><span data-stu-id="1b4ec-144">Terminated</span></span>|<span data-ttu-id="1b4ec-145">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1b4ec-146">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="1b4ec-146">Unsuspended</span></span>|<span data-ttu-id="1b4ec-147">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1b4ec-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1b4ec-148">Example</span></span>  
 <span data-ttu-id="1b4ec-149">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="1b4ec-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b4ec-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="1b4ec-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1b4ec-151">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1b4ec-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1b4ec-152">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="1b4ec-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
