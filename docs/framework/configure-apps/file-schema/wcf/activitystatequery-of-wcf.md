---
title: '&lt;activityStateQuery&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de042732e7957fa6ea8c22d03ff6892ee1e912f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="a780c-102">&lt;activityStateQuery&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="a780c-102">&lt;activityStateQuery&gt; of WCF</span></span>
<span data-ttu-id="a780c-103">Representa uma consulta que é usada para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a780c-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a780c-104">Por exemplo, convém manter o controle de toda vez que a atividade "Enviar email" é concluído em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a780c-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a780c-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="a780c-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a780c-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="a780c-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="a780c-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a780c-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="a780c-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a780c-108">\<system.serviceModel></span></span>  
<span data-ttu-id="a780c-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="a780c-109">\<tracking></span></span>  
<span data-ttu-id="a780c-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a780c-110">\<trackingProfile></span></span>  
<span data-ttu-id="a780c-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="a780c-111">\<workflow></span></span>  
<span data-ttu-id="a780c-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="a780c-112">\<activityStateQueries></span></span>  
<span data-ttu-id="a780c-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="a780c-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a780c-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a780c-114">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a780c-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a780c-115">Attributes and Elements</span></span>  
 <span data-ttu-id="a780c-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a780c-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a780c-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="a780c-117">Attributes</span></span>  
  
|<span data-ttu-id="a780c-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="a780c-118">Attribute</span></span>|<span data-ttu-id="a780c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a780c-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a780c-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="a780c-120">activityName</span></span>|<span data-ttu-id="a780c-121">Uma cadeia de caracteres que especifica o nome da atividade para filtrar <xref:System.Activities.Tracking.ActivityStateRecord> instâncias no.</span><span class="sxs-lookup"><span data-stu-id="a780c-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a780c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a780c-122">Child Elements</span></span>  
  
|<span data-ttu-id="a780c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a780c-123">Element</span></span>|<span data-ttu-id="a780c-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a780c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a780c-125">\<argumentos ></span><span class="sxs-lookup"><span data-stu-id="a780c-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="a780c-126">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="a780c-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="a780c-127">\<estados ></span><span class="sxs-lookup"><span data-stu-id="a780c-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="a780c-128">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="a780c-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="a780c-129">\<estados ></span><span class="sxs-lookup"><span data-stu-id="a780c-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="a780c-130">Uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="a780c-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a780c-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a780c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="a780c-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="a780c-132">Element</span></span>|<span data-ttu-id="a780c-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="a780c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a780c-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="a780c-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="a780c-135">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="a780c-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a780c-136">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="a780c-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a780c-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="a780c-137">Remarks</span></span>  
 <span data-ttu-id="a780c-138">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a780c-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a780c-139">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="a780c-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a780c-140">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido.</span><span class="sxs-lookup"><span data-stu-id="a780c-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a780c-141">Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="a780c-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a780c-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a780c-142">See Also</span></span>  
 <span data-ttu-id="a780c-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span><span class="sxs-lookup"><span data-stu-id="a780c-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span></span>    
 <span data-ttu-id="a780c-144"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="a780c-144"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>     
 [<span data-ttu-id="a780c-145">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a780c-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a780c-146">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a780c-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
