---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 59a76ea772dc8d06c390e3bca9d531df5f11e5f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148718"
---
# \<customTrackingQuery>

<span data-ttu-id="69380-101">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="69380-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="69380-102">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="69380-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="69380-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="69380-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="69380-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="69380-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69380-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69380-105">Attributes and Elements</span></span>  

 <span data-ttu-id="69380-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69380-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69380-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="69380-107">Attributes</span></span>  
  
|<span data-ttu-id="69380-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="69380-108">Attribute</span></span>|<span data-ttu-id="69380-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="69380-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69380-110">activityName</span><span class="sxs-lookup"><span data-stu-id="69380-110">activityName</span></span>|<span data-ttu-id="69380-111">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="69380-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="69380-112">name</span><span class="sxs-lookup"><span data-stu-id="69380-112">name</span></span>|<span data-ttu-id="69380-113">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="69380-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69380-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69380-114">Child Elements</span></span>  

 <span data-ttu-id="69380-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="69380-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69380-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69380-116">Parent Elements</span></span>  
  
|<span data-ttu-id="69380-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="69380-117">Element</span></span>|<span data-ttu-id="69380-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="69380-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="69380-119">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="69380-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69380-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="69380-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="69380-121">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="69380-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="69380-122">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="69380-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
