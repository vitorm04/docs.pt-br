---
title: '&lt;bookmarkResumptionQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: f0721e7e14d543b1ff212fe59ed6a2de0a8a9968
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308372"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="8b17f-102">&lt;bookmarkResumptionQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="8b17f-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>

<span data-ttu-id="8b17f-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8b17f-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="8b17f-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="8b17f-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="8b17f-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8b17f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="8b17f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8b17f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8b17f-107">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="8b17f-107">\<tracking></span></span>  
<span data-ttu-id="8b17f-108">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="8b17f-108">\<profiles></span></span>  
<span data-ttu-id="8b17f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8b17f-109">\<trackingProfile></span></span>  
<span data-ttu-id="8b17f-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="8b17f-110">\<workflow></span></span>  
<span data-ttu-id="8b17f-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="8b17f-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="8b17f-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="8b17f-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b17f-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b17f-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="8b17f-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b17f-114">Attributes and elements</span></span>

<span data-ttu-id="8b17f-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b17f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b17f-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b17f-116">Attributes</span></span>  
  
|<span data-ttu-id="8b17f-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b17f-117">Attribute</span></span>|<span data-ttu-id="8b17f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b17f-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8b17f-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="8b17f-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b17f-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b17f-120">Child elements</span></span>

<span data-ttu-id="8b17f-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8b17f-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="8b17f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b17f-122">Parent elements</span></span>  
  
|<span data-ttu-id="8b17f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b17f-123">Element</span></span>|<span data-ttu-id="8b17f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b17f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b17f-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="8b17f-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="8b17f-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8b17f-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b17f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b17f-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8b17f-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8b17f-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8b17f-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="8b17f-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
