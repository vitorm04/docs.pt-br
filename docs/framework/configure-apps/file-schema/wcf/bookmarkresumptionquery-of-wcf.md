---
title: '&lt;bookmarkResumptionQuery&gt; of WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3240fcf026869aee7540c0e792ccd81e2592e620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="1a6ea-102">&lt;bookmarkResumptionQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="1a6ea-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="1a6ea-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1a6ea-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1a6ea-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="1a6ea-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="1a6ea-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1a6ea-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="1a6ea-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1a6ea-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-107">\<tracking></span></span>  
<span data-ttu-id="1a6ea-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-108">\<trackingProfile></span></span>  
<span data-ttu-id="1a6ea-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-109">\<workflow></span></span>  
<span data-ttu-id="1a6ea-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="1a6ea-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6ea-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a6ea-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a6ea-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1a6ea-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1a6ea-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1a6ea-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a6ea-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="1a6ea-115">Attributes</span></span>  
  
|<span data-ttu-id="1a6ea-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="1a6ea-116">Attribute</span></span>|<span data-ttu-id="1a6ea-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a6ea-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a6ea-118">name</span><span class="sxs-lookup"><span data-stu-id="1a6ea-118">name</span></span>|<span data-ttu-id="1a6ea-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="1a6ea-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a6ea-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1a6ea-120">Child Elements</span></span>  
 <span data-ttu-id="1a6ea-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1a6ea-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a6ea-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1a6ea-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1a6ea-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1a6ea-123">Element</span></span>|<span data-ttu-id="1a6ea-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a6ea-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a6ea-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="1a6ea-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="1a6ea-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1a6ea-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a6ea-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a6ea-127">See Also</span></span>  
 <span data-ttu-id="1a6ea-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1a6ea-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1a6ea-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1a6ea-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="1a6ea-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1a6ea-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1a6ea-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="1a6ea-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
