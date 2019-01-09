---
title: '&lt;bookmarkResumptionQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 6463404e17edff8eb1efe3f96e44b5b9997ffca3
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147805"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="5daa2-102">&lt;bookmarkResumptionQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="5daa2-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>

<span data-ttu-id="5daa2-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5daa2-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="5daa2-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="5daa2-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="5daa2-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5daa2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="5daa2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5daa2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5daa2-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="5daa2-107">\<tracking></span></span>  
<span data-ttu-id="5daa2-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="5daa2-108">\<profiles></span></span>  
<span data-ttu-id="5daa2-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5daa2-109">\<trackingProfile></span></span>  
<span data-ttu-id="5daa2-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5daa2-110">\<workflow></span></span>  
<span data-ttu-id="5daa2-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="5daa2-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="5daa2-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="5daa2-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5daa2-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5daa2-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5daa2-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5daa2-114">Attributes and elements</span></span>

<span data-ttu-id="5daa2-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5daa2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5daa2-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="5daa2-116">Attributes</span></span>  
  
|<span data-ttu-id="5daa2-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="5daa2-117">Attribute</span></span>|<span data-ttu-id="5daa2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5daa2-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5daa2-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="5daa2-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5daa2-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5daa2-120">Child elements</span></span>

<span data-ttu-id="5daa2-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5daa2-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="5daa2-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5daa2-122">Parent elements</span></span>  
  
|<span data-ttu-id="5daa2-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="5daa2-123">Element</span></span>|<span data-ttu-id="5daa2-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5daa2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5daa2-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="5daa2-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="5daa2-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5daa2-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5daa2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5daa2-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5daa2-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5daa2-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5daa2-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="5daa2-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
