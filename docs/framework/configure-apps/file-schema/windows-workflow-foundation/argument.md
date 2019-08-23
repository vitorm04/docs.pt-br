---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: f2aeb61e2e72f5bd6a696c031279f2c57907166b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946138"
---
# <a name="argument"></a><span data-ttu-id="b6640-101">\<argumento ></span><span class="sxs-lookup"><span data-stu-id="b6640-101">\<argument></span></span>
<span data-ttu-id="b6640-102">Um elemento de configuração que representa um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="b6640-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="b6640-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b6640-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b6640-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b6640-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b6640-105">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="b6640-105">\<tracking></span></span>  
<span data-ttu-id="b6640-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b6640-106">\<trackingProfile></span></span>  
<span data-ttu-id="b6640-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b6640-107">\<workflow></span></span>  
<span data-ttu-id="b6640-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b6640-108">\<activityStateQueries></span></span>  
<span data-ttu-id="b6640-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b6640-109">\<activityStateQuery></span></span>  
<span data-ttu-id="b6640-110">\<argumentos ></span><span class="sxs-lookup"><span data-stu-id="b6640-110">\<arguments></span></span>  
<span data-ttu-id="b6640-111">\<argumento ></span><span class="sxs-lookup"><span data-stu-id="b6640-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6640-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6640-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6640-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b6640-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b6640-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b6640-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6640-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6640-115">Attributes</span></span>  
  
|<span data-ttu-id="b6640-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b6640-116">Attribute</span></span>|<span data-ttu-id="b6640-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6640-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6640-118">name</span><span class="sxs-lookup"><span data-stu-id="b6640-118">name</span></span>|<span data-ttu-id="b6640-119">Uma cadeia de caracteres que especifica o nome do argumento.</span><span class="sxs-lookup"><span data-stu-id="b6640-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6640-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b6640-120">Child Elements</span></span>  
 <span data-ttu-id="b6640-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b6640-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6640-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b6640-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b6640-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6640-123">Element</span></span>|<span data-ttu-id="b6640-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6640-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6640-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="b6640-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="b6640-126">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="b6640-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6640-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6640-127">Remarks</span></span>  
 <span data-ttu-id="b6640-128">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6640-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b6640-129">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="b6640-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b6640-130">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6640-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b6640-131">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="b6640-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b6640-132">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b6640-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6640-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6640-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b6640-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b6640-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b6640-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b6640-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
