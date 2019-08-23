---
title: <state> de <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947489"
---
# <a name="state-of-states"></a><span data-ttu-id="ea89a-102">\<Estado > de \<Estados ></span><span class="sxs-lookup"><span data-stu-id="ea89a-102">\<state> of \<states></span></span>
<span data-ttu-id="ea89a-103">Um elemento de configuração que contém o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ea89a-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="ea89a-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ea89a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ea89a-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ea89a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ea89a-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="ea89a-106">\<tracking></span></span>  
<span data-ttu-id="ea89a-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ea89a-107">\<trackingProfile></span></span>  
<span data-ttu-id="ea89a-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ea89a-108">\<workflow></span></span>  
<span data-ttu-id="ea89a-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="ea89a-109">\<activityStateQueries></span></span>  
<span data-ttu-id="ea89a-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ea89a-110">\<activityStateQuery></span></span>  
<span data-ttu-id="ea89a-111">\<> de Estados</span><span class="sxs-lookup"><span data-stu-id="ea89a-111">\<states></span></span>  
<span data-ttu-id="ea89a-112">\<state></span><span class="sxs-lookup"><span data-stu-id="ea89a-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea89a-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea89a-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea89a-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ea89a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ea89a-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ea89a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea89a-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="ea89a-116">Attributes</span></span>  
  
|<span data-ttu-id="ea89a-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="ea89a-117">Attribute</span></span>|<span data-ttu-id="ea89a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea89a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea89a-119">name</span><span class="sxs-lookup"><span data-stu-id="ea89a-119">name</span></span>|<span data-ttu-id="ea89a-120">Uma cadeia de caracteres que especifica o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ea89a-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea89a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ea89a-121">Child Elements</span></span>  
 <span data-ttu-id="ea89a-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ea89a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea89a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ea89a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ea89a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea89a-124">Element</span></span>|<span data-ttu-id="ea89a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea89a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea89a-126">\<states></span><span class="sxs-lookup"><span data-stu-id="ea89a-126">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="ea89a-127">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ea89a-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea89a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea89a-128">Remarks</span></span>  
 <span data-ttu-id="ea89a-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ea89a-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ea89a-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="ea89a-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ea89a-131">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ea89a-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ea89a-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="ea89a-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ea89a-133">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ea89a-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea89a-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea89a-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ea89a-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ea89a-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ea89a-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ea89a-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
