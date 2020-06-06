---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152203"
---
# \<customTrackingQuery>
<span data-ttu-id="d0734-101">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="d0734-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d0734-102">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d0734-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d0734-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d0734-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="d0734-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0734-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0734-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0734-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d0734-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0734-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0734-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0734-107">Attributes</span></span>  
  
|<span data-ttu-id="d0734-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0734-108">Attribute</span></span>|<span data-ttu-id="d0734-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0734-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0734-110">activityName</span><span class="sxs-lookup"><span data-stu-id="d0734-110">activityName</span></span>|<span data-ttu-id="d0734-111">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d0734-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="d0734-112">name</span><span class="sxs-lookup"><span data-stu-id="d0734-112">name</span></span>|<span data-ttu-id="d0734-113">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="d0734-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0734-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0734-114">Child Elements</span></span>  
 <span data-ttu-id="d0734-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d0734-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0734-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0734-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d0734-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0734-117">Element</span></span>|<span data-ttu-id="d0734-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0734-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="d0734-119">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="d0734-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0734-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0734-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d0734-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d0734-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d0734-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d0734-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
