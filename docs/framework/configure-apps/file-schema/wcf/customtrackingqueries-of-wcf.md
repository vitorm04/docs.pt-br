---
title: <customTrackingQueries>do WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855436"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="1278b-102">\<customTrackingQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="1278b-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="1278b-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="1278b-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="1278b-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1278b-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="1278b-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1278b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="1278b-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1278b-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1278b-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1278b-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1278b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1278b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="1278b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="1278b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="1278b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1278b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="1278b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="1278b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="1278b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> customTrackingQueries**</span><span class="sxs-lookup"><span data-stu-id="1278b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="1278b-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1278b-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1278b-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1278b-114">Attributes and elements</span></span>

<span data-ttu-id="1278b-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1278b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1278b-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="1278b-116">Attributes</span></span>

<span data-ttu-id="1278b-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1278b-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="1278b-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1278b-118">Child elements</span></span>
  
|<span data-ttu-id="1278b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="1278b-119">Element</span></span>|<span data-ttu-id="1278b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="1278b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1278b-121">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="1278b-121">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="1278b-122">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="1278b-122">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1278b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1278b-123">Parent elements</span></span>  
  
|<span data-ttu-id="1278b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="1278b-124">Element</span></span>|<span data-ttu-id="1278b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="1278b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1278b-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="1278b-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="1278b-127">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1278b-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1278b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1278b-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1278b-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1278b-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1278b-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="1278b-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
