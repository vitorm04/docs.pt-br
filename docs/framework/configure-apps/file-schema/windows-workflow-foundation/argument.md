---
title: '&lt;argument&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: bfcb98085e0b2292d46acfd0a57096219afff606
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756313"
---
# <a name="ltargumentgt"></a><span data-ttu-id="4fe9d-102">&lt;argument&gt;</span><span class="sxs-lookup"><span data-stu-id="4fe9d-102">&lt;argument&gt;</span></span>
<span data-ttu-id="4fe9d-103">Um elemento de configuração que representa um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="4fe9d-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4fe9d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4fe9d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4fe9d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4fe9d-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="4fe9d-106">\<tracking></span></span>  
<span data-ttu-id="4fe9d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4fe9d-107">\<trackingProfile></span></span>  
<span data-ttu-id="4fe9d-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4fe9d-108">\<workflow></span></span>  
<span data-ttu-id="4fe9d-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="4fe9d-109">\<activityStateQueries></span></span>  
<span data-ttu-id="4fe9d-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="4fe9d-110">\<activityStateQuery></span></span>  
<span data-ttu-id="4fe9d-111">\<argumentos ></span><span class="sxs-lookup"><span data-stu-id="4fe9d-111">\<arguments></span></span>  
<span data-ttu-id="4fe9d-112">\<argumento ></span><span class="sxs-lookup"><span data-stu-id="4fe9d-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe9d-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fe9d-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe9d-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4fe9d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe9d-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe9d-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="4fe9d-116">Attributes</span></span>  
  
|<span data-ttu-id="4fe9d-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="4fe9d-117">Attribute</span></span>|<span data-ttu-id="4fe9d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe9d-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fe9d-119">name</span><span class="sxs-lookup"><span data-stu-id="4fe9d-119">name</span></span>|<span data-ttu-id="4fe9d-120">Uma cadeia de caracteres que especifica o nome do argumento.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe9d-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4fe9d-121">Child Elements</span></span>  
 <span data-ttu-id="4fe9d-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe9d-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4fe9d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe9d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fe9d-124">Element</span></span>|<span data-ttu-id="4fe9d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe9d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe9d-126">\<argumentos ></span><span class="sxs-lookup"><span data-stu-id="4fe9d-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="4fe9d-127">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe9d-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fe9d-128">Remarks</span></span>  
 <span data-ttu-id="4fe9d-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4fe9d-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4fe9d-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido.</span><span class="sxs-lookup"><span data-stu-id="4fe9d-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4fe9d-132">Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="4fe9d-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fe9d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fe9d-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="4fe9d-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4fe9d-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4fe9d-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="4fe9d-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
