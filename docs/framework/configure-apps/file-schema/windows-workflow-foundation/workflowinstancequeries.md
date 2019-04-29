---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: e54f98c980f60d02377e38d53d9d0eb48581eec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613281"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="7f1a0-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7f1a0-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="7f1a0-102">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="7f1a0-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7f1a0-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7f1a0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7f1a0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7f1a0-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="7f1a0-105">\<tracking></span></span>  
<span data-ttu-id="7f1a0-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7f1a0-106">\<trackingProfile></span></span>  
<span data-ttu-id="7f1a0-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7f1a0-107">\<workflow></span></span>  
<span data-ttu-id="7f1a0-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7f1a0-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1a0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f1a0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f1a0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f1a0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f1a0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f1a0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f1a0-112">Attributes</span></span>  
 <span data-ttu-id="7f1a0-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f1a0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f1a0-114">Child Elements</span></span>  
  
|<span data-ttu-id="7f1a0-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f1a0-115">Element</span></span>|<span data-ttu-id="7f1a0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f1a0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f1a0-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7f1a0-117">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="7f1a0-118">Uma consulta que é usada para controlar as alterações de ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f1a0-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f1a0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f1a0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f1a0-120">Element</span></span>|<span data-ttu-id="7f1a0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f1a0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f1a0-122">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7f1a0-122">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7f1a0-123">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f1a0-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f1a0-124">Remarks</span></span>  
 <span data-ttu-id="7f1a0-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="7f1a0-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="7f1a0-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f1a0-126">Example</span></span>  
 <span data-ttu-id="7f1a0-127">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f1a0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f1a0-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7f1a0-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7f1a0-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7f1a0-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7f1a0-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
