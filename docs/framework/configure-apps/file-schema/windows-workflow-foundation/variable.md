---
title: '&lt;variable&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 185e7e7196f6679ec3d1fae8a2a256b934022ca9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647875"
---
# <a name="ltvariablegt"></a><span data-ttu-id="d5236-102">&lt;variable&gt;</span><span class="sxs-lookup"><span data-stu-id="d5236-102">&lt;variable&gt;</span></span>
<span data-ttu-id="d5236-103">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="d5236-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="d5236-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d5236-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d5236-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d5236-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d5236-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="d5236-106">\<tracking></span></span>  
<span data-ttu-id="d5236-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="d5236-107">\<profiles></span></span>  
<span data-ttu-id="d5236-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d5236-108">\<trackingProfile></span></span>  
<span data-ttu-id="d5236-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d5236-109">\<workflow></span></span>  
<span data-ttu-id="d5236-110">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="d5236-110">\<activityStateQueries></span></span>  
<span data-ttu-id="d5236-111">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d5236-111">\<activityStateQuery></span></span>  
<span data-ttu-id="d5236-112">\<variables></span><span class="sxs-lookup"><span data-stu-id="d5236-112">\<variables></span></span>  
<span data-ttu-id="d5236-113">\<variable></span><span class="sxs-lookup"><span data-stu-id="d5236-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5236-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5236-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5236-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d5236-115">Attributes and Elements</span></span>  
 <span data-ttu-id="d5236-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d5236-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5236-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="d5236-117">Attributes</span></span>  
  
|<span data-ttu-id="d5236-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="d5236-118">Attribute</span></span>|<span data-ttu-id="d5236-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5236-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5236-120">name</span><span class="sxs-lookup"><span data-stu-id="d5236-120">name</span></span>|<span data-ttu-id="d5236-121">Uma cadeia de caracteres que especifica o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="d5236-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5236-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d5236-122">Child Elements</span></span>  
 <span data-ttu-id="d5236-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d5236-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5236-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d5236-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d5236-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d5236-125">Element</span></span>|<span data-ttu-id="d5236-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5236-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5236-127">\<variable></span><span class="sxs-lookup"><span data-stu-id="d5236-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="d5236-128">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="d5236-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5236-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5236-129">Remarks</span></span>  
 <span data-ttu-id="d5236-130">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d5236-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d5236-131">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="d5236-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d5236-132">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d5236-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d5236-133">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="d5236-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d5236-134">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d5236-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5236-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5236-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d5236-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d5236-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d5236-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d5236-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
