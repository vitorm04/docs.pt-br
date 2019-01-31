---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 1a6899eaa04ad16192e07f4bc2ad1abe6e4aedd5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257358"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="ce6f9-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="ce6f9-101">\<faultPropagationQuery></span></span>
<span data-ttu-id="ce6f9-102">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ce6f9-103">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ce6f9-104">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ce6f9-105">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="ce6f9-106">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ce6f9-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ce6f9-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ce6f9-107">\<system.serviceModel></span></span>  
<span data-ttu-id="ce6f9-108">\<tracking></span><span class="sxs-lookup"><span data-stu-id="ce6f9-108">\<tracking></span></span>  
<span data-ttu-id="ce6f9-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ce6f9-109">\<trackingProfile></span></span>  
<span data-ttu-id="ce6f9-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ce6f9-110">\<workflow></span></span>  
<span data-ttu-id="ce6f9-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="ce6f9-111">\<faultPropagationQueries></span></span>  
<span data-ttu-id="ce6f9-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="ce6f9-112">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6f9-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce6f9-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce6f9-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce6f9-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ce6f9-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce6f9-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce6f9-116">Attributes</span></span>  
  
|<span data-ttu-id="ce6f9-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce6f9-117">Attribute</span></span>|<span data-ttu-id="ce6f9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce6f9-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce6f9-119">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="ce6f9-119">activityName</span></span>|<span data-ttu-id="ce6f9-120">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-120">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="ce6f9-121">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="ce6f9-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="ce6f9-122">faultHandlerActivityName</span></span>|<span data-ttu-id="ce6f9-123">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce6f9-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce6f9-124">Child Elements</span></span>  
 <span data-ttu-id="ce6f9-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce6f9-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce6f9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ce6f9-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce6f9-127">Element</span></span>|<span data-ttu-id="ce6f9-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce6f9-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce6f9-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="ce6f9-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="ce6f9-130">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ce6f9-131">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="ce6f9-131">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce6f9-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce6f9-132">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ce6f9-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ce6f9-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ce6f9-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ce6f9-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
