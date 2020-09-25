---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: efd1e4e54223ff9f5d60b4087fbe5b6bebf1af2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189578"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="cb60e-101">Representa uma consulta que é usada para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cb60e-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="cb60e-102">A consulta é necessária para um participante de rastreamento assinar os registros de continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="cb60e-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="cb60e-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cb60e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="cb60e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb60e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb60e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb60e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cb60e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cb60e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb60e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb60e-107">Attributes</span></span>  
  
|<span data-ttu-id="cb60e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cb60e-108">Attribute</span></span>|<span data-ttu-id="cb60e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb60e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb60e-110">name</span><span class="sxs-lookup"><span data-stu-id="cb60e-110">name</span></span>|<span data-ttu-id="cb60e-111">Uma cadeia de caracteres que especifica o nome do registro para assinar o indicador.</span><span class="sxs-lookup"><span data-stu-id="cb60e-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb60e-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cb60e-112">Child Elements</span></span>  

 <span data-ttu-id="cb60e-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cb60e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb60e-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb60e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cb60e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb60e-115">Element</span></span>|<span data-ttu-id="cb60e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb60e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="cb60e-117">Representa uma coleção de consultas que são usados para controlar a continuação de um indicador dentro de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cb60e-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb60e-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb60e-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cb60e-119">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="cb60e-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cb60e-120">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="cb60e-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
