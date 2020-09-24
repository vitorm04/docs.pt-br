---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 936267f7d61dfd09af45ddb96b4406c92c30b3b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148770"
---
# \<activityScheduledQueries>

<span data-ttu-id="2b5d7-101">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="2b5d7-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2b5d7-102">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="2b5d7-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="2b5d7-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2b5d7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="2b5d7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b5d7-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b5d7-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2b5d7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2b5d7-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2b5d7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b5d7-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="2b5d7-107">Attributes</span></span>  

 <span data-ttu-id="2b5d7-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2b5d7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b5d7-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2b5d7-109">Child Elements</span></span>  
  
|<span data-ttu-id="2b5d7-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b5d7-110">Element</span></span>|<span data-ttu-id="2b5d7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b5d7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="2b5d7-112">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="2b5d7-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b5d7-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2b5d7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2b5d7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b5d7-114">Element</span></span>|<span data-ttu-id="2b5d7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b5d7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="2b5d7-116">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="2b5d7-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b5d7-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b5d7-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2b5d7-118">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2b5d7-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2b5d7-119">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="2b5d7-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
