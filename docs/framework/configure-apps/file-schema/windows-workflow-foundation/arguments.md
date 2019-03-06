---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 3e9fc4f286e7aba6406ce61910da9e614e13ffca
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368084"
---
# <a name="arguments"></a><span data-ttu-id="b7ee1-101">\<arguments></span><span class="sxs-lookup"><span data-stu-id="b7ee1-101">\<arguments></span></span>
<span data-ttu-id="b7ee1-102">Representa uma coleção de argumentos associados a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="b7ee1-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b7ee1-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b7ee1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b7ee1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b7ee1-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b7ee1-105">\<tracking></span></span>  
<span data-ttu-id="b7ee1-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b7ee1-106">\<trackingProfile></span></span>  
<span data-ttu-id="b7ee1-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="b7ee1-107">\<workflow></span></span>  
<span data-ttu-id="b7ee1-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b7ee1-108">\<activityStateQueries></span></span>  
<span data-ttu-id="b7ee1-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b7ee1-109">\<activityStateQuery></span></span>  
<span data-ttu-id="b7ee1-110">\<arguments></span><span class="sxs-lookup"><span data-stu-id="b7ee1-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ee1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7ee1-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7ee1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7ee1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b7ee1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7ee1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7ee1-114">Attributes</span></span>  
 <span data-ttu-id="b7ee1-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7ee1-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7ee1-116">Child Elements</span></span>  
  
|<span data-ttu-id="b7ee1-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7ee1-117">Element</span></span>|<span data-ttu-id="b7ee1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7ee1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7ee1-119">\<argument></span><span class="sxs-lookup"><span data-stu-id="b7ee1-119">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="b7ee1-120">Um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7ee1-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7ee1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b7ee1-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7ee1-122">Element</span></span>|<span data-ttu-id="b7ee1-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7ee1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7ee1-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b7ee1-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="b7ee1-125">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b7ee1-126">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7ee1-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7ee1-127">Remarks</span></span>  
 <span data-ttu-id="b7ee1-128">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b7ee1-129">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b7ee1-130">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b7ee1-131">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b7ee1-132">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b7ee1-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7ee1-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7ee1-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b7ee1-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7ee1-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b7ee1-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b7ee1-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
