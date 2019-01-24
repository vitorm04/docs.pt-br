---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: a5eb00d1e094484e3ec01e0db18719ec50e4b953
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515057"
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="37c85-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="37c85-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="37c85-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="37c85-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="37c85-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="37c85-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="37c85-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="37c85-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="37c85-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37c85-106">\<system.serviceModel></span></span>  
<span data-ttu-id="37c85-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="37c85-107">\<tracking></span></span>  
<span data-ttu-id="37c85-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="37c85-108">\<trackingProfile></span></span>  
<span data-ttu-id="37c85-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="37c85-109">\<workflow></span></span>  
<span data-ttu-id="37c85-110">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="37c85-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="37c85-111">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="37c85-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c85-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37c85-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c85-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="37c85-113">Attributes and Elements</span></span>  
 <span data-ttu-id="37c85-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="37c85-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c85-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="37c85-115">Attributes</span></span>  
  
|<span data-ttu-id="37c85-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="37c85-116">Attribute</span></span>|<span data-ttu-id="37c85-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="37c85-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37c85-118">name</span><span class="sxs-lookup"><span data-stu-id="37c85-118">name</span></span>|<span data-ttu-id="37c85-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="37c85-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37c85-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="37c85-120">Child Elements</span></span>  
 <span data-ttu-id="37c85-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="37c85-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37c85-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="37c85-122">Parent Elements</span></span>  
  
|<span data-ttu-id="37c85-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="37c85-123">Element</span></span>|<span data-ttu-id="37c85-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="37c85-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c85-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="37c85-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="37c85-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="37c85-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37c85-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37c85-127">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="37c85-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="37c85-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="37c85-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="37c85-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
