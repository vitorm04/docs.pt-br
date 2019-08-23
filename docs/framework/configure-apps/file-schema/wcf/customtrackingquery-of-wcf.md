---
title: <customTrackingQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: b034727dc89b58794ec2834cb0ff39cd7e5f1dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919357"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="c5b66-102">\<customTrackingQuery > do WCF</span><span class="sxs-lookup"><span data-stu-id="c5b66-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="c5b66-103">Representa uma consulta que é usada para rastrear eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="c5b66-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="c5b66-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c5b66-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="c5b66-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c5b66-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c5b66-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5b66-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c5b66-107">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="c5b66-107">\<tracking></span></span>  
<span data-ttu-id="c5b66-108">\<perfis ></span><span class="sxs-lookup"><span data-stu-id="c5b66-108">\<profiles></span></span>  
<span data-ttu-id="c5b66-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c5b66-109">\<trackingProfile></span></span>  
<span data-ttu-id="c5b66-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c5b66-110">\<workflow></span></span>  
<span data-ttu-id="c5b66-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="c5b66-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="c5b66-112">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="c5b66-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b66-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5b66-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5b66-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5b66-114">Attributes and elements</span></span>  

<span data-ttu-id="c5b66-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5b66-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5b66-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5b66-116">Attributes</span></span>  
  
|<span data-ttu-id="c5b66-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="c5b66-117">Attribute</span></span>|<span data-ttu-id="c5b66-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5b66-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="c5b66-119">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c5b66-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="c5b66-120">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="c5b66-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5b66-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5b66-121">Child elements</span></span>

<span data-ttu-id="c5b66-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c5b66-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5b66-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5b66-123">Parent elements</span></span>

|<span data-ttu-id="c5b66-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5b66-124">Element</span></span>|<span data-ttu-id="c5b66-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5b66-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5b66-126">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="c5b66-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="c5b66-127">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="c5b66-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="c5b66-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5b66-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c5b66-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c5b66-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c5b66-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c5b66-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
