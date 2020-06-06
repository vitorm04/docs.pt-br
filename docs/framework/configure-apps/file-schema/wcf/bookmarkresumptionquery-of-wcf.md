---
title: <bookmarkResumptionQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834001"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="efce6-102">\<bookmarkResumptionQuery>do WCF</span><span class="sxs-lookup"><span data-stu-id="efce6-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="efce6-103">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="efce6-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="efce6-104">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="efce6-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="efce6-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="efce6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="efce6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efce6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efce6-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="efce6-107">Attributes and elements</span></span>

<span data-ttu-id="efce6-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="efce6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efce6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="efce6-109">Attributes</span></span>  
  
|<span data-ttu-id="efce6-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="efce6-110">Attribute</span></span>|<span data-ttu-id="efce6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="efce6-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="efce6-112">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="efce6-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efce6-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="efce6-113">Child elements</span></span>

<span data-ttu-id="efce6-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="efce6-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="efce6-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="efce6-115">Parent elements</span></span>  
  
|<span data-ttu-id="efce6-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="efce6-116">Element</span></span>|<span data-ttu-id="efce6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="efce6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="efce6-118">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="efce6-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efce6-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="efce6-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="efce6-120">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="efce6-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="efce6-121">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="efce6-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
