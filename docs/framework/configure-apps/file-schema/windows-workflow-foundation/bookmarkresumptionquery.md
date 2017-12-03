---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bafb044d052692385e0be0f4dbb1271eca847b1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="5e828-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="5e828-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="5e828-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5e828-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="5e828-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="5e828-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="5e828-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5e828-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5e828-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e828-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5e828-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="5e828-107">\<tracking></span></span>  
<span data-ttu-id="5e828-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5e828-108">\<trackingProfile></span></span>  
<span data-ttu-id="5e828-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="5e828-109">\<workflow></span></span>  
<span data-ttu-id="5e828-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="5e828-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="5e828-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="5e828-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e828-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e828-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e828-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e828-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5e828-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e828-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e828-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e828-115">Attributes</span></span>  
  
|<span data-ttu-id="5e828-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e828-116">Attribute</span></span>|<span data-ttu-id="5e828-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e828-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e828-118">name</span><span class="sxs-lookup"><span data-stu-id="5e828-118">name</span></span>|<span data-ttu-id="5e828-119">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="5e828-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e828-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e828-120">Child Elements</span></span>  
 <span data-ttu-id="5e828-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e828-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e828-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e828-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5e828-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e828-123">Element</span></span>|<span data-ttu-id="5e828-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e828-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e828-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="5e828-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="5e828-126">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5e828-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e828-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e828-127">See Also</span></span>  
 <span data-ttu-id="5e828-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5e828-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="5e828-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5e828-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="5e828-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5e828-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5e828-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="5e828-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
