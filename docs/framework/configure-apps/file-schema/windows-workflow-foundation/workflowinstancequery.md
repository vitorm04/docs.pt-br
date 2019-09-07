---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397508"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="449bf-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="449bf-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="449bf-102">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="449bf-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="449bf-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="449bf-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="449bf-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="449bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="449bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="449bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="449bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQueries**](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="449bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="449bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowInstanceQuery**</span><span class="sxs-lookup"><span data-stu-id="449bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="449bf-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="449bf-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="449bf-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="449bf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="449bf-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="449bf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="449bf-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="449bf-114">Attributes</span></span>  
 <span data-ttu-id="449bf-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="449bf-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="449bf-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="449bf-116">Child Elements</span></span>  
  
|<span data-ttu-id="449bf-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="449bf-117">Element</span></span>|<span data-ttu-id="449bf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="449bf-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="449bf-119">\<states></span><span class="sxs-lookup"><span data-stu-id="449bf-119">\<states></span></span>](states.md)|<span data-ttu-id="449bf-120">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="449bf-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="449bf-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="449bf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="449bf-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="449bf-122">Element</span></span>|<span data-ttu-id="449bf-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="449bf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="449bf-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="449bf-124">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="449bf-125">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="449bf-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="449bf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="449bf-126">Remarks</span></span>  
 <span data-ttu-id="449bf-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="449bf-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="449bf-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="449bf-128">Example</span></span>  
 <span data-ttu-id="449bf-129">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="449bf-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="449bf-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="449bf-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="449bf-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="449bf-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="449bf-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="449bf-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
