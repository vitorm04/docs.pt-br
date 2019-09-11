---
title: <customTrackingQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855423"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="10087-102">\<customTrackingQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="10087-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="10087-103">Representa uma consulta que é usada para rastrear eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="10087-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="10087-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="10087-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="10087-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10087-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="10087-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="10087-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="10087-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="10087-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="10087-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10087-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="10087-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="10087-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="10087-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10087-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="10087-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10087-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="10087-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> customTrackingQueries**](customtrackingqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10087-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)</span></span>\
<span data-ttu-id="10087-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> customTrackingQuery**</span><span class="sxs-lookup"><span data-stu-id="10087-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10087-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10087-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10087-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="10087-115">Attributes and elements</span></span>  

<span data-ttu-id="10087-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="10087-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10087-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="10087-117">Attributes</span></span>  
  
|<span data-ttu-id="10087-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="10087-118">Attribute</span></span>|<span data-ttu-id="10087-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="10087-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="10087-120">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="10087-120">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="10087-121">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="10087-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10087-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="10087-122">Child elements</span></span>

<span data-ttu-id="10087-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="10087-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10087-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="10087-124">Parent elements</span></span>

|<span data-ttu-id="10087-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="10087-125">Element</span></span>|<span data-ttu-id="10087-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="10087-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10087-127">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="10087-127">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="10087-128">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="10087-128">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="10087-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10087-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="10087-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="10087-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="10087-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="10087-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
