---
title: '&lt;cancelRequestedQuery&gt; de WCF'
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 72fd23097760375738c2116b4535940873436986
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498262"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="f922f-102">&lt;cancelRequestedQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="f922f-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>

<span data-ttu-id="f922f-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f922f-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f922f-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="f922f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="f922f-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f922f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="f922f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f922f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f922f-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="f922f-107">\<tracking></span></span>  
<span data-ttu-id="f922f-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="f922f-108">\<profiles></span></span>  
<span data-ttu-id="f922f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f922f-109">\<trackingProfile></span></span>  
<span data-ttu-id="f922f-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f922f-110">\<workflow></span></span>  
<span data-ttu-id="f922f-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="f922f-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="f922f-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="f922f-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f922f-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f922f-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f922f-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f922f-114">Attributes and elements</span></span>

<span data-ttu-id="f922f-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f922f-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f922f-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="f922f-116">Attributes</span></span>  
  
|<span data-ttu-id="f922f-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="f922f-117">Attribute</span></span>|<span data-ttu-id="f922f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f922f-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="f922f-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="f922f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="f922f-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="f922f-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f922f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f922f-121">Child elements</span></span>

<span data-ttu-id="f922f-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f922f-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="f922f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f922f-123">Parent elements</span></span>
  
|<span data-ttu-id="f922f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f922f-124">Element</span></span>|<span data-ttu-id="f922f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f922f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f922f-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="f922f-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="f922f-127">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f922f-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f922f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f922f-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f922f-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f922f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f922f-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f922f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
