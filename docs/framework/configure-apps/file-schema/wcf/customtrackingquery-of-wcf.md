---
title: <customTrackingQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855423"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="ecfd9-102">\<customTrackingQuery>do WCF</span><span class="sxs-lookup"><span data-stu-id="ecfd9-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="ecfd9-103">Representa uma consulta que é usada para rastrear eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="ecfd9-104">A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="ecfd9-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ecfd9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="ecfd9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecfd9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecfd9-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ecfd9-107">Attributes and elements</span></span>  

<span data-ttu-id="ecfd9-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecfd9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ecfd9-109">Attributes</span></span>  
  
|<span data-ttu-id="ecfd9-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="ecfd9-110">Attribute</span></span>|<span data-ttu-id="ecfd9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecfd9-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="ecfd9-112">Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="ecfd9-113">Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecfd9-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ecfd9-114">Child elements</span></span>

<span data-ttu-id="ecfd9-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ecfd9-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ecfd9-116">Parent elements</span></span>

|<span data-ttu-id="ecfd9-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ecfd9-117">Element</span></span>|<span data-ttu-id="ecfd9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecfd9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="ecfd9-119">Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.</span><span class="sxs-lookup"><span data-stu-id="ecfd9-119">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="ecfd9-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="ecfd9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ecfd9-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ecfd9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ecfd9-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ecfd9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
