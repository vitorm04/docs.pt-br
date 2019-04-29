---
title: <workflowInstanceQueries> do WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 89e122b87743a81a80ce63b382ae235c1c4863bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790514"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="f807e-102">\<workflowInstanceQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="f807e-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="f807e-103">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="f807e-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f807e-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f807e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f807e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f807e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f807e-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="f807e-106">\<tracking></span></span>  
<span data-ttu-id="f807e-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="f807e-107">\<profiles></span></span>  
<span data-ttu-id="f807e-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f807e-108">\<trackingProfile></span></span>  
<span data-ttu-id="f807e-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f807e-109">\<workflow></span></span>  
<span data-ttu-id="f807e-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f807e-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f807e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f807e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f807e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f807e-112">Attributes and elements</span></span>

<span data-ttu-id="f807e-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f807e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f807e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="f807e-114">Attributes</span></span>  

<span data-ttu-id="f807e-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f807e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f807e-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f807e-116">Child elements</span></span>  
  
|<span data-ttu-id="f807e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="f807e-117">Element</span></span>|<span data-ttu-id="f807e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f807e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f807e-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="f807e-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="f807e-120">Uma consulta que é usada para controlar as alterações de ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f807e-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f807e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f807e-121">Parent elements</span></span>  
  
|<span data-ttu-id="f807e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f807e-122">Element</span></span>|<span data-ttu-id="f807e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f807e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f807e-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f807e-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f807e-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) propriedade.</span><span class="sxs-lookup"><span data-stu-id="f807e-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f807e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f807e-126">Remarks</span></span>

<span data-ttu-id="f807e-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="f807e-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f807e-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f807e-128">Example</span></span>  

<span data-ttu-id="f807e-129">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="f807e-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="f807e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f807e-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f807e-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f807e-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f807e-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f807e-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
