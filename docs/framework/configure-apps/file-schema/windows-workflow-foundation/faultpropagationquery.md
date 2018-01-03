---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244ae0db12964e2baf6de15f545cfa40152ee88e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="6cefb-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="6cefb-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="6cefb-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="6cefb-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6cefb-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="6cefb-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="6cefb-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="6cefb-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="6cefb-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="6cefb-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="6cefb-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6cefb-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6cefb-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6cefb-108">\<system.serviceModel></span></span>  
<span data-ttu-id="6cefb-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="6cefb-109">\<tracking></span></span>  
<span data-ttu-id="6cefb-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6cefb-110">\<trackingProfile></span></span>  
<span data-ttu-id="6cefb-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="6cefb-111">\<workflow></span></span>  
<span data-ttu-id="6cefb-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="6cefb-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="6cefb-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="6cefb-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cefb-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cefb-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cefb-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6cefb-115">Attributes and Elements</span></span>  
 <span data-ttu-id="6cefb-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6cefb-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cefb-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="6cefb-117">Attributes</span></span>  
  
|<span data-ttu-id="6cefb-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="6cefb-118">Attribute</span></span>|<span data-ttu-id="6cefb-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cefb-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cefb-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="6cefb-120">activityName</span></span>|<span data-ttu-id="6cefb-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="6cefb-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="6cefb-122">O padrão é *, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="6cefb-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="6cefb-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="6cefb-123">faultHandlerActivityName</span></span>|<span data-ttu-id="6cefb-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="6cefb-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cefb-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6cefb-125">Child Elements</span></span>  
 <span data-ttu-id="6cefb-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6cefb-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cefb-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6cefb-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6cefb-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="6cefb-128">Element</span></span>|<span data-ttu-id="6cefb-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cefb-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cefb-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="6cefb-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="6cefb-131">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="6cefb-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6cefb-132">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="6cefb-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cefb-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cefb-133">See Also</span></span>  
 <span data-ttu-id="6cefb-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6cefb-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="6cefb-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6cefb-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="6cefb-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6cefb-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6cefb-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6cefb-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
