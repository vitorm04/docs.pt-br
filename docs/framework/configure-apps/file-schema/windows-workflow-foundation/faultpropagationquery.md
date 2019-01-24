---
title: '&lt;faultPropagationQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: a91a6f61b39a780ed48ad8d5f5e0dfb9ef60da39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538330"
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="0c0c1-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="0c0c1-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="0c0c1-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0c0c1-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="0c0c1-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0c0c1-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="0c0c1-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0c0c1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0c0c1-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0c0c1-108">\<system.serviceModel></span></span>  
<span data-ttu-id="0c0c1-109">\<tracking></span><span class="sxs-lookup"><span data-stu-id="0c0c1-109">\<tracking></span></span>  
<span data-ttu-id="0c0c1-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0c0c1-110">\<trackingProfile></span></span>  
<span data-ttu-id="0c0c1-111">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0c0c1-111">\<workflow></span></span>  
<span data-ttu-id="0c0c1-112">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="0c0c1-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="0c0c1-113">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="0c0c1-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0c1-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c0c1-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c0c1-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c0c1-115">Attributes and Elements</span></span>  
 <span data-ttu-id="0c0c1-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c0c1-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c0c1-117">Attributes</span></span>  
  
|<span data-ttu-id="0c0c1-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="0c0c1-118">Attribute</span></span>|<span data-ttu-id="0c0c1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c0c1-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c0c1-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="0c0c1-120">activityName</span></span>|<span data-ttu-id="0c0c1-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="0c0c1-122">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="0c0c1-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="0c0c1-123">faultHandlerActivityName</span></span>|<span data-ttu-id="0c0c1-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c0c1-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c0c1-125">Child Elements</span></span>  
 <span data-ttu-id="0c0c1-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c0c1-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c0c1-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0c0c1-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c0c1-128">Element</span></span>|<span data-ttu-id="0c0c1-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c0c1-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c0c1-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="0c0c1-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="0c0c1-131">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0c0c1-132">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0c0c1-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c0c1-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c0c1-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0c0c1-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0c0c1-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0c0c1-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0c0c1-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
