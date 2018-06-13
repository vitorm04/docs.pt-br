---
title: '&lt;bookmarkResumptionQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 083b42efdd2b10dad870b6590fc20331a090f8aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748250"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="49b5b-102">&lt;bookmarkResumptionQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="49b5b-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="49b5b-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="49b5b-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="49b5b-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="49b5b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="49b5b-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="49b5b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="49b5b-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="49b5b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="49b5b-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="49b5b-107">\<tracking></span></span>  
<span data-ttu-id="49b5b-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="49b5b-108">\<trackingProfile></span></span>  
<span data-ttu-id="49b5b-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="49b5b-109">\<workflow></span></span>  
<span data-ttu-id="49b5b-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="49b5b-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="49b5b-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="49b5b-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b5b-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49b5b-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49b5b-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="49b5b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="49b5b-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="49b5b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49b5b-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="49b5b-115">Attributes</span></span>  
  
|<span data-ttu-id="49b5b-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="49b5b-116">Attribute</span></span>|<span data-ttu-id="49b5b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="49b5b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49b5b-118">name</span><span class="sxs-lookup"><span data-stu-id="49b5b-118">name</span></span>|<span data-ttu-id="49b5b-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="49b5b-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49b5b-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="49b5b-120">Child Elements</span></span>  
 <span data-ttu-id="49b5b-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="49b5b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49b5b-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="49b5b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="49b5b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="49b5b-123">Element</span></span>|<span data-ttu-id="49b5b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="49b5b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49b5b-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="49b5b-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="49b5b-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="49b5b-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49b5b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49b5b-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="49b5b-128">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="49b5b-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="49b5b-129">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="49b5b-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
