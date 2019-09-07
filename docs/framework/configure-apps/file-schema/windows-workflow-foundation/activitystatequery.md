---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 5d3c35589330ab5bed5f89c0dafac006b9e3af55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398945"
---
# <a name="activitystatequery"></a><span data-ttu-id="3df52-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="3df52-101">\<activityStateQuery></span></span>
<span data-ttu-id="3df52-102">Representa uma consulta que é usada para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3df52-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="3df52-103">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3df52-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="3df52-104">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="3df52-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="3df52-105">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="3df52-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="3df52-106">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3df52-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3df52-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3df52-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3df52-108">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3df52-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="3df52-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="3df52-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="3df52-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="3df52-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="3df52-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3df52-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="3df52-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="3df52-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="3df52-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> activityStateQuery**</span><span class="sxs-lookup"><span data-stu-id="3df52-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df52-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3df52-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3df52-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3df52-115">Attributes and Elements</span></span>  
 <span data-ttu-id="3df52-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3df52-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3df52-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="3df52-117">Attributes</span></span>  
  
|<span data-ttu-id="3df52-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="3df52-118">Attribute</span></span>|<span data-ttu-id="3df52-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df52-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3df52-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="3df52-120">activityName</span></span>|<span data-ttu-id="3df52-121">Uma cadeia de caracteres que especifica o nome da atividade para filtrar <xref:System.Activities.Tracking.ActivityStateRecord> instâncias no.</span><span class="sxs-lookup"><span data-stu-id="3df52-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3df52-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3df52-122">Child Elements</span></span>  
  
|<span data-ttu-id="3df52-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="3df52-123">Element</span></span>|<span data-ttu-id="3df52-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df52-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3df52-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="3df52-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="3df52-126">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="3df52-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="3df52-127">\<states></span><span class="sxs-lookup"><span data-stu-id="3df52-127">\<states></span></span>](states.md)|<span data-ttu-id="3df52-128">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="3df52-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="3df52-129">\<states></span><span class="sxs-lookup"><span data-stu-id="3df52-129">\<states></span></span>](states.md)|<span data-ttu-id="3df52-130">Uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="3df52-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3df52-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3df52-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3df52-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="3df52-132">Element</span></span>|<span data-ttu-id="3df52-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df52-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3df52-134">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="3df52-134">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="3df52-135">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="3df52-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3df52-136">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="3df52-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3df52-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="3df52-137">Remarks</span></span>  
 <span data-ttu-id="3df52-138">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3df52-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="3df52-139">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="3df52-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="3df52-140">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3df52-140">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="3df52-141">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="3df52-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="3df52-142">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="3df52-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3df52-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3df52-143">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3df52-144">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3df52-144">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3df52-145">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3df52-145">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
