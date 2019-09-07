---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398844"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="005df-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="005df-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="005df-102">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="005df-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="005df-103">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="005df-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="005df-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="005df-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="005df-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="005df-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="005df-106">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="005df-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="005df-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="005df-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="005df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="005df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="005df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="005df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="005df-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> bookmarkResumptionQueries**](bookmarkresumptionqueries.md)</span><span class="sxs-lookup"><span data-stu-id="005df-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)</span></span>\
<span data-ttu-id="005df-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> bookmarkResumptionQuery**</span><span class="sxs-lookup"><span data-stu-id="005df-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005df-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="005df-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="005df-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="005df-113">Attributes and Elements</span></span>  
 <span data-ttu-id="005df-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="005df-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="005df-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="005df-115">Attributes</span></span>  
  
|<span data-ttu-id="005df-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="005df-116">Attribute</span></span>|<span data-ttu-id="005df-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="005df-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="005df-118">name</span><span class="sxs-lookup"><span data-stu-id="005df-118">name</span></span>|<span data-ttu-id="005df-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="005df-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="005df-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="005df-120">Child Elements</span></span>  
 <span data-ttu-id="005df-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="005df-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="005df-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="005df-122">Parent Elements</span></span>  
  
|<span data-ttu-id="005df-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="005df-123">Element</span></span>|<span data-ttu-id="005df-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="005df-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="005df-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="005df-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="005df-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="005df-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="005df-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="005df-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="005df-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="005df-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="005df-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="005df-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
