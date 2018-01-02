---
title: '&lt;faultPropagationQuery&gt; of WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f017b695b91a08c1126b48c944977c054c73affe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="8e901-102">&lt;faultPropagationQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="8e901-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="8e901-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="8e901-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8e901-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="8e901-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="8e901-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="8e901-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="8e901-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="8e901-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="8e901-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8e901-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="8e901-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8e901-108">\<system.serviceModel></span></span>  
<span data-ttu-id="8e901-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="8e901-109">\<tracking></span></span>  
<span data-ttu-id="8e901-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8e901-110">\<trackingProfile></span></span>  
<span data-ttu-id="8e901-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="8e901-111">\<workflow></span></span>  
<span data-ttu-id="8e901-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="8e901-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="8e901-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="8e901-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e901-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e901-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e901-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e901-115">Attributes and Elements</span></span>  
 <span data-ttu-id="8e901-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e901-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e901-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e901-117">Attributes</span></span>  
  
|<span data-ttu-id="8e901-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e901-118">Attribute</span></span>|<span data-ttu-id="8e901-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e901-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e901-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="8e901-120">activityName</span></span>|<span data-ttu-id="8e901-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="8e901-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="8e901-122">O padrão é *, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="8e901-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="8e901-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="8e901-123">faultHandlerActivityName</span></span>|<span data-ttu-id="8e901-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="8e901-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e901-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e901-125">Child Elements</span></span>  
 <span data-ttu-id="8e901-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8e901-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e901-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e901-127">Parent Elements</span></span>  
  
|<span data-ttu-id="8e901-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e901-128">Element</span></span>|<span data-ttu-id="8e901-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e901-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e901-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="8e901-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="8e901-131">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="8e901-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8e901-132">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="8e901-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e901-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e901-133">See Also</span></span>  
 <span data-ttu-id="8e901-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8e901-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8e901-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8e901-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8e901-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8e901-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8e901-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8e901-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
