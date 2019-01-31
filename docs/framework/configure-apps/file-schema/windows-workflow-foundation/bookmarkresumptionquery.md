---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 7fb298bcbc5b4bf5d699d3c79936ca3c15f67c0e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268178"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="186c2-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="186c2-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="186c2-102">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="186c2-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="186c2-103">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="186c2-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="186c2-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="186c2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="186c2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="186c2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="186c2-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="186c2-106">\<tracking></span></span>  
<span data-ttu-id="186c2-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="186c2-107">\<trackingProfile></span></span>  
<span data-ttu-id="186c2-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="186c2-108">\<workflow></span></span>  
<span data-ttu-id="186c2-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="186c2-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="186c2-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="186c2-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186c2-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="186c2-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="186c2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="186c2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="186c2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="186c2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="186c2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="186c2-114">Attributes</span></span>  
  
|<span data-ttu-id="186c2-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="186c2-115">Attribute</span></span>|<span data-ttu-id="186c2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="186c2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="186c2-117">name</span><span class="sxs-lookup"><span data-stu-id="186c2-117">name</span></span>|<span data-ttu-id="186c2-118">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="186c2-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="186c2-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="186c2-119">Child Elements</span></span>  
 <span data-ttu-id="186c2-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="186c2-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="186c2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="186c2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="186c2-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="186c2-122">Element</span></span>|<span data-ttu-id="186c2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="186c2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="186c2-124">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="186c2-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="186c2-125">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="186c2-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="186c2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="186c2-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="186c2-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="186c2-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="186c2-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="186c2-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
