---
title: <cancelRequestedQuery> do WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: bd6157e63761efa954744ab08ea6c66535def514
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281327"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="f56d0-102">\<cancelRequestedQuery> of WCF</span><span class="sxs-lookup"><span data-stu-id="f56d0-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="f56d0-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f56d0-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f56d0-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="f56d0-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="f56d0-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f56d0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="f56d0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f56d0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f56d0-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="f56d0-107">\<tracking></span></span>  
<span data-ttu-id="f56d0-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="f56d0-108">\<profiles></span></span>  
<span data-ttu-id="f56d0-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f56d0-109">\<trackingProfile></span></span>  
<span data-ttu-id="f56d0-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f56d0-110">\<workflow></span></span>  
<span data-ttu-id="f56d0-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="f56d0-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="f56d0-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="f56d0-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f56d0-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f56d0-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f56d0-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f56d0-114">Attributes and elements</span></span>

<span data-ttu-id="f56d0-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f56d0-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f56d0-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="f56d0-116">Attributes</span></span>  
  
|<span data-ttu-id="f56d0-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="f56d0-117">Attribute</span></span>|<span data-ttu-id="f56d0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f56d0-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="f56d0-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="f56d0-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="f56d0-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="f56d0-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f56d0-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f56d0-121">Child elements</span></span>

<span data-ttu-id="f56d0-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f56d0-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="f56d0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f56d0-123">Parent elements</span></span>
  
|<span data-ttu-id="f56d0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f56d0-124">Element</span></span>|<span data-ttu-id="f56d0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f56d0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f56d0-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="f56d0-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="f56d0-127">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f56d0-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f56d0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f56d0-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f56d0-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f56d0-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f56d0-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="f56d0-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
