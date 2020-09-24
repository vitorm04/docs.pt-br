---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 207931f68303883c29161cc28a5fc1974d01b6b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148731"
---
# \<activityScheduledQuery>

<span data-ttu-id="611f7-101">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="611f7-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="611f7-102">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="611f7-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="611f7-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="611f7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="611f7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="611f7-104">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="611f7-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="611f7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="611f7-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="611f7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="611f7-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="611f7-107">Attributes</span></span>  
  
|<span data-ttu-id="611f7-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="611f7-108">Attribute</span></span>|<span data-ttu-id="611f7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="611f7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="611f7-110">activityName</span><span class="sxs-lookup"><span data-stu-id="611f7-110">activityName</span></span>|<span data-ttu-id="611f7-111">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="611f7-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="611f7-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="611f7-112">childActivityName</span></span>|<span data-ttu-id="611f7-113">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="611f7-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="611f7-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="611f7-114">Child Elements</span></span>  

 <span data-ttu-id="611f7-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="611f7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="611f7-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="611f7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="611f7-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="611f7-117">Element</span></span>|<span data-ttu-id="611f7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="611f7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="611f7-119">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="611f7-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="611f7-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="611f7-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="611f7-121">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="611f7-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="611f7-122">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="611f7-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
