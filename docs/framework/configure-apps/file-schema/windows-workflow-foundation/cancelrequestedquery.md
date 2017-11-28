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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e1697b245f9ab61cab3e4b26b1756259f0eba9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="188d5-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="188d5-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="188d5-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="188d5-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="188d5-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="188d5-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="188d5-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="188d5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="188d5-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="188d5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="188d5-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="188d5-107">\<tracking></span></span>  
<span data-ttu-id="188d5-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="188d5-108">\<trackingProfile></span></span>  
<span data-ttu-id="188d5-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="188d5-109">\<workflow></span></span>  
<span data-ttu-id="188d5-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="188d5-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="188d5-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="188d5-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="188d5-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="188d5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="188d5-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="188d5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="188d5-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="188d5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="188d5-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="188d5-115">Attributes</span></span>  
  
|<span data-ttu-id="188d5-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="188d5-116">Attribute</span></span>|<span data-ttu-id="188d5-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="188d5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="188d5-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="188d5-118">activityName</span></span>|<span data-ttu-id="188d5-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="188d5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="188d5-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="188d5-120">childActivityName</span></span>|<span data-ttu-id="188d5-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="188d5-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="188d5-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="188d5-122">Child Elements</span></span>  
 <span data-ttu-id="188d5-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="188d5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="188d5-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="188d5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="188d5-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="188d5-125">Element</span></span>|<span data-ttu-id="188d5-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="188d5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="188d5-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="188d5-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="188d5-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="188d5-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="188d5-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="188d5-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="188d5-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="188d5-130">See Also</span></span>  
 <span data-ttu-id="188d5-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="188d5-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="188d5-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="188d5-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="188d5-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="188d5-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="188d5-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="188d5-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
