---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5f2e46d5e4cdd64c37219476790b9ff92c606b6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215307"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="06f6f-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="06f6f-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="06f6f-102">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="06f6f-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="06f6f-103">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="06f6f-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="06f6f-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="06f6f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="06f6f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="06f6f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="06f6f-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="06f6f-106">\<tracking></span></span>  
<span data-ttu-id="06f6f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="06f6f-107">\<trackingProfile></span></span>  
<span data-ttu-id="06f6f-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="06f6f-108">\<workflow></span></span>  
<span data-ttu-id="06f6f-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="06f6f-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="06f6f-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="06f6f-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f6f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06f6f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06f6f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="06f6f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="06f6f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="06f6f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06f6f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="06f6f-114">Attributes</span></span>  
  
|<span data-ttu-id="06f6f-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="06f6f-115">Attribute</span></span>|<span data-ttu-id="06f6f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="06f6f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06f6f-117">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="06f6f-117">activityName</span></span>|<span data-ttu-id="06f6f-118">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="06f6f-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="06f6f-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="06f6f-119">childActivityName</span></span>|<span data-ttu-id="06f6f-120">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="06f6f-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06f6f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06f6f-121">Child Elements</span></span>  
 <span data-ttu-id="06f6f-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="06f6f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06f6f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="06f6f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="06f6f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="06f6f-124">Element</span></span>|<span data-ttu-id="06f6f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="06f6f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06f6f-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="06f6f-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="06f6f-127">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="06f6f-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="06f6f-128">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="06f6f-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06f6f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06f6f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="06f6f-130">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="06f6f-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="06f6f-131">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="06f6f-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
