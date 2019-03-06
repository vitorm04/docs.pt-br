---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3ff568c267331538fb9be0e6cb40eebbca44d882
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375656"
---
# <a name="variables"></a><span data-ttu-id="a1498-101">\<variables></span><span class="sxs-lookup"><span data-stu-id="a1498-101">\<variables></span></span>
<span data-ttu-id="a1498-102">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="a1498-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="a1498-103">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a1498-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a1498-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a1498-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a1498-105">\<tracking></span><span class="sxs-lookup"><span data-stu-id="a1498-105">\<tracking></span></span>  
<span data-ttu-id="a1498-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a1498-106">\<trackingProfile></span></span>  
<span data-ttu-id="a1498-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a1498-107">\<workflow></span></span>  
<span data-ttu-id="a1498-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="a1498-108">\<activityStateQueries></span></span>  
<span data-ttu-id="a1498-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="a1498-109">\<activityStateQuery></span></span>  
<span data-ttu-id="a1498-110">\<variables></span><span class="sxs-lookup"><span data-stu-id="a1498-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1498-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1498-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1498-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a1498-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a1498-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a1498-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1498-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1498-114">Attributes</span></span>  
 <span data-ttu-id="a1498-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a1498-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1498-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1498-116">Child Elements</span></span>  
  
|<span data-ttu-id="a1498-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1498-117">Element</span></span>|<span data-ttu-id="a1498-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1498-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1498-119">\<variable></span><span class="sxs-lookup"><span data-stu-id="a1498-119">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="a1498-120">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="a1498-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1498-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a1498-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a1498-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1498-122">Element</span></span>|<span data-ttu-id="a1498-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1498-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1498-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="a1498-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="a1498-125">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="a1498-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a1498-126">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="a1498-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1498-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1498-127">Remarks</span></span>  
 <span data-ttu-id="a1498-128">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a1498-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a1498-129">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="a1498-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a1498-130">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos a extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a1498-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="a1498-131">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="a1498-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a1498-132">Argumentos e variáveis podem ser extraídos somente com um ActivityStateRecord e são assinados dentro de um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="a1498-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1498-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1498-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a1498-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a1498-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a1498-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a1498-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
