---
title: <faultPropagationQuery>do WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 6ba6478ca500c0a8ef150966a97898f8743ffdf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925626"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="40c72-102">\<faultPropagationQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="40c72-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="40c72-103">Representa uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="40c72-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="40c72-104">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="40c72-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="40c72-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="40c72-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="40c72-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="40c72-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="40c72-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="40c72-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="40c72-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="40c72-108">\<system.serviceModel></span></span>\
<span data-ttu-id="40c72-109">\<tracking></span><span class="sxs-lookup"><span data-stu-id="40c72-109">\<tracking></span></span>\
<span data-ttu-id="40c72-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="40c72-110">\<profiles></span></span>\
<span data-ttu-id="40c72-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="40c72-111">\<trackingProfile></span></span>\
<span data-ttu-id="40c72-112">\<> do fluxo de trabalho </span><span class="sxs-lookup"><span data-stu-id="40c72-112">\<workflow></span></span>\
<span data-ttu-id="40c72-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="40c72-113">\<faultPropagationQueries></span></span>\
<span data-ttu-id="40c72-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="40c72-114">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="40c72-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40c72-115">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="40c72-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40c72-116">Attributes and elements</span></span>

<span data-ttu-id="40c72-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="40c72-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="40c72-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="40c72-118">Attributes</span></span>

|<span data-ttu-id="40c72-119">Atributo</span><span class="sxs-lookup"><span data-stu-id="40c72-119">Attribute</span></span>|<span data-ttu-id="40c72-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="40c72-120">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="40c72-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagaram a falha.</span><span class="sxs-lookup"><span data-stu-id="40c72-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="40c72-122">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="40c72-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="40c72-123">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="40c72-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40c72-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="40c72-124">Child elements</span></span>

<span data-ttu-id="40c72-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="40c72-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40c72-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="40c72-126">Parent elements</span></span>

|<span data-ttu-id="40c72-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="40c72-127">Element</span></span>|<span data-ttu-id="40c72-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="40c72-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40c72-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="40c72-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="40c72-130">Representa uma lista de elementos de configuração que são usados para rastrear a manipulação de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="40c72-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="40c72-131">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="40c72-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="40c72-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40c72-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="40c72-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="40c72-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="40c72-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="40c72-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
