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
ms.workload: dotnet
ms.openlocfilehash: 0c9ad0f766256d6507775c2cca1b9d54b474abc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="b48e9-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b48e9-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="b48e9-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b48e9-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b48e9-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="b48e9-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="b48e9-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b48e9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b48e9-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b48e9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b48e9-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="b48e9-107">\<tracking></span></span>  
<span data-ttu-id="b48e9-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b48e9-108">\<trackingProfile></span></span>  
<span data-ttu-id="b48e9-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="b48e9-109">\<workflow></span></span>  
<span data-ttu-id="b48e9-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b48e9-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="b48e9-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="b48e9-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48e9-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b48e9-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b48e9-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b48e9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b48e9-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b48e9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b48e9-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b48e9-115">Attributes</span></span>  
  
|<span data-ttu-id="b48e9-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b48e9-116">Attribute</span></span>|<span data-ttu-id="b48e9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b48e9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b48e9-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="b48e9-118">activityName</span></span>|<span data-ttu-id="b48e9-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="b48e9-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b48e9-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b48e9-120">childActivityName</span></span>|<span data-ttu-id="b48e9-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="b48e9-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b48e9-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b48e9-122">Child Elements</span></span>  
 <span data-ttu-id="b48e9-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b48e9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b48e9-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b48e9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b48e9-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b48e9-125">Element</span></span>|<span data-ttu-id="b48e9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b48e9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b48e9-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b48e9-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="b48e9-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b48e9-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b48e9-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="b48e9-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b48e9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b48e9-130">See Also</span></span>  
 <span data-ttu-id="b48e9-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b48e9-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b48e9-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b48e9-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b48e9-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b48e9-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b48e9-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="b48e9-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
