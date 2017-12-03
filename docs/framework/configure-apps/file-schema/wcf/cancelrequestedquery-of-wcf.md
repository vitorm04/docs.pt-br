---
title: '&lt;cancelRequestedQuery&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fc9df52c691e13802607714977f3aa778cde84e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="b19b0-102">&lt;cancelRequestedQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="b19b0-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="b19b0-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b19b0-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b19b0-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="b19b0-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="b19b0-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b19b0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b19b0-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b19b0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b19b0-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="b19b0-107">\<tracking></span></span>  
<span data-ttu-id="b19b0-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b19b0-108">\<trackingProfile></span></span>  
<span data-ttu-id="b19b0-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="b19b0-109">\<workflow></span></span>  
<span data-ttu-id="b19b0-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b19b0-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="b19b0-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="b19b0-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19b0-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b19b0-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b19b0-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b19b0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b19b0-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b19b0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b19b0-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b19b0-115">Attributes</span></span>  
  
|<span data-ttu-id="b19b0-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b19b0-116">Attribute</span></span>|<span data-ttu-id="b19b0-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b19b0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b19b0-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="b19b0-118">activityName</span></span>|<span data-ttu-id="b19b0-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="b19b0-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b19b0-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b19b0-120">childActivityName</span></span>|<span data-ttu-id="b19b0-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="b19b0-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b19b0-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b19b0-122">Child Elements</span></span>  
 <span data-ttu-id="b19b0-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b19b0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b19b0-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b19b0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b19b0-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b19b0-125">Element</span></span>|<span data-ttu-id="b19b0-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b19b0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b19b0-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b19b0-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="b19b0-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b19b0-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b19b0-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="b19b0-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b19b0-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b19b0-130">See Also</span></span>  
 <span data-ttu-id="b19b0-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b19b0-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b19b0-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b19b0-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="b19b0-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b19b0-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b19b0-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b19b0-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
