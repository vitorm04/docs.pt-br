---
title: '&lt;customTrackingQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9ee5a4a25d379eafb936098597df1ec61ff09f0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725851"
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="5a628-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="5a628-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="5a628-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="5a628-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="5a628-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5a628-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="5a628-105">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5a628-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5a628-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5a628-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5a628-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="5a628-107">\<tracking></span></span>  
<span data-ttu-id="5a628-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5a628-108">\<trackingProfile></span></span>  
<span data-ttu-id="5a628-109">\<workflow></span><span class="sxs-lookup"><span data-stu-id="5a628-109">\<workflow></span></span>  
<span data-ttu-id="5a628-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="5a628-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="5a628-111">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="5a628-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a628-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a628-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a628-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5a628-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5a628-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5a628-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a628-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5a628-115">Attributes</span></span>  
  
|<span data-ttu-id="5a628-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5a628-116">Attribute</span></span>|<span data-ttu-id="5a628-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a628-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a628-118">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="5a628-118">activityName</span></span>|<span data-ttu-id="5a628-119">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5a628-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="5a628-120">name</span><span class="sxs-lookup"><span data-stu-id="5a628-120">name</span></span>|<span data-ttu-id="5a628-121">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="5a628-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a628-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5a628-122">Child Elements</span></span>  
 <span data-ttu-id="5a628-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5a628-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a628-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5a628-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5a628-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a628-125">Element</span></span>|<span data-ttu-id="5a628-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a628-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a628-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="5a628-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="5a628-128">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="5a628-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a628-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a628-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5a628-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5a628-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5a628-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="5a628-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
