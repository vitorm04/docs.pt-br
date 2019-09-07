---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397589"
---
# <a name="variables"></a><span data-ttu-id="7e016-101">\<variáveis ></span><span class="sxs-lookup"><span data-stu-id="7e016-101">\<variables></span></span>
<span data-ttu-id="7e016-102">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="7e016-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="7e016-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7e016-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7e016-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e016-105">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7e016-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7e016-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7e016-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7e016-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="7e016-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQuery**](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="7e016-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="7e016-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<variáveis >**</span><span class="sxs-lookup"><span data-stu-id="7e016-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e016-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e016-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e016-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e016-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7e016-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e016-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e016-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e016-115">Attributes</span></span>  
 <span data-ttu-id="7e016-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7e016-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7e016-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e016-117">Child Elements</span></span>  
  
|<span data-ttu-id="7e016-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e016-118">Element</span></span>|<span data-ttu-id="7e016-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e016-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e016-120">\<variable></span><span class="sxs-lookup"><span data-stu-id="7e016-120">\<variable></span></span>](variable.md)|<span data-ttu-id="7e016-121">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="7e016-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e016-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e016-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7e016-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e016-123">Element</span></span>|<span data-ttu-id="7e016-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e016-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e016-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="7e016-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="7e016-126">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7e016-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7e016-127">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="7e016-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e016-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e016-128">Remarks</span></span>  
 <span data-ttu-id="7e016-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7e016-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="7e016-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="7e016-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="7e016-131">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7e016-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="7e016-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="7e016-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7e016-133">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="7e016-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e016-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e016-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7e016-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7e016-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7e016-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="7e016-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
