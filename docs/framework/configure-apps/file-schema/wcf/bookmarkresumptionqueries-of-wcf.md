---
title: <bookmarkResumptionQueries>do WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850133"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="dbda5-102">\<bookmarkResumptionQueries>do WCF</span><span class="sxs-lookup"><span data-stu-id="dbda5-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="dbda5-103">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dbda5-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="dbda5-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="dbda5-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="dbda5-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dbda5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="dbda5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbda5-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbda5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dbda5-107">Attributes and elements</span></span>  
  
<span data-ttu-id="dbda5-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dbda5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbda5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dbda5-109">Attributes</span></span>  
  
<span data-ttu-id="dbda5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dbda5-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dbda5-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dbda5-111">Child elements</span></span>  
  
|<span data-ttu-id="dbda5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="dbda5-112">Element</span></span>|<span data-ttu-id="dbda5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbda5-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="dbda5-114">Uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dbda5-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="dbda5-115">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="dbda5-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbda5-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dbda5-116">Parent elements</span></span>  
  
|<span data-ttu-id="dbda5-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="dbda5-117">Element</span></span>|<span data-ttu-id="dbda5-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbda5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="dbda5-119">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="dbda5-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbda5-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="dbda5-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dbda5-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="dbda5-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dbda5-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="dbda5-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
