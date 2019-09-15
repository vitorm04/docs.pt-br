---
title: <activityStateQuery>do WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 49c507424e813067e1dad9b08167d9661acef36f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991225"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="4efea-102">\<activityStateQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="4efea-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="4efea-103">Representa uma consulta que é usada para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4efea-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="4efea-104">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4efea-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="4efea-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="4efea-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="4efea-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="4efea-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="4efea-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4efea-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="4efea-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4efea-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4efea-109">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4efea-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4efea-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4efea-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="4efea-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="4efea-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="4efea-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4efea-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="4efea-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4efea-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="4efea-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> activityStateQueries**](activitystatequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4efea-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)</span></span>\
<span data-ttu-id="4efea-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> activityStateQuery**</span><span class="sxs-lookup"><span data-stu-id="4efea-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4efea-116">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4efea-116">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4efea-117">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4efea-117">Attributes and elements</span></span>  

<span data-ttu-id="4efea-118">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4efea-118">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4efea-119">Atributos</span><span class="sxs-lookup"><span data-stu-id="4efea-119">Attributes</span></span>  
  
|<span data-ttu-id="4efea-120">Atributo</span><span class="sxs-lookup"><span data-stu-id="4efea-120">Attribute</span></span>|<span data-ttu-id="4efea-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efea-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4efea-122">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="4efea-122">activityName</span></span>|<span data-ttu-id="4efea-123">Uma cadeia de caracteres que especifica o nome da atividade para filtrar <xref:System.Activities.Tracking.ActivityStateRecord> instâncias no.</span><span class="sxs-lookup"><span data-stu-id="4efea-123">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4efea-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4efea-124">Child elements</span></span>  
  
|<span data-ttu-id="4efea-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="4efea-125">Element</span></span>|<span data-ttu-id="4efea-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efea-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4efea-127">\<arguments></span><span class="sxs-lookup"><span data-stu-id="4efea-127">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="4efea-128">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="4efea-128">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="4efea-129">\<states></span><span class="sxs-lookup"><span data-stu-id="4efea-129">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="4efea-130">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="4efea-130">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="4efea-131">\<states></span><span class="sxs-lookup"><span data-stu-id="4efea-131">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="4efea-132">Uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="4efea-132">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4efea-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4efea-133">Parent elements</span></span>  
  
|<span data-ttu-id="4efea-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="4efea-134">Element</span></span>|<span data-ttu-id="4efea-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efea-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4efea-136">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="4efea-136">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="4efea-137">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="4efea-137">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4efea-138">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="4efea-138">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4efea-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="4efea-139">Remarks</span></span>

<span data-ttu-id="4efea-140">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4efea-140">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4efea-141">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="4efea-141">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4efea-142">Você pode usar os [ \<argumentos >](../windows-workflow-foundation/arguments.md), [ \<Estados >](../windows-workflow-foundation/states.md) e [ \<Estados >](../windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4efea-142">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4efea-143">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="4efea-143">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4efea-144">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](../windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="4efea-144">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="4efea-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4efea-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="4efea-146">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4efea-146">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4efea-147">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4efea-147">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
