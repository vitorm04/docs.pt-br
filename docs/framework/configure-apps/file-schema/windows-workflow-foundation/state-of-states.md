---
title: '&lt;estado&gt; de &lt;Estados&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: e4eaf1cbe788018b46759efb1e9755d65b19cc60
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148283"
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="e31aa-102">&lt;estado&gt; de &lt;Estados&gt;</span><span class="sxs-lookup"><span data-stu-id="e31aa-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="e31aa-103">Um elemento de configuração que contém o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="e31aa-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="e31aa-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e31aa-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e31aa-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e31aa-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e31aa-106">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="e31aa-106">\<tracking></span></span>  
<span data-ttu-id="e31aa-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e31aa-107">\<trackingProfile></span></span>  
<span data-ttu-id="e31aa-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e31aa-108">\<workflow></span></span>  
<span data-ttu-id="e31aa-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="e31aa-109">\<activityStateQueries></span></span>  
<span data-ttu-id="e31aa-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e31aa-110">\<activityStateQuery></span></span>  
<span data-ttu-id="e31aa-111">\<estados ></span><span class="sxs-lookup"><span data-stu-id="e31aa-111">\<states></span></span>  
<span data-ttu-id="e31aa-112">\<estado ></span><span class="sxs-lookup"><span data-stu-id="e31aa-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31aa-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e31aa-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e31aa-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e31aa-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e31aa-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e31aa-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e31aa-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="e31aa-116">Attributes</span></span>  
  
|<span data-ttu-id="e31aa-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="e31aa-117">Attribute</span></span>|<span data-ttu-id="e31aa-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e31aa-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e31aa-119">name</span><span class="sxs-lookup"><span data-stu-id="e31aa-119">name</span></span>|<span data-ttu-id="e31aa-120">Uma cadeia de caracteres que especifica o estado da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="e31aa-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e31aa-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e31aa-121">Child Elements</span></span>  
 <span data-ttu-id="e31aa-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e31aa-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e31aa-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e31aa-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e31aa-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e31aa-124">Element</span></span>|<span data-ttu-id="e31aa-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e31aa-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e31aa-126">\<estados ></span><span class="sxs-lookup"><span data-stu-id="e31aa-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="e31aa-127">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="e31aa-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e31aa-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e31aa-128">Remarks</span></span>  
 <span data-ttu-id="e31aa-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e31aa-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e31aa-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="e31aa-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e31aa-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e31aa-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e31aa-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="e31aa-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e31aa-133">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="e31aa-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e31aa-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e31aa-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="e31aa-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e31aa-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e31aa-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e31aa-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
