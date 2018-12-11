---
title: '&lt;Argumentos&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 6810e004d74cec1dec3056017eb324ff667d9f1d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152561"
---
# <a name="ltargumentsgt"></a><span data-ttu-id="6f28b-102">&lt;Argumentos&gt;</span><span class="sxs-lookup"><span data-stu-id="6f28b-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="6f28b-103">Representa uma coleção de argumentos associados a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="6f28b-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="6f28b-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6f28b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6f28b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6f28b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6f28b-106">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="6f28b-106">\<tracking></span></span>  
<span data-ttu-id="6f28b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6f28b-107">\<trackingProfile></span></span>  
<span data-ttu-id="6f28b-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6f28b-108">\<workflow></span></span>  
<span data-ttu-id="6f28b-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="6f28b-109">\<activityStateQueries></span></span>  
<span data-ttu-id="6f28b-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="6f28b-110">\<activityStateQuery></span></span>  
<span data-ttu-id="6f28b-111">\<argumentos ></span><span class="sxs-lookup"><span data-stu-id="6f28b-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f28b-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f28b-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f28b-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f28b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6f28b-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f28b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f28b-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f28b-115">Attributes</span></span>  
 <span data-ttu-id="6f28b-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f28b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f28b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f28b-117">Child Elements</span></span>  
  
|<span data-ttu-id="6f28b-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f28b-118">Element</span></span>|<span data-ttu-id="6f28b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f28b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f28b-120">\<argumento ></span><span class="sxs-lookup"><span data-stu-id="6f28b-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="6f28b-121">Um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="6f28b-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f28b-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f28b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6f28b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f28b-123">Element</span></span>|<span data-ttu-id="6f28b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f28b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f28b-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="6f28b-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="6f28b-126">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6f28b-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6f28b-127">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="6f28b-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f28b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f28b-128">Remarks</span></span>  
 <span data-ttu-id="6f28b-129">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6f28b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="6f28b-130">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="6f28b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="6f28b-131">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6f28b-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="6f28b-132">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="6f28b-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="6f28b-133">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="6f28b-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f28b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f28b-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="6f28b-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6f28b-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6f28b-136">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6f28b-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
