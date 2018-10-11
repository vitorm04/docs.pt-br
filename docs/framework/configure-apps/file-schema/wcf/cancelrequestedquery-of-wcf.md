---
title: '&lt;cancelRequestedQuery&gt; de WCF'
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 38d946a213131e8dcb6f4100d0ad67f7c167f342
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086395"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="eba56-102">&lt;cancelRequestedQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="eba56-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="eba56-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="eba56-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="eba56-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="eba56-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="eba56-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="eba56-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="eba56-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eba56-106">\<system.serviceModel></span></span>  
<span data-ttu-id="eba56-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="eba56-107">\<tracking></span></span>  
<span data-ttu-id="eba56-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eba56-108">\<trackingProfile></span></span>  
<span data-ttu-id="eba56-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="eba56-109">\<workflow></span></span>  
<span data-ttu-id="eba56-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="eba56-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="eba56-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="eba56-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba56-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eba56-112">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="eba56-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eba56-113">Attributes and Elements</span></span>  
 <span data-ttu-id="eba56-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eba56-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eba56-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="eba56-115">Attributes</span></span>  
  
|<span data-ttu-id="eba56-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="eba56-116">Attribute</span></span>|<span data-ttu-id="eba56-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="eba56-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eba56-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="eba56-118">activityName</span></span>|<span data-ttu-id="eba56-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="eba56-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="eba56-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="eba56-120">childActivityName</span></span>|<span data-ttu-id="eba56-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="eba56-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eba56-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eba56-122">Child Elements</span></span>  
 <span data-ttu-id="eba56-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eba56-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eba56-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eba56-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eba56-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="eba56-125">Element</span></span>|<span data-ttu-id="eba56-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="eba56-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eba56-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="eba56-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="eba56-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="eba56-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="eba56-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="eba56-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eba56-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eba56-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>     
 [<span data-ttu-id="eba56-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eba56-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="eba56-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="eba56-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
