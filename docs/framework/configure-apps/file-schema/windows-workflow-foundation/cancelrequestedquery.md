---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a3d24536589288ce9585901f3d955075bc856c97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520302"
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="43f00-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="43f00-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="43f00-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="43f00-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="43f00-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="43f00-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="43f00-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="43f00-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="43f00-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="43f00-106">\<system.serviceModel></span></span>  
<span data-ttu-id="43f00-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="43f00-107">\<tracking></span></span>  
<span data-ttu-id="43f00-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="43f00-108">\<trackingProfile></span></span>  
<span data-ttu-id="43f00-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="43f00-109">\<workflow></span></span>  
<span data-ttu-id="43f00-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="43f00-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="43f00-111">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="43f00-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f00-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43f00-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43f00-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43f00-113">Attributes and Elements</span></span>  
 <span data-ttu-id="43f00-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43f00-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43f00-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="43f00-115">Attributes</span></span>  
  
|<span data-ttu-id="43f00-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="43f00-116">Attribute</span></span>|<span data-ttu-id="43f00-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="43f00-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43f00-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="43f00-118">activityName</span></span>|<span data-ttu-id="43f00-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="43f00-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="43f00-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="43f00-120">childActivityName</span></span>|<span data-ttu-id="43f00-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="43f00-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43f00-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43f00-122">Child Elements</span></span>  
 <span data-ttu-id="43f00-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="43f00-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43f00-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43f00-124">Parent Elements</span></span>  
  
|<span data-ttu-id="43f00-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="43f00-125">Element</span></span>|<span data-ttu-id="43f00-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="43f00-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43f00-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="43f00-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="43f00-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="43f00-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="43f00-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="43f00-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43f00-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43f00-130">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="43f00-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="43f00-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="43f00-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="43f00-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
