---
title: '&lt;customTrackingQueries&gt; de WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 11ad4281d2925a48508c6a3e8258b0b1cd49a326
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749680"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="ec6ff-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="ec6ff-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="ec6ff-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="ec6ff-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ec6ff-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ec6ff-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ec6ff-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ec6ff-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="ec6ff-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ec6ff-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ec6ff-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="ec6ff-107">\<tracking></span></span>  
<span data-ttu-id="ec6ff-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ec6ff-108">\<trackingProfile></span></span>  
<span data-ttu-id="ec6ff-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ec6ff-109">\<workflow></span></span>  
<span data-ttu-id="ec6ff-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ec6ff-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec6ff-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec6ff-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec6ff-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec6ff-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ec6ff-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec6ff-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec6ff-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec6ff-114">Attributes</span></span>  
 <span data-ttu-id="ec6ff-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ec6ff-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec6ff-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec6ff-116">Child Elements</span></span>  
  
|<span data-ttu-id="ec6ff-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec6ff-117">Element</span></span>|<span data-ttu-id="ec6ff-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec6ff-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec6ff-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="ec6ff-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="ec6ff-120">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="ec6ff-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec6ff-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec6ff-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ec6ff-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec6ff-122">Element</span></span>|<span data-ttu-id="ec6ff-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec6ff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec6ff-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ec6ff-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ec6ff-125">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ec6ff-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec6ff-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec6ff-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="ec6ff-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ec6ff-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ec6ff-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ec6ff-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
