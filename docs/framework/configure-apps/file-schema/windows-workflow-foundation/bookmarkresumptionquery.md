---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: e43ba66e2c3ccfbb723b1eea8ef6774ad3f9f2aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140030"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="af4fc-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="af4fc-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="af4fc-102">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af4fc-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="af4fc-103">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="af4fc-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="af4fc-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="af4fc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="af4fc-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="af4fc-105">\<system.serviceModel></span></span>  
<span data-ttu-id="af4fc-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="af4fc-106">\<tracking></span></span>  
<span data-ttu-id="af4fc-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="af4fc-107">\<trackingProfile></span></span>  
<span data-ttu-id="af4fc-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="af4fc-108">\<workflow></span></span>  
<span data-ttu-id="af4fc-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="af4fc-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="af4fc-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="af4fc-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af4fc-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af4fc-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af4fc-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af4fc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="af4fc-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="af4fc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af4fc-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="af4fc-114">Attributes</span></span>  
  
|<span data-ttu-id="af4fc-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="af4fc-115">Attribute</span></span>|<span data-ttu-id="af4fc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="af4fc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af4fc-117">name</span><span class="sxs-lookup"><span data-stu-id="af4fc-117">name</span></span>|<span data-ttu-id="af4fc-118">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="af4fc-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af4fc-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="af4fc-119">Child Elements</span></span>  
 <span data-ttu-id="af4fc-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="af4fc-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af4fc-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="af4fc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="af4fc-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="af4fc-122">Element</span></span>|<span data-ttu-id="af4fc-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="af4fc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af4fc-124">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="af4fc-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="af4fc-125">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af4fc-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af4fc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af4fc-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="af4fc-127">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="af4fc-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="af4fc-128">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="af4fc-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
