---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 398b018ce407aee0687c95037753f3affa07aa9b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398789"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="f1e0b-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="f1e0b-101">\<customTrackingQueries></span></span>
<span data-ttu-id="f1e0b-102">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="f1e0b-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f1e0b-103">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f1e0b-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="f1e0b-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f1e0b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f1e0b-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1e0b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f1e0b-106">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f1e0b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f1e0b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="f1e0b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="f1e0b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="f1e0b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="f1e0b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f1e0b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="f1e0b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> customTrackingQueries**</span><span class="sxs-lookup"><span data-stu-id="f1e0b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e0b-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1e0b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1e0b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1e0b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f1e0b-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1e0b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1e0b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1e0b-114">Attributes</span></span>  
 <span data-ttu-id="f1e0b-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f1e0b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1e0b-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1e0b-116">Child Elements</span></span>  
  
|<span data-ttu-id="f1e0b-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1e0b-117">Element</span></span>|<span data-ttu-id="f1e0b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1e0b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1e0b-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="f1e0b-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="f1e0b-120">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="f1e0b-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1e0b-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1e0b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f1e0b-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1e0b-122">Element</span></span>|<span data-ttu-id="f1e0b-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1e0b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1e0b-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f1e0b-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="f1e0b-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="f1e0b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1e0b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1e0b-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f1e0b-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f1e0b-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f1e0b-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f1e0b-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
