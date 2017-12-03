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
ms.openlocfilehash: 330413b676025020924dc15f54170c4dc19e616a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="b7e94-102">&lt;faultPropagationQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="b7e94-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="b7e94-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b7e94-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b7e94-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="b7e94-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b7e94-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b7e94-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b7e94-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="b7e94-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="b7e94-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b7e94-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b7e94-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b7e94-108">\<system.serviceModel></span></span>  
<span data-ttu-id="b7e94-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="b7e94-109">\<tracking></span></span>  
<span data-ttu-id="b7e94-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b7e94-110">\<trackingProfile></span></span>  
<span data-ttu-id="b7e94-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="b7e94-111">\<workflow></span></span>  
<span data-ttu-id="b7e94-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b7e94-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="b7e94-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b7e94-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e94-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7e94-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7e94-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7e94-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b7e94-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7e94-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7e94-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7e94-117">Attributes</span></span>  
  
|<span data-ttu-id="b7e94-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7e94-118">Attribute</span></span>|<span data-ttu-id="b7e94-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e94-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7e94-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="b7e94-120">activityName</span></span>|<span data-ttu-id="b7e94-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="b7e94-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="b7e94-122">O padrão é *, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="b7e94-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="b7e94-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="b7e94-123">faultHandlerActivityName</span></span>|<span data-ttu-id="b7e94-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="b7e94-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7e94-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7e94-125">Child Elements</span></span>  
 <span data-ttu-id="b7e94-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b7e94-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7e94-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7e94-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b7e94-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7e94-128">Element</span></span>|<span data-ttu-id="b7e94-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e94-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e94-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b7e94-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="b7e94-131">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b7e94-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b7e94-132">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="b7e94-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7e94-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7e94-133">See Also</span></span>  
 <span data-ttu-id="b7e94-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b7e94-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b7e94-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b7e94-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b7e94-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7e94-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b7e94-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b7e94-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
