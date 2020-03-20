---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152281"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="e05b9-101">\<cancelarPedidoQuery></span><span class="sxs-lookup"><span data-stu-id="e05b9-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="e05b9-102">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e05b9-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e05b9-103">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="e05b9-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="e05b9-104">Para obter mais informações sobre o rastreamento de consultas de perfil, consulte [Perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e05b9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e05b9-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e05b9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e05b9-106">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e05b9-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e05b9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e05b9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e05b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e05b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e05b9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e05b9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e05b9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelarConsultas solicitadas>**](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="e05b9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="e05b9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelar>de Quequery Solicitado**</span><span class="sxs-lookup"><span data-stu-id="e05b9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e05b9-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e05b9-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e05b9-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e05b9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e05b9-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e05b9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e05b9-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="e05b9-115">Attributes</span></span>  
  
|<span data-ttu-id="e05b9-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="e05b9-116">Attribute</span></span>|<span data-ttu-id="e05b9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="e05b9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e05b9-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e05b9-118">activityName</span></span>|<span data-ttu-id="e05b9-119">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="e05b9-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e05b9-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e05b9-120">childActivityName</span></span>|<span data-ttu-id="e05b9-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="e05b9-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e05b9-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e05b9-122">Child Elements</span></span>  
 <span data-ttu-id="e05b9-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e05b9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e05b9-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e05b9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e05b9-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="e05b9-125">Element</span></span>|<span data-ttu-id="e05b9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e05b9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e05b9-127">\<falhaPropagaçãoquery></span><span class="sxs-lookup"><span data-stu-id="e05b9-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="e05b9-128">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e05b9-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e05b9-129">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="e05b9-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e05b9-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="e05b9-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e05b9-131">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e05b9-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e05b9-132">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e05b9-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
