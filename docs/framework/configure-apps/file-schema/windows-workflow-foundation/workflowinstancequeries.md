---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 11e301de1ab3dbd4c97f236bfd07c5de4a632272
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398571"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="fa345-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="fa345-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="fa345-102">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="fa345-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="fa345-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fa345-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fa345-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa345-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fa345-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fa345-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="fa345-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="fa345-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="fa345-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="fa345-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="fa345-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fa345-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="fa345-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowInstanceQueries**</span><span class="sxs-lookup"><span data-stu-id="fa345-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa345-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa345-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa345-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fa345-111">Attributes and Elements</span></span>  

<span data-ttu-id="fa345-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fa345-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa345-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="fa345-113">Attributes</span></span>  

<span data-ttu-id="fa345-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fa345-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa345-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fa345-115">Child Elements</span></span>  
  
|<span data-ttu-id="fa345-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa345-116">Element</span></span>|<span data-ttu-id="fa345-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa345-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa345-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="fa345-118">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="fa345-119">Uma consulta que é usada para controlar as alterações de ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa345-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa345-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fa345-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fa345-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa345-121">Element</span></span>|<span data-ttu-id="fa345-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa345-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa345-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="fa345-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="fa345-124">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="fa345-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa345-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa345-125">Remarks</span></span>  

<span data-ttu-id="fa345-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="fa345-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="fa345-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa345-127">Example</span></span>  

<span data-ttu-id="fa345-128">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="fa345-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa345-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa345-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fa345-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="fa345-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fa345-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="fa345-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
