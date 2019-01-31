---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 4e525bc4c77649a6c6d70ddb2408b6ecce4a0f09
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263753"
---
# <a name="customtrackingquery"></a><span data-ttu-id="3869a-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="3869a-101">\<customTrackingQuery></span></span>
<span data-ttu-id="3869a-102">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="3869a-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="3869a-103">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3869a-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="3869a-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3869a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3869a-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3869a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3869a-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3869a-106">\<tracking></span></span>  
<span data-ttu-id="3869a-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3869a-107">\<trackingProfile></span></span>  
<span data-ttu-id="3869a-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="3869a-108">\<workflow></span></span>  
<span data-ttu-id="3869a-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="3869a-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="3869a-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="3869a-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3869a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3869a-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3869a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3869a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3869a-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3869a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3869a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="3869a-114">Attributes</span></span>  
  
|<span data-ttu-id="3869a-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="3869a-115">Attribute</span></span>|<span data-ttu-id="3869a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3869a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3869a-117">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="3869a-117">activityName</span></span>|<span data-ttu-id="3869a-118">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3869a-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="3869a-119">name</span><span class="sxs-lookup"><span data-stu-id="3869a-119">name</span></span>|<span data-ttu-id="3869a-120">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="3869a-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3869a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3869a-121">Child Elements</span></span>  
 <span data-ttu-id="3869a-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3869a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3869a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3869a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3869a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="3869a-124">Element</span></span>|<span data-ttu-id="3869a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="3869a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3869a-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="3869a-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="3869a-127">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="3869a-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3869a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3869a-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3869a-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3869a-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3869a-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="3869a-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
