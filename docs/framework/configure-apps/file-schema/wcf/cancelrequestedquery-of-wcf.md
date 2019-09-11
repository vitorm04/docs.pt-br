---
title: <cancelRequestedQuery>do WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850056"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="a20b3-102">\<cancelRequestedQuery> of WCF</span><span class="sxs-lookup"><span data-stu-id="a20b3-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="a20b3-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="a20b3-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a20b3-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="a20b3-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="a20b3-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a20b3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="a20b3-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a20b3-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a20b3-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a20b3-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a20b3-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a20b3-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a20b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="a20b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a20b3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a20b3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="a20b3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a20b3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="a20b3-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> cancelRequestedQueries**](cancelrequestedqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a20b3-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)</span></span>\
<span data-ttu-id="a20b3-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> cancelRequestedQuery**</span><span class="sxs-lookup"><span data-stu-id="a20b3-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a20b3-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a20b3-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a20b3-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a20b3-115">Attributes and elements</span></span>

<span data-ttu-id="a20b3-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a20b3-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a20b3-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="a20b3-117">Attributes</span></span>  
  
|<span data-ttu-id="a20b3-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="a20b3-118">Attribute</span></span>|<span data-ttu-id="a20b3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a20b3-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="a20b3-120">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="a20b3-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="a20b3-121">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="a20b3-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a20b3-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a20b3-122">Child elements</span></span>

<span data-ttu-id="a20b3-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a20b3-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="a20b3-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a20b3-124">Parent elements</span></span>
  
|<span data-ttu-id="a20b3-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="a20b3-125">Element</span></span>|<span data-ttu-id="a20b3-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="a20b3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a20b3-127">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a20b3-127">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="a20b3-128">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="a20b3-128">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a20b3-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a20b3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a20b3-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a20b3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a20b3-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a20b3-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
