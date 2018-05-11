---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e532ea482108c9a5cabe13a99afddca10f8341d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="79803-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="79803-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="79803-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="79803-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="79803-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="79803-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="79803-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="79803-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="79803-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="79803-106">\<system.serviceModel></span></span>  
<span data-ttu-id="79803-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="79803-107">\<tracking></span></span>  
<span data-ttu-id="79803-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="79803-108">\<trackingProfile></span></span>  
<span data-ttu-id="79803-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="79803-109">\<workflow></span></span>  
<span data-ttu-id="79803-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="79803-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="79803-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="79803-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79803-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79803-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79803-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="79803-113">Attributes and Elements</span></span>  
 <span data-ttu-id="79803-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="79803-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79803-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="79803-115">Attributes</span></span>  
  
|<span data-ttu-id="79803-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="79803-116">Attribute</span></span>|<span data-ttu-id="79803-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="79803-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79803-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="79803-118">activityName</span></span>|<span data-ttu-id="79803-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="79803-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="79803-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="79803-120">childActivityName</span></span>|<span data-ttu-id="79803-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="79803-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79803-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="79803-122">Child Elements</span></span>  
 <span data-ttu-id="79803-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="79803-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79803-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="79803-124">Parent Elements</span></span>  
  
|<span data-ttu-id="79803-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="79803-125">Element</span></span>|<span data-ttu-id="79803-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="79803-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79803-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="79803-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="79803-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="79803-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="79803-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="79803-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79803-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79803-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="79803-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="79803-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="79803-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="79803-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
