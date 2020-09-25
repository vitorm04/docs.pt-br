---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 047d13bc8477214fa1e3c9ffdbed6785b29da637
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189572"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="bf2e4-101">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bf2e4-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bf2e4-102">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="bf2e4-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="bf2e4-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bf2e4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="bf2e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf2e4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf2e4-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bf2e4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bf2e4-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bf2e4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf2e4-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf2e4-107">Attributes</span></span>  

 <span data-ttu-id="bf2e4-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bf2e4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf2e4-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf2e4-109">Child Elements</span></span>  
  
|<span data-ttu-id="bf2e4-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf2e4-110">Element</span></span>|<span data-ttu-id="bf2e4-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf2e4-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="bf2e4-112">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bf2e4-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bf2e4-113">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="bf2e4-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf2e4-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf2e4-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bf2e4-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf2e4-115">Element</span></span>|<span data-ttu-id="bf2e4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf2e4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="bf2e4-117">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="bf2e4-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf2e4-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="bf2e4-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bf2e4-119">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf2e4-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bf2e4-120">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="bf2e4-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
