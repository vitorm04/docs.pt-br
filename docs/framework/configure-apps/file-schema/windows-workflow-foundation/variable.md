---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397773"
---
# <a name="variable"></a><span data-ttu-id="12f76-101">\<variable></span><span class="sxs-lookup"><span data-stu-id="12f76-101">\<variable></span></span>
<span data-ttu-id="12f76-102">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="12f76-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="12f76-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="12f76-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="12f76-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="12f76-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="12f76-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="12f76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="12f76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="12f76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="12f76-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQuery**](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="12f76-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<variáveis >** ](variables.md)</span><span class="sxs-lookup"><span data-stu-id="12f76-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)</span></span>\
<span data-ttu-id="12f76-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de variável**</span><span class="sxs-lookup"><span data-stu-id="12f76-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f76-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12f76-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12f76-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="12f76-114">Attributes and Elements</span></span>  
 <span data-ttu-id="12f76-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="12f76-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12f76-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="12f76-116">Attributes</span></span>  
  
|<span data-ttu-id="12f76-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="12f76-117">Attribute</span></span>|<span data-ttu-id="12f76-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="12f76-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12f76-119">name</span><span class="sxs-lookup"><span data-stu-id="12f76-119">name</span></span>|<span data-ttu-id="12f76-120">Uma cadeia de caracteres que especifica o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="12f76-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12f76-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="12f76-121">Child Elements</span></span>  
 <span data-ttu-id="12f76-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="12f76-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12f76-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="12f76-123">Parent Elements</span></span>  
  
|<span data-ttu-id="12f76-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="12f76-124">Element</span></span>|<span data-ttu-id="12f76-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="12f76-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12f76-126">\<variable></span><span class="sxs-lookup"><span data-stu-id="12f76-126">\<variable></span></span>](variable.md)|<span data-ttu-id="12f76-127">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="12f76-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12f76-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="12f76-128">Remarks</span></span>  
 <span data-ttu-id="12f76-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="12f76-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="12f76-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="12f76-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="12f76-131">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="12f76-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="12f76-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="12f76-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="12f76-133">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="12f76-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12f76-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12f76-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="12f76-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="12f76-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="12f76-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="12f76-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
