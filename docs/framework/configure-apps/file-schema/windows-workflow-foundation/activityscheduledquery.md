---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152405"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="644d3-101">\<> de atividadeSprogramadas de consulta</span><span class="sxs-lookup"><span data-stu-id="644d3-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="644d3-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="644d3-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="644d3-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="644d3-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="644d3-104">Para obter mais informações sobre o rastreamento de consultas de perfil, consulte [Perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="644d3-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="644d3-106">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="644d3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="644d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="644d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="644d3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<atividades>agendadas**](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="644d3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="644d3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<atividade>de queda programada**</span><span class="sxs-lookup"><span data-stu-id="644d3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="644d3-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="644d3-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="644d3-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="644d3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="644d3-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="644d3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="644d3-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="644d3-115">Attributes</span></span>  
  
|<span data-ttu-id="644d3-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="644d3-116">Attribute</span></span>|<span data-ttu-id="644d3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="644d3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="644d3-118">activityName</span><span class="sxs-lookup"><span data-stu-id="644d3-118">activityName</span></span>|<span data-ttu-id="644d3-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="644d3-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="644d3-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="644d3-120">childActivityName</span></span>|<span data-ttu-id="644d3-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="644d3-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="644d3-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="644d3-122">Child Elements</span></span>  
 <span data-ttu-id="644d3-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="644d3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="644d3-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="644d3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="644d3-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="644d3-125">Element</span></span>|<span data-ttu-id="644d3-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="644d3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="644d3-127">\<atividade>de queda programada</span><span class="sxs-lookup"><span data-stu-id="644d3-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="644d3-128">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="644d3-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="644d3-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="644d3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="644d3-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="644d3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="644d3-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="644d3-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
