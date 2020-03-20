---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152418"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="e6c06-101">\<atividades> de consultas programadas</span><span class="sxs-lookup"><span data-stu-id="e6c06-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="e6c06-102">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e6c06-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e6c06-103">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="e6c06-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e6c06-104">Para obter mais informações sobre o rastreamento de consultas de perfil, consulte [Perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e6c06-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e6c06-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6c06-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6c06-106">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e6c06-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e6c06-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e6c06-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e6c06-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e6c06-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e6c06-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e6c06-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e6c06-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<atividades>agendadas**</span><span class="sxs-lookup"><span data-stu-id="e6c06-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c06-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6c06-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6c06-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e6c06-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e6c06-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e6c06-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6c06-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="e6c06-114">Attributes</span></span>  
 <span data-ttu-id="e6c06-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e6c06-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6c06-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e6c06-116">Child Elements</span></span>  
  
|<span data-ttu-id="e6c06-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6c06-117">Element</span></span>|<span data-ttu-id="e6c06-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6c06-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6c06-119">\<atividade>de queda programada</span><span class="sxs-lookup"><span data-stu-id="e6c06-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="e6c06-120">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e6c06-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6c06-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e6c06-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e6c06-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6c06-122">Element</span></span>|<span data-ttu-id="e6c06-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6c06-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6c06-124">\<>de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e6c06-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e6c06-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="e6c06-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6c06-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6c06-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e6c06-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e6c06-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e6c06-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e6c06-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
