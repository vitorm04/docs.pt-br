---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6b1137e89799af34d0808d83e56c7c333a49635
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="bc211-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="bc211-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="bc211-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="bc211-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="bc211-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="bc211-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="bc211-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bc211-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="bc211-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bc211-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bc211-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="bc211-107">\<tracking></span></span>  
<span data-ttu-id="bc211-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bc211-108">\<trackingProfile></span></span>  
<span data-ttu-id="bc211-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="bc211-109">\<workflow></span></span>  
<span data-ttu-id="bc211-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="bc211-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="bc211-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="bc211-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc211-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc211-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc211-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc211-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bc211-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc211-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc211-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc211-115">Attributes</span></span>  
  
|<span data-ttu-id="bc211-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc211-116">Attribute</span></span>|<span data-ttu-id="bc211-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc211-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc211-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="bc211-118">activityName</span></span>|<span data-ttu-id="bc211-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="bc211-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="bc211-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="bc211-120">childActivityName</span></span>|<span data-ttu-id="bc211-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="bc211-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc211-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc211-122">Child Elements</span></span>  
 <span data-ttu-id="bc211-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bc211-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc211-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc211-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bc211-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc211-125">Element</span></span>|<span data-ttu-id="bc211-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc211-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc211-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="bc211-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="bc211-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="bc211-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="bc211-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="bc211-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc211-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc211-130">See Also</span></span>  
 <span data-ttu-id="bc211-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bc211-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="bc211-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bc211-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="bc211-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bc211-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bc211-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="bc211-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
