---
title: <state> de <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 391e552bce34d637a324c78702cb0e7121f2c999
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398658"
---
# <a name="state-of-states"></a><span data-ttu-id="4fe53-102">\<Estado > de \<Estados ></span><span class="sxs-lookup"><span data-stu-id="4fe53-102">\<state> of \<states></span></span>
<span data-ttu-id="4fe53-103">Um elemento de configuração que contém o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="4fe53-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="4fe53-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4fe53-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4fe53-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4fe53-106">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="4fe53-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="4fe53-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="4fe53-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="4fe53-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="4fe53-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQuery**](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="4fe53-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de Estados**](states-of-activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="4fe53-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)</span></span>\
<span data-ttu-id="4fe53-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Estado >**</span><span class="sxs-lookup"><span data-stu-id="4fe53-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe53-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fe53-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe53-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4fe53-115">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe53-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4fe53-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe53-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="4fe53-117">Attributes</span></span>  
  
|<span data-ttu-id="4fe53-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="4fe53-118">Attribute</span></span>|<span data-ttu-id="4fe53-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe53-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fe53-120">name</span><span class="sxs-lookup"><span data-stu-id="4fe53-120">name</span></span>|<span data-ttu-id="4fe53-121">Uma cadeia de caracteres que especifica o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="4fe53-121">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe53-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4fe53-122">Child Elements</span></span>  
 <span data-ttu-id="4fe53-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4fe53-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe53-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4fe53-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe53-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fe53-125">Element</span></span>|<span data-ttu-id="4fe53-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe53-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe53-127">\<states></span><span class="sxs-lookup"><span data-stu-id="4fe53-127">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="4fe53-128">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="4fe53-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe53-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fe53-129">Remarks</span></span>  
 <span data-ttu-id="4fe53-130">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4fe53-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4fe53-131">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="4fe53-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4fe53-132">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4fe53-132">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4fe53-133">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="4fe53-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4fe53-134">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="4fe53-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fe53-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fe53-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4fe53-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4fe53-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4fe53-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4fe53-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
