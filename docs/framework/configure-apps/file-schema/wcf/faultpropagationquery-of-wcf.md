---
title: <faultPropagationQuery>do WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855335"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="4a9f6-102">\<faultPropagationQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="4a9f6-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="4a9f6-103">Representa uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4a9f6-104">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="4a9f6-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="4a9f6-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="4a9f6-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4a9f6-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="4a9f6-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a9f6-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4a9f6-109">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4a9f6-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4a9f6-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4a9f6-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="4a9f6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="4a9f6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="4a9f6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4a9f6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="4a9f6-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4a9f6-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="4a9f6-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> faultPropagationQueries**](faultpropagationqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4a9f6-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)</span></span>\
<span data-ttu-id="4a9f6-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> faultPropagationQuery**</span><span class="sxs-lookup"><span data-stu-id="4a9f6-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="4a9f6-116">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a9f6-116">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a9f6-117">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4a9f6-117">Attributes and elements</span></span>

<span data-ttu-id="4a9f6-118">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-118">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a9f6-119">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a9f6-119">Attributes</span></span>

|<span data-ttu-id="4a9f6-120">Atributo</span><span class="sxs-lookup"><span data-stu-id="4a9f6-120">Attribute</span></span>|<span data-ttu-id="4a9f6-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a9f6-121">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="4a9f6-122">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagaram a falha.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-122">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="4a9f6-123">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-123">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="4a9f6-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4a9f6-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4a9f6-125">Child elements</span></span>

<span data-ttu-id="4a9f6-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a9f6-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4a9f6-127">Parent elements</span></span>

|<span data-ttu-id="4a9f6-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a9f6-128">Element</span></span>|<span data-ttu-id="4a9f6-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a9f6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a9f6-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="4a9f6-130">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="4a9f6-131">Representa uma lista de elementos de configuração que são usados para rastrear a manipulação de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4a9f6-132">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="4a9f6-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4a9f6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a9f6-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4a9f6-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4a9f6-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4a9f6-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4a9f6-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
