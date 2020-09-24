---
title: <state> do WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: c323f7dba265e7fbcb09482115694088e761af0e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148887"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="9f5b8-102">\<state> do WCF, \<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="9f5b8-102">\<state> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="9f5b8-103">Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="9f5b8-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9f5b8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="9f5b8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f5b8-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f5b8-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f5b8-106">Attributes and elements</span></span>

<span data-ttu-id="9f5b8-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="9f5b8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f5b8-108">Attributes</span></span>

|<span data-ttu-id="9f5b8-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f5b8-109">Attribute</span></span>|<span data-ttu-id="9f5b8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f5b8-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9f5b8-111">Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f5b8-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f5b8-112">Child elements</span></span>

<span data-ttu-id="9f5b8-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f5b8-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f5b8-114">Parent elements</span></span>

|<span data-ttu-id="9f5b8-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f5b8-115">Element</span></span>|<span data-ttu-id="9f5b8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f5b8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="9f5b8-117">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f5b8-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f5b8-118">Remarks</span></span>  

<span data-ttu-id="9f5b8-119">Os registros retornados são filtrados por estados nesta coleção.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="9f5b8-120">Os valores de estado possíveis são descritos na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="9f5b8-120">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="9f5b8-121">Estado</span><span class="sxs-lookup"><span data-stu-id="9f5b8-121">State</span></span>|<span data-ttu-id="9f5b8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f5b8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f5b8-123">Anulado</span><span class="sxs-lookup"><span data-stu-id="9f5b8-123">Aborted</span></span>|<span data-ttu-id="9f5b8-124">A instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9f5b8-125">Concluído</span><span class="sxs-lookup"><span data-stu-id="9f5b8-125">Completed</span></span>|<span data-ttu-id="9f5b8-126">A instância de fluxo de trabalho for concluída.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="9f5b8-127">Excluído</span><span class="sxs-lookup"><span data-stu-id="9f5b8-127">Deleted</span></span>|<span data-ttu-id="9f5b8-128">A instância de fluxo de trabalho é excluída.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="9f5b8-129">Idle</span><span class="sxs-lookup"><span data-stu-id="9f5b8-129">Idle</span></span>|<span data-ttu-id="9f5b8-130">A instância de fluxo de trabalho está ociosa.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="9f5b8-131">Persistente</span><span class="sxs-lookup"><span data-stu-id="9f5b8-131">Persisted</span></span>|<span data-ttu-id="9f5b8-132">A instância de fluxo de trabalho é mantida.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="9f5b8-133">Retomada</span><span class="sxs-lookup"><span data-stu-id="9f5b8-133">Resumed</span></span>|<span data-ttu-id="9f5b8-134">A instância de fluxo de trabalho é retomada.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="9f5b8-135">Iniciado</span><span class="sxs-lookup"><span data-stu-id="9f5b8-135">Started</span></span>|<span data-ttu-id="9f5b8-136">A instância de fluxo de trabalho é iniciada.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="9f5b8-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="9f5b8-137">UnhandledException</span></span>|<span data-ttu-id="9f5b8-138">A instância de fluxo de trabalho encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="9f5b8-139">Descarregado</span><span class="sxs-lookup"><span data-stu-id="9f5b8-139">Unloaded</span></span>|<span data-ttu-id="9f5b8-140">A instância de fluxo de trabalho é descarregada.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="9f5b8-141">Canceled</span><span class="sxs-lookup"><span data-stu-id="9f5b8-141">Canceled</span></span>|<span data-ttu-id="9f5b8-142">A instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="9f5b8-143">Suspenso</span><span class="sxs-lookup"><span data-stu-id="9f5b8-143">Suspended</span></span>|<span data-ttu-id="9f5b8-144">A instância de fluxo de trabalho é suspensa.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="9f5b8-145">Terminado</span><span class="sxs-lookup"><span data-stu-id="9f5b8-145">Terminated</span></span>|<span data-ttu-id="9f5b8-146">A instância de fluxo de trabalho é encerrada.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="9f5b8-147">Não suspenso</span><span class="sxs-lookup"><span data-stu-id="9f5b8-147">Unsuspended</span></span>|<span data-ttu-id="9f5b8-148">A instância de fluxo de trabalho é unsuspended.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f5b8-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f5b8-149">Example</span></span>

<span data-ttu-id="9f5b8-150">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="9f5b8-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="9f5b8-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f5b8-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9f5b8-152">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9f5b8-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9f5b8-153">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="9f5b8-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
