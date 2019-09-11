---
title: <bookmarkResumptionQueries>do WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850133"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="bd21e-102">\<bookmarkResumptionQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="bd21e-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="bd21e-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bd21e-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bd21e-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="bd21e-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="bd21e-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bd21e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="bd21e-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd21e-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd21e-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd21e-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd21e-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="bd21e-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="bd21e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="bd21e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="bd21e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="bd21e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="bd21e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="bd21e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="bd21e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> bookmarkResumptionQueries**</span><span class="sxs-lookup"><span data-stu-id="bd21e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="bd21e-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd21e-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd21e-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd21e-114">Attributes and elements</span></span>  
  
<span data-ttu-id="bd21e-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bd21e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd21e-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd21e-116">Attributes</span></span>  
  
<span data-ttu-id="bd21e-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bd21e-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd21e-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bd21e-118">Child elements</span></span>  
  
|<span data-ttu-id="bd21e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd21e-119">Element</span></span>|<span data-ttu-id="bd21e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd21e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd21e-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="bd21e-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="bd21e-122">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bd21e-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bd21e-123">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="bd21e-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd21e-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bd21e-124">Parent elements</span></span>  
  
|<span data-ttu-id="bd21e-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd21e-125">Element</span></span>|<span data-ttu-id="bd21e-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd21e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd21e-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="bd21e-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="bd21e-128">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="bd21e-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd21e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd21e-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bd21e-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bd21e-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bd21e-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="bd21e-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
