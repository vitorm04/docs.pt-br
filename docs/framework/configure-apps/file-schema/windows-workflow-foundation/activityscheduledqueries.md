---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: a43242e2f22c48a57c11f6f03657d7d3de27ff48
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398977"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="eef7a-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="eef7a-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="eef7a-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="eef7a-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="eef7a-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="eef7a-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="eef7a-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="eef7a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="eef7a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eef7a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eef7a-106">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="eef7a-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="eef7a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="eef7a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="eef7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="eef7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="eef7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="eef7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="eef7a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> activityScheduledQueries**</span><span class="sxs-lookup"><span data-stu-id="eef7a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef7a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eef7a-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eef7a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eef7a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eef7a-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eef7a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eef7a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="eef7a-114">Attributes</span></span>  
 <span data-ttu-id="eef7a-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eef7a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eef7a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eef7a-116">Child Elements</span></span>  
  
|<span data-ttu-id="eef7a-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="eef7a-117">Element</span></span>|<span data-ttu-id="eef7a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="eef7a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eef7a-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="eef7a-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="eef7a-120">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="eef7a-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eef7a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eef7a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eef7a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="eef7a-122">Element</span></span>|<span data-ttu-id="eef7a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="eef7a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eef7a-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="eef7a-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="eef7a-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="eef7a-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eef7a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eef7a-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="eef7a-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eef7a-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="eef7a-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="eef7a-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
