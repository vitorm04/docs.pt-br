---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398920"
---
# <a name="arguments"></a><span data-ttu-id="2203e-101">\<argumentos ></span><span class="sxs-lookup"><span data-stu-id="2203e-101">\<arguments></span></span>
<span data-ttu-id="2203e-102">Representa uma coleção de argumentos associados a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="2203e-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="2203e-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2203e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2203e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2203e-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2203e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="2203e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="2203e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="2203e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="2203e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQuery**](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="2203e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="2203e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<argumentos >**</span><span class="sxs-lookup"><span data-stu-id="2203e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2203e-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2203e-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2203e-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2203e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2203e-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2203e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2203e-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="2203e-115">Attributes</span></span>  
 <span data-ttu-id="2203e-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2203e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2203e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2203e-117">Child Elements</span></span>  
  
|<span data-ttu-id="2203e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="2203e-118">Element</span></span>|<span data-ttu-id="2203e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2203e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2203e-120">\<argument></span><span class="sxs-lookup"><span data-stu-id="2203e-120">\<argument></span></span>](argument.md)|<span data-ttu-id="2203e-121">Um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="2203e-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2203e-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2203e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2203e-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="2203e-123">Element</span></span>|<span data-ttu-id="2203e-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="2203e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2203e-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="2203e-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="2203e-126">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="2203e-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2203e-127">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="2203e-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2203e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2203e-128">Remarks</span></span>  
 <span data-ttu-id="2203e-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2203e-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="2203e-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="2203e-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="2203e-131">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2203e-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="2203e-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="2203e-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="2203e-133">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="2203e-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2203e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2203e-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2203e-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2203e-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2203e-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="2203e-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
