---
title: <workflowInstanceQueries>do WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854779"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="7eb8e-102">\<workflowInstanceQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="7eb8e-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="7eb8e-103">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="7eb8e-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7eb8e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7eb8e-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7eb8e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7eb8e-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7eb8e-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7eb8e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="7eb8e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="7eb8e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="7eb8e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="7eb8e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="7eb8e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="7eb8e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="7eb8e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="7eb8e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowInstanceQueries**</span><span class="sxs-lookup"><span data-stu-id="7eb8e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb8e-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7eb8e-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eb8e-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7eb8e-113">Attributes and elements</span></span>

<span data-ttu-id="7eb8e-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eb8e-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="7eb8e-115">Attributes</span></span>  

<span data-ttu-id="7eb8e-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7eb8e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7eb8e-117">Child elements</span></span>  
  
|<span data-ttu-id="7eb8e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="7eb8e-118">Element</span></span>|<span data-ttu-id="7eb8e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eb8e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eb8e-120">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7eb8e-120">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="7eb8e-121">Uma consulta que é usada para controlar as alterações de ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-121">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7eb8e-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7eb8e-122">Parent elements</span></span>  
  
|<span data-ttu-id="7eb8e-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7eb8e-123">Element</span></span>|<span data-ttu-id="7eb8e-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eb8e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eb8e-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7eb8e-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="7eb8e-126">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) .</span><span class="sxs-lookup"><span data-stu-id="7eb8e-126">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eb8e-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="7eb8e-127">Remarks</span></span>

<span data-ttu-id="7eb8e-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="7eb8e-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="7eb8e-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7eb8e-129">Example</span></span>  

<span data-ttu-id="7eb8e-130">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="7eb8e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eb8e-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7eb8e-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7eb8e-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7eb8e-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7eb8e-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
