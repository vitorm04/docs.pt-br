---
title: <activityScheduledQueries>do WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850500"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="27ee0-102">\<activityScheduledQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="27ee0-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="27ee0-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="27ee0-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="27ee0-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="27ee0-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="27ee0-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="27ee0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="27ee0-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27ee0-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27ee0-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="27ee0-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27ee0-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="27ee0-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="27ee0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="27ee0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="27ee0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="27ee0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="27ee0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="27ee0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="27ee0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> activityScheduledQueries**</span><span class="sxs-lookup"><span data-stu-id="27ee0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27ee0-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27ee0-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27ee0-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27ee0-114">Attributes and elements</span></span>  

<span data-ttu-id="27ee0-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="27ee0-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27ee0-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="27ee0-116">Attributes</span></span>  

<span data-ttu-id="27ee0-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="27ee0-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27ee0-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27ee0-118">Child elements</span></span>  
  
|<span data-ttu-id="27ee0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="27ee0-119">Element</span></span>|<span data-ttu-id="27ee0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="27ee0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27ee0-121">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="27ee0-121">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="27ee0-122">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="27ee0-122">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27ee0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="27ee0-123">Parent elements</span></span>  
  
|<span data-ttu-id="27ee0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="27ee0-124">Element</span></span>|<span data-ttu-id="27ee0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="27ee0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27ee0-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="27ee0-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="27ee0-127">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="27ee0-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27ee0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27ee0-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="27ee0-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="27ee0-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="27ee0-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="27ee0-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
