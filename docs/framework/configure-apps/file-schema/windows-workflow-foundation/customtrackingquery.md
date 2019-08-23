---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9605f5d050baf046ff3c549c19191934299a65e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945747"
---
# <a name="customtrackingquery"></a><span data-ttu-id="45ae5-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="45ae5-101">\<customTrackingQuery></span></span>
<span data-ttu-id="45ae5-102">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="45ae5-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="45ae5-103">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="45ae5-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="45ae5-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="45ae5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="45ae5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="45ae5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="45ae5-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="45ae5-106">\<tracking></span></span>  
<span data-ttu-id="45ae5-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="45ae5-107">\<trackingProfile></span></span>  
<span data-ttu-id="45ae5-108">\<workflow></span><span class="sxs-lookup"><span data-stu-id="45ae5-108">\<workflow></span></span>  
<span data-ttu-id="45ae5-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="45ae5-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="45ae5-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="45ae5-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ae5-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45ae5-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45ae5-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45ae5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="45ae5-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="45ae5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45ae5-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="45ae5-114">Attributes</span></span>  
  
|<span data-ttu-id="45ae5-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="45ae5-115">Attribute</span></span>|<span data-ttu-id="45ae5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="45ae5-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45ae5-117">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="45ae5-117">activityName</span></span>|<span data-ttu-id="45ae5-118">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="45ae5-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="45ae5-119">name</span><span class="sxs-lookup"><span data-stu-id="45ae5-119">name</span></span>|<span data-ttu-id="45ae5-120">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="45ae5-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45ae5-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45ae5-121">Child Elements</span></span>  
 <span data-ttu-id="45ae5-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="45ae5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45ae5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45ae5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="45ae5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="45ae5-124">Element</span></span>|<span data-ttu-id="45ae5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="45ae5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45ae5-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="45ae5-126">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="45ae5-127">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="45ae5-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45ae5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45ae5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="45ae5-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45ae5-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="45ae5-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="45ae5-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
