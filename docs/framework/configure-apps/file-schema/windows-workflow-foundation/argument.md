---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: ed08f5533cd6b3839775d061452cb17110cc627e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398900"
---
# <a name="argument"></a><span data-ttu-id="91965-101">\<argumento ></span><span class="sxs-lookup"><span data-stu-id="91965-101">\<argument></span></span>
<span data-ttu-id="91965-102">Um elemento de configuração que representa um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="91965-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="91965-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="91965-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="91965-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91965-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91965-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="91965-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="91965-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="91965-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="91965-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="91965-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="91965-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="91965-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="91965-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="91965-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="91965-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQuery**](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="91965-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="91965-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<argumentos >** ](arguments.md)</span><span class="sxs-lookup"><span data-stu-id="91965-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)</span></span>\
<span data-ttu-id="91965-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<argumento >**</span><span class="sxs-lookup"><span data-stu-id="91965-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91965-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91965-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91965-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="91965-114">Attributes and Elements</span></span>  
 <span data-ttu-id="91965-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="91965-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91965-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="91965-116">Attributes</span></span>  
  
|<span data-ttu-id="91965-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="91965-117">Attribute</span></span>|<span data-ttu-id="91965-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="91965-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91965-119">name</span><span class="sxs-lookup"><span data-stu-id="91965-119">name</span></span>|<span data-ttu-id="91965-120">Uma cadeia de caracteres que especifica o nome do argumento.</span><span class="sxs-lookup"><span data-stu-id="91965-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91965-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="91965-121">Child Elements</span></span>  
 <span data-ttu-id="91965-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="91965-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91965-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="91965-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91965-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="91965-124">Element</span></span>|<span data-ttu-id="91965-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="91965-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91965-126">\<arguments></span><span class="sxs-lookup"><span data-stu-id="91965-126">\<arguments></span></span>](arguments.md)|<span data-ttu-id="91965-127">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="91965-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91965-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="91965-128">Remarks</span></span>  
 <span data-ttu-id="91965-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91965-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="91965-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="91965-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="91965-131">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91965-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="91965-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="91965-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="91965-133">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="91965-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91965-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91965-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="91965-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="91965-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="91965-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="91965-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
