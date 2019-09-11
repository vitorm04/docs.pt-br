---
title: <bookmarkResumptionQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 36d169b78e78692c7b45c75d5d375bddbba1c66f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850109"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="ae85b-102">\<bookmarkResumptionQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="ae85b-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="ae85b-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ae85b-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ae85b-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="ae85b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="ae85b-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="ae85b-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ae85b-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ae85b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="ae85b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="ae85b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="ae85b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="ae85b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="ae85b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> bookmarkResumptionQueries**](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ae85b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="ae85b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> bookmarkResumptionQuery**</span><span class="sxs-lookup"><span data-stu-id="ae85b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae85b-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae85b-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae85b-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae85b-115">Attributes and elements</span></span>

<span data-ttu-id="ae85b-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae85b-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae85b-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae85b-117">Attributes</span></span>  
  
|<span data-ttu-id="ae85b-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="ae85b-118">Attribute</span></span>|<span data-ttu-id="ae85b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae85b-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="ae85b-120">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="ae85b-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae85b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae85b-121">Child elements</span></span>

<span data-ttu-id="ae85b-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ae85b-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ae85b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae85b-123">Parent elements</span></span>  
  
|<span data-ttu-id="ae85b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae85b-124">Element</span></span>|<span data-ttu-id="ae85b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae85b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae85b-126">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="ae85b-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="ae85b-127">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ae85b-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae85b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae85b-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ae85b-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ae85b-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ae85b-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ae85b-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
