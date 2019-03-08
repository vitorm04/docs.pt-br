---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679353"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="f135e-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="f135e-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="f135e-102">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="f135e-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f135e-103">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="f135e-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f135e-104">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="f135e-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f135e-105">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="f135e-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="f135e-106">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f135e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="f135e-107">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="f135e-107">\<system.serviceModel>\\</span></span>
<span data-ttu-id="f135e-108">\<tracking>\\</span><span class="sxs-lookup"><span data-stu-id="f135e-108">\<tracking>\\</span></span>
<span data-ttu-id="f135e-109">\<trackingProfile>\\</span><span class="sxs-lookup"><span data-stu-id="f135e-109">\<trackingProfile>\\</span></span>
<span data-ttu-id="f135e-110">\<fluxo de trabalho > \\</span><span class="sxs-lookup"><span data-stu-id="f135e-110">\<workflow>\\</span></span>
<span data-ttu-id="f135e-111">\<faultPropagationQueries>\\</span><span class="sxs-lookup"><span data-stu-id="f135e-111">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="f135e-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="f135e-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="f135e-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f135e-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="f135e-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f135e-114">Attributes and Elements</span></span>

<span data-ttu-id="f135e-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f135e-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f135e-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="f135e-116">Attributes</span></span>

|<span data-ttu-id="f135e-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="f135e-117">Attribute</span></span>|<span data-ttu-id="f135e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f135e-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f135e-119">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="f135e-119">activityName</span></span>|<span data-ttu-id="f135e-120">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagou a falha.</span><span class="sxs-lookup"><span data-stu-id="f135e-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="f135e-121">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="f135e-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="f135e-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="f135e-122">faultHandlerActivityName</span></span>|<span data-ttu-id="f135e-123">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="f135e-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f135e-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f135e-124">Child Elements</span></span>

<span data-ttu-id="f135e-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f135e-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f135e-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f135e-126">Parent Elements</span></span>

|<span data-ttu-id="f135e-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="f135e-127">Element</span></span>|<span data-ttu-id="f135e-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="f135e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f135e-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="f135e-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="f135e-130">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="f135e-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f135e-131">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="f135e-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f135e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f135e-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f135e-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f135e-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f135e-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f135e-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
