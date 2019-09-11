---
title: <workflowInstanceQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854735"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="329f0-102">\<workflowInstanceQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="329f0-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="329f0-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="329f0-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="329f0-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="329f0-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="329f0-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="329f0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="329f0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="329f0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="329f0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="329f0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="329f0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowInstanceQueries**](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="329f0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="329f0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowInstanceQuery**</span><span class="sxs-lookup"><span data-stu-id="329f0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329f0-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="329f0-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="329f0-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="329f0-114">Attributes and elements</span></span>  

<span data-ttu-id="329f0-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="329f0-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="329f0-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="329f0-116">Attributes</span></span>  

<span data-ttu-id="329f0-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="329f0-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="329f0-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="329f0-118">Child elements</span></span>  
  
|<span data-ttu-id="329f0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="329f0-119">Element</span></span>|<span data-ttu-id="329f0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="329f0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="329f0-121">\<states></span><span class="sxs-lookup"><span data-stu-id="329f0-121">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="329f0-122">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="329f0-122">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="329f0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="329f0-123">Parent elements</span></span>  
  
|<span data-ttu-id="329f0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="329f0-124">Element</span></span>|<span data-ttu-id="329f0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="329f0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="329f0-126">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="329f0-126">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="329f0-127">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="329f0-127">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="329f0-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="329f0-128">Remarks</span></span>  

<span data-ttu-id="329f0-129"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="329f0-129">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="329f0-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="329f0-130">Example</span></span>  

<span data-ttu-id="329f0-131">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="329f0-131">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="329f0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="329f0-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="329f0-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="329f0-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="329f0-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="329f0-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
