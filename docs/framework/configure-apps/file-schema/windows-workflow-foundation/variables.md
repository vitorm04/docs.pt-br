---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 563ce96f61bbb39f1590ca0f43c163ea2d3d7961
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947251"
---
# <a name="variables"></a><span data-ttu-id="2221f-101">\<variáveis ></span><span class="sxs-lookup"><span data-stu-id="2221f-101">\<variables></span></span>
<span data-ttu-id="2221f-102">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="2221f-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="2221f-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2221f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2221f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2221f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2221f-105">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="2221f-105">\<tracking></span></span>  
<span data-ttu-id="2221f-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2221f-106">\<trackingProfile></span></span>  
<span data-ttu-id="2221f-107">\<workflow></span><span class="sxs-lookup"><span data-stu-id="2221f-107">\<workflow></span></span>  
<span data-ttu-id="2221f-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="2221f-108">\<activityStateQueries></span></span>  
<span data-ttu-id="2221f-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="2221f-109">\<activityStateQuery></span></span>  
<span data-ttu-id="2221f-110">\<variáveis ></span><span class="sxs-lookup"><span data-stu-id="2221f-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2221f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2221f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2221f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2221f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2221f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2221f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2221f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="2221f-114">Attributes</span></span>  
 <span data-ttu-id="2221f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2221f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2221f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2221f-116">Child Elements</span></span>  
  
|<span data-ttu-id="2221f-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="2221f-117">Element</span></span>|<span data-ttu-id="2221f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="2221f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2221f-119">\<variable></span><span class="sxs-lookup"><span data-stu-id="2221f-119">\<variable></span></span>](variable.md)|<span data-ttu-id="2221f-120">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="2221f-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2221f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2221f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2221f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="2221f-122">Element</span></span>|<span data-ttu-id="2221f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="2221f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2221f-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="2221f-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="2221f-125">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="2221f-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2221f-126">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="2221f-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2221f-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="2221f-127">Remarks</span></span>  
 <span data-ttu-id="2221f-128">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2221f-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="2221f-129">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="2221f-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="2221f-130">Você pode usar os [ \<argumentos >](arguments.md), [ \<Estados >](states.md) e [ \<Estados >](states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2221f-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="2221f-131">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="2221f-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="2221f-132">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [ \<o activityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="2221f-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2221f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2221f-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2221f-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2221f-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2221f-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="2221f-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
