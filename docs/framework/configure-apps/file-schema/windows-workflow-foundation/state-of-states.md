---
title: '&lt;estado&gt; de &lt;Estados&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0985c9ea84cc29b1cb8883411d3b9b1e52de97b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="f3f18-102">&lt;estado&gt; de &lt;Estados&gt;</span><span class="sxs-lookup"><span data-stu-id="f3f18-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="f3f18-103">Um elemento de configuração que contém o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="f3f18-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="f3f18-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f3f18-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f3f18-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f3f18-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f3f18-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="f3f18-106">\<tracking></span></span>  
<span data-ttu-id="f3f18-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f3f18-107">\<trackingProfile></span></span>  
<span data-ttu-id="f3f18-108">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="f3f18-108">\<workflow></span></span>  
<span data-ttu-id="f3f18-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="f3f18-109">\<activityStateQueries></span></span>  
<span data-ttu-id="f3f18-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="f3f18-110">\<activityStateQuery></span></span>  
<span data-ttu-id="f3f18-111">\<estados ></span><span class="sxs-lookup"><span data-stu-id="f3f18-111">\<states></span></span>  
<span data-ttu-id="f3f18-112">\<estado ></span><span class="sxs-lookup"><span data-stu-id="f3f18-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f18-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3f18-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3f18-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f3f18-114">Attributes and Elements</span></span>  
 <span data-ttu-id="f3f18-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f3f18-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3f18-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="f3f18-116">Attributes</span></span>  
  
|<span data-ttu-id="f3f18-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="f3f18-117">Attribute</span></span>|<span data-ttu-id="f3f18-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3f18-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3f18-119">name</span><span class="sxs-lookup"><span data-stu-id="f3f18-119">name</span></span>|<span data-ttu-id="f3f18-120">Uma cadeia de caracteres que especifica o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="f3f18-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3f18-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f3f18-121">Child Elements</span></span>  
 <span data-ttu-id="f3f18-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f3f18-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3f18-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f3f18-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f3f18-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3f18-124">Element</span></span>|<span data-ttu-id="f3f18-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3f18-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3f18-126">\<estados ></span><span class="sxs-lookup"><span data-stu-id="f3f18-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="f3f18-127">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="f3f18-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3f18-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3f18-128">Remarks</span></span>  
 <span data-ttu-id="f3f18-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f3f18-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="f3f18-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="f3f18-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="f3f18-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido.</span><span class="sxs-lookup"><span data-stu-id="f3f18-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="f3f18-132">Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="f3f18-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3f18-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3f18-133">See Also</span></span>  
 <span data-ttu-id="f3f18-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f3f18-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f3f18-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f3f18-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f3f18-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f3f18-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f3f18-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f3f18-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
