---
title: '&lt;variable&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 7d41d80bfe83cfafca01509d50709e21730bcb97
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltvariablegt"></a><span data-ttu-id="f0a6d-102">&lt;variable&gt;</span><span class="sxs-lookup"><span data-stu-id="f0a6d-102">&lt;variable&gt;</span></span>
<span data-ttu-id="f0a6d-103">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="f0a6d-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f0a6d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f0a6d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f0a6d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f0a6d-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-106">\<tracking></span></span>  
<span data-ttu-id="f0a6d-107">\<perfis ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-107">\<profiles></span></span>  
<span data-ttu-id="f0a6d-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f0a6d-108">\<trackingProfile></span></span>  
<span data-ttu-id="f0a6d-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f0a6d-109">\<workflow></span></span>  
<span data-ttu-id="f0a6d-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-110">\<activityStateQueries></span></span>  
<span data-ttu-id="f0a6d-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-111">\<activityStateQuery></span></span>  
<span data-ttu-id="f0a6d-112">\<variáveis ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-112">\<variables></span></span>  
<span data-ttu-id="f0a6d-113">\<variável ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0a6d-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0a6d-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0a6d-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f0a6d-115">Attributes and Elements</span></span>  
 <span data-ttu-id="f0a6d-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0a6d-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="f0a6d-117">Attributes</span></span>  
  
|<span data-ttu-id="f0a6d-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="f0a6d-118">Attribute</span></span>|<span data-ttu-id="f0a6d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0a6d-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0a6d-120">name</span><span class="sxs-lookup"><span data-stu-id="f0a6d-120">name</span></span>|<span data-ttu-id="f0a6d-121">Uma cadeia de caracteres que especifica o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0a6d-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f0a6d-122">Child Elements</span></span>  
 <span data-ttu-id="f0a6d-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0a6d-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f0a6d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f0a6d-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="f0a6d-125">Element</span></span>|<span data-ttu-id="f0a6d-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0a6d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0a6d-127">\<variável ></span><span class="sxs-lookup"><span data-stu-id="f0a6d-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="f0a6d-128">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0a6d-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0a6d-129">Remarks</span></span>  
 <span data-ttu-id="f0a6d-130">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="f0a6d-131">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="f0a6d-132">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido.</span><span class="sxs-lookup"><span data-stu-id="f0a6d-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="f0a6d-133">Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="f0a6d-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0a6d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0a6d-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="f0a6d-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0a6d-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f0a6d-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f0a6d-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
