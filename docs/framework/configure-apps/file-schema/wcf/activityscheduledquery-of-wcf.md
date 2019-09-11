---
title: <activityScheduledQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850469"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="003f4-102">\<activityScheduledQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="003f4-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="003f4-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="003f4-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="003f4-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="003f4-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="003f4-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="003f4-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="003f4-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="003f4-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="003f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="003f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="003f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="003f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="003f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityScheduledQueries**](activityscheduledqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="003f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)</span></span>\
<span data-ttu-id="003f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> activityScheduledQuery**</span><span class="sxs-lookup"><span data-stu-id="003f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="003f4-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="003f4-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="003f4-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="003f4-115">Attributes and elements</span></span>  

<span data-ttu-id="003f4-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="003f4-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="003f4-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="003f4-117">Attributes</span></span>  
  
|<span data-ttu-id="003f4-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="003f4-118">Attribute</span></span>|<span data-ttu-id="003f4-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="003f4-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="003f4-120">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="003f4-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="003f4-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="003f4-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="003f4-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="003f4-122">Child elements</span></span>

<span data-ttu-id="003f4-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="003f4-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="003f4-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="003f4-124">Parent elements</span></span>  
  
|<span data-ttu-id="003f4-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="003f4-125">Element</span></span>|<span data-ttu-id="003f4-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="003f4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="003f4-127">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="003f4-127">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="003f4-128">Uma coleção de consultas que são usadas para rastrear uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="003f4-128">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="003f4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="003f4-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="003f4-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="003f4-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="003f4-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="003f4-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
