---
title: <customTrackingQueries>do WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855436"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="57dcd-102">\<customTrackingQueries>do WCF</span><span class="sxs-lookup"><span data-stu-id="57dcd-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="57dcd-103">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="57dcd-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="57dcd-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="57dcd-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="57dcd-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="57dcd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="57dcd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57dcd-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57dcd-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57dcd-107">Attributes and elements</span></span>

<span data-ttu-id="57dcd-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="57dcd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57dcd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="57dcd-109">Attributes</span></span>

<span data-ttu-id="57dcd-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="57dcd-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="57dcd-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="57dcd-111">Child elements</span></span>
  
|<span data-ttu-id="57dcd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="57dcd-112">Element</span></span>|<span data-ttu-id="57dcd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="57dcd-113">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="57dcd-114">Uma consulta que é usada para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="57dcd-114">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57dcd-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="57dcd-115">Parent elements</span></span>  
  
|<span data-ttu-id="57dcd-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="57dcd-116">Element</span></span>|<span data-ttu-id="57dcd-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="57dcd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="57dcd-118">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="57dcd-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57dcd-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="57dcd-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="57dcd-120">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="57dcd-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="57dcd-121">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="57dcd-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
