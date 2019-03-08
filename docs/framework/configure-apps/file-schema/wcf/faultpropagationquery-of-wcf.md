---
title: <faultPropagationQuery> do WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: e5793852d49a052d05f6cb2f4efbe166d67afc62
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675401"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="8838e-102">\<faultPropagationQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="8838e-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="8838e-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="8838e-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8838e-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="8838e-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="8838e-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="8838e-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="8838e-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="8838e-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="8838e-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8838e-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="8838e-108">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="8838e-108">\<system.serviceModel>\\</span></span>
<span data-ttu-id="8838e-109">\<tracking>\\</span><span class="sxs-lookup"><span data-stu-id="8838e-109">\<tracking>\\</span></span>
<span data-ttu-id="8838e-110">\<profiles>\\</span><span class="sxs-lookup"><span data-stu-id="8838e-110">\<profiles>\\</span></span>
<span data-ttu-id="8838e-111">\<trackingProfile>\\</span><span class="sxs-lookup"><span data-stu-id="8838e-111">\<trackingProfile>\\</span></span>
<span data-ttu-id="8838e-112">\<fluxo de trabalho > \\</span><span class="sxs-lookup"><span data-stu-id="8838e-112">\<workflow>\\</span></span>
<span data-ttu-id="8838e-113">\<faultPropagationQueries>\\</span><span class="sxs-lookup"><span data-stu-id="8838e-113">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="8838e-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="8838e-114">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="8838e-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8838e-115">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8838e-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8838e-116">Attributes and elements</span></span>

<span data-ttu-id="8838e-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8838e-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8838e-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="8838e-118">Attributes</span></span>

|<span data-ttu-id="8838e-119">Atributo</span><span class="sxs-lookup"><span data-stu-id="8838e-119">Attribute</span></span>|<span data-ttu-id="8838e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="8838e-120">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="8838e-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagou a falha.</span><span class="sxs-lookup"><span data-stu-id="8838e-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="8838e-122">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="8838e-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="8838e-123">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="8838e-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8838e-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8838e-124">Child elements</span></span>

<span data-ttu-id="8838e-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8838e-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8838e-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8838e-126">Parent elements</span></span>

|<span data-ttu-id="8838e-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="8838e-127">Element</span></span>|<span data-ttu-id="8838e-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="8838e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8838e-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="8838e-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="8838e-130">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="8838e-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8838e-131">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="8838e-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8838e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8838e-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8838e-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8838e-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8838e-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8838e-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
