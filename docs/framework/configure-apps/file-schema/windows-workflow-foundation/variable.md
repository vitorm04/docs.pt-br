---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: c85f3c57739c48566c97c8b1debfb7f2c3912bdf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613515"
---
# <a name="variable"></a><span data-ttu-id="b1033-101">\<variable></span><span class="sxs-lookup"><span data-stu-id="b1033-101">\<variable></span></span>
<span data-ttu-id="b1033-102">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="b1033-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="b1033-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b1033-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b1033-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b1033-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b1033-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b1033-105">\<tracking></span></span>  
<span data-ttu-id="b1033-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="b1033-106">\<profiles></span></span>  
<span data-ttu-id="b1033-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b1033-107">\<trackingProfile></span></span>  
<span data-ttu-id="b1033-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b1033-108">\<workflow></span></span>  
<span data-ttu-id="b1033-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b1033-109">\<activityStateQueries></span></span>  
<span data-ttu-id="b1033-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b1033-110">\<activityStateQuery></span></span>  
<span data-ttu-id="b1033-111">\<variables></span><span class="sxs-lookup"><span data-stu-id="b1033-111">\<variables></span></span>  
<span data-ttu-id="b1033-112">\<variable></span><span class="sxs-lookup"><span data-stu-id="b1033-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1033-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1033-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1033-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1033-114">Attributes and Elements</span></span>  
 <span data-ttu-id="b1033-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1033-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1033-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1033-116">Attributes</span></span>  
  
|<span data-ttu-id="b1033-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="b1033-117">Attribute</span></span>|<span data-ttu-id="b1033-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1033-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1033-119">name</span><span class="sxs-lookup"><span data-stu-id="b1033-119">name</span></span>|<span data-ttu-id="b1033-120">Uma cadeia de caracteres que especifica o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="b1033-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1033-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1033-121">Child Elements</span></span>  
 <span data-ttu-id="b1033-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b1033-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1033-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1033-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b1033-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1033-124">Element</span></span>|<span data-ttu-id="b1033-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1033-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1033-126">\<variable></span><span class="sxs-lookup"><span data-stu-id="b1033-126">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="b1033-127">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="b1033-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1033-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1033-128">Remarks</span></span>  
 <span data-ttu-id="b1033-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b1033-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b1033-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="b1033-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b1033-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b1033-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b1033-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="b1033-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b1033-133">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b1033-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1033-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1033-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b1033-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b1033-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b1033-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b1033-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
