---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398726"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="63d7e-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="63d7e-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="63d7e-102">Representa uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="63d7e-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="63d7e-103">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="63d7e-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="63d7e-104">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="63d7e-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="63d7e-105">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="63d7e-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="63d7e-106">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="63d7e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="63d7e-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="63d7e-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63d7e-108">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="63d7e-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="63d7e-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="63d7e-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="63d7e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="63d7e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="63d7e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="63d7e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="63d7e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> faultPropagationQueries**](faultpropagationqueries.md)</span><span class="sxs-lookup"><span data-stu-id="63d7e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)</span></span>\
<span data-ttu-id="63d7e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> faultPropagationQuery**</span><span class="sxs-lookup"><span data-stu-id="63d7e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>

## <a name="syntax"></a><span data-ttu-id="63d7e-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63d7e-114">Syntax</span></span>

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63d7e-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63d7e-115">Attributes and Elements</span></span>

<span data-ttu-id="63d7e-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63d7e-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="63d7e-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="63d7e-117">Attributes</span></span>

|<span data-ttu-id="63d7e-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="63d7e-118">Attribute</span></span>|<span data-ttu-id="63d7e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="63d7e-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="63d7e-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="63d7e-120">activityName</span></span>|<span data-ttu-id="63d7e-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagaram a falha.</span><span class="sxs-lookup"><span data-stu-id="63d7e-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="63d7e-122">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="63d7e-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="63d7e-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="63d7e-123">faultHandlerActivityName</span></span>|<span data-ttu-id="63d7e-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="63d7e-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="63d7e-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63d7e-125">Child Elements</span></span>

<span data-ttu-id="63d7e-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="63d7e-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63d7e-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63d7e-127">Parent Elements</span></span>

|<span data-ttu-id="63d7e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="63d7e-128">Element</span></span>|<span data-ttu-id="63d7e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="63d7e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63d7e-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="63d7e-130">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="63d7e-131">Representa uma lista de elementos de configuração que são usados para rastrear a manipulação de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="63d7e-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="63d7e-132">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="63d7e-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="63d7e-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63d7e-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="63d7e-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="63d7e-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63d7e-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="63d7e-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
