---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152203"
---
# <a name="customtrackingquery"></a><span data-ttu-id="45b6f-101">\<> de personalTrackingQuery</span><span class="sxs-lookup"><span data-stu-id="45b6f-101">\<customTrackingQuery></span></span>
<span data-ttu-id="45b6f-102">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="45b6f-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="45b6f-103">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="45b6f-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="45b6f-104">Para obter mais informações sobre o rastreamento de consultas de perfil, consulte [Perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="45b6f-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45b6f-106">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="45b6f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="45b6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="45b6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="45b6f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamento personalizado**](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="45b6f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="45b6f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de rastreamento personalizado**</span><span class="sxs-lookup"><span data-stu-id="45b6f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b6f-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45b6f-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45b6f-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45b6f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="45b6f-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="45b6f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45b6f-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="45b6f-115">Attributes</span></span>  
  
|<span data-ttu-id="45b6f-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="45b6f-116">Attribute</span></span>|<span data-ttu-id="45b6f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="45b6f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45b6f-118">activityName</span><span class="sxs-lookup"><span data-stu-id="45b6f-118">activityName</span></span>|<span data-ttu-id="45b6f-119">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="45b6f-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="45b6f-120">name</span><span class="sxs-lookup"><span data-stu-id="45b6f-120">name</span></span>|<span data-ttu-id="45b6f-121">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="45b6f-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45b6f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45b6f-122">Child Elements</span></span>  
 <span data-ttu-id="45b6f-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="45b6f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45b6f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45b6f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="45b6f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="45b6f-125">Element</span></span>|<span data-ttu-id="45b6f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="45b6f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45b6f-127">\<>de rastreamento personalizado</span><span class="sxs-lookup"><span data-stu-id="45b6f-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="45b6f-128">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="45b6f-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45b6f-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="45b6f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="45b6f-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45b6f-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="45b6f-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="45b6f-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
