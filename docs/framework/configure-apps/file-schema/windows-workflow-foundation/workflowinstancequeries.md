---
title: '&lt;workflowInstanceQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: a165d6f55afbbf1489a7355d4207a74ac1f003ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755585"
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="891d2-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="891d2-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="891d2-103">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="891d2-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="891d2-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="891d2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="891d2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="891d2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="891d2-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="891d2-106">\<tracking></span></span>  
<span data-ttu-id="891d2-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="891d2-107">\<trackingProfile></span></span>  
<span data-ttu-id="891d2-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="891d2-108">\<workflow></span></span>  
<span data-ttu-id="891d2-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="891d2-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="891d2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="891d2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="891d2-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="891d2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="891d2-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="891d2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="891d2-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="891d2-113">Attributes</span></span>  
 <span data-ttu-id="891d2-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="891d2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="891d2-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="891d2-115">Child Elements</span></span>  
  
|<span data-ttu-id="891d2-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="891d2-116">Element</span></span>|<span data-ttu-id="891d2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="891d2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="891d2-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="891d2-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="891d2-119">Uma consulta que é usada para controlar as alterações de ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="891d2-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="891d2-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="891d2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="891d2-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="891d2-121">Element</span></span>|<span data-ttu-id="891d2-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="891d2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="891d2-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="891d2-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="891d2-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.</span><span class="sxs-lookup"><span data-stu-id="891d2-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="891d2-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="891d2-125">Remarks</span></span>  
 <span data-ttu-id="891d2-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="891d2-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="891d2-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="891d2-127">Example</span></span>  
 <span data-ttu-id="891d2-128">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="891d2-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="891d2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="891d2-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="891d2-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="891d2-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="891d2-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="891d2-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
