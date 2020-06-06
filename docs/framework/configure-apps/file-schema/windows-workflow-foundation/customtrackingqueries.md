---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152255"
---
# \<customTrackingQueries>
<span data-ttu-id="92897-101">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="92897-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="92897-102">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="92897-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="92897-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="92897-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="92897-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92897-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92897-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="92897-105">Attributes and Elements</span></span>  
 <span data-ttu-id="92897-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="92897-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92897-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="92897-107">Attributes</span></span>  
 <span data-ttu-id="92897-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="92897-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92897-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="92897-109">Child Elements</span></span>  
  
|<span data-ttu-id="92897-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="92897-110">Element</span></span>|<span data-ttu-id="92897-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="92897-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="92897-112">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="92897-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92897-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="92897-113">Parent Elements</span></span>  
  
|<span data-ttu-id="92897-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="92897-114">Element</span></span>|<span data-ttu-id="92897-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="92897-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="92897-116">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="92897-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92897-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="92897-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="92897-118">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="92897-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="92897-119">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="92897-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
