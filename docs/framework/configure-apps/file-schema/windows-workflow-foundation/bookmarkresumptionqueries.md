---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398860"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="cc95f-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="cc95f-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="cc95f-102">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cc95f-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="cc95f-103">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="cc95f-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="cc95f-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cc95f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cc95f-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc95f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc95f-106">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc95f-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cc95f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="cc95f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="cc95f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="cc95f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="cc95f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc95f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="cc95f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> bookmarkResumptionQueries**</span><span class="sxs-lookup"><span data-stu-id="cc95f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="cc95f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc95f-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc95f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cc95f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cc95f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cc95f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc95f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc95f-114">Attributes</span></span>  
 <span data-ttu-id="cc95f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cc95f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc95f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc95f-116">Child Elements</span></span>  
  
|<span data-ttu-id="cc95f-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc95f-117">Element</span></span>|<span data-ttu-id="cc95f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc95f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc95f-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="cc95f-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="cc95f-120">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cc95f-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="cc95f-121">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="cc95f-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc95f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc95f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cc95f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc95f-123">Element</span></span>|<span data-ttu-id="cc95f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc95f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc95f-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cc95f-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cc95f-126">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="cc95f-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc95f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc95f-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cc95f-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="cc95f-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cc95f-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="cc95f-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
