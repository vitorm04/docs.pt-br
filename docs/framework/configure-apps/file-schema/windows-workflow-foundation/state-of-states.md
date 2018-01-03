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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13ae0e8cc59adec0b4e4bd9f2cf4c7ea31811602
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="a3be0-102">&lt;estado&gt; de &lt;Estados&gt;</span><span class="sxs-lookup"><span data-stu-id="a3be0-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="a3be0-103">Um elemento de configuração que contém o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="a3be0-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="a3be0-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a3be0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a3be0-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a3be0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a3be0-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="a3be0-106">\<tracking></span></span>  
<span data-ttu-id="a3be0-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a3be0-107">\<trackingProfile></span></span>  
<span data-ttu-id="a3be0-108">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="a3be0-108">\<workflow></span></span>  
<span data-ttu-id="a3be0-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="a3be0-109">\<activityStateQueries></span></span>  
<span data-ttu-id="a3be0-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="a3be0-110">\<activityStateQuery></span></span>  
<span data-ttu-id="a3be0-111">\<estados ></span><span class="sxs-lookup"><span data-stu-id="a3be0-111">\<states></span></span>  
<span data-ttu-id="a3be0-112">\<estado ></span><span class="sxs-lookup"><span data-stu-id="a3be0-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3be0-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3be0-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3be0-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a3be0-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a3be0-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a3be0-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3be0-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3be0-116">Attributes</span></span>  
  
|<span data-ttu-id="a3be0-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3be0-117">Attribute</span></span>|<span data-ttu-id="a3be0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3be0-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3be0-119">name</span><span class="sxs-lookup"><span data-stu-id="a3be0-119">name</span></span>|<span data-ttu-id="a3be0-120">Uma cadeia de caracteres que especifica o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="a3be0-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3be0-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3be0-121">Child Elements</span></span>  
 <span data-ttu-id="a3be0-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a3be0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3be0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a3be0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a3be0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3be0-124">Element</span></span>|<span data-ttu-id="a3be0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3be0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3be0-126">\<estados ></span><span class="sxs-lookup"><span data-stu-id="a3be0-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="a3be0-127">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="a3be0-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3be0-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3be0-128">Remarks</span></span>  
 <span data-ttu-id="a3be0-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3be0-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a3be0-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="a3be0-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a3be0-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido.</span><span class="sxs-lookup"><span data-stu-id="a3be0-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a3be0-132">Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="a3be0-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3be0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3be0-133">See Also</span></span>  
 <span data-ttu-id="a3be0-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a3be0-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a3be0-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a3be0-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="a3be0-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a3be0-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a3be0-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a3be0-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
