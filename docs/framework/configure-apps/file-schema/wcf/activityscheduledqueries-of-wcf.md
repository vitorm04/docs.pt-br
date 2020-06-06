---
title: <activityScheduledQueries>do WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850500"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="a8f51-102">\<activityScheduledQueries>do WCF</span><span class="sxs-lookup"><span data-stu-id="a8f51-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="a8f51-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="a8f51-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a8f51-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="a8f51-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="a8f51-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a8f51-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="a8f51-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8f51-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8f51-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a8f51-107">Attributes and elements</span></span>  

<span data-ttu-id="a8f51-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a8f51-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8f51-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8f51-109">Attributes</span></span>  

<span data-ttu-id="a8f51-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8f51-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8f51-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a8f51-111">Child elements</span></span>  
  
|<span data-ttu-id="a8f51-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8f51-112">Element</span></span>|<span data-ttu-id="a8f51-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8f51-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="a8f51-114">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="a8f51-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8f51-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8f51-115">Parent elements</span></span>  
  
|<span data-ttu-id="a8f51-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8f51-116">Element</span></span>|<span data-ttu-id="a8f51-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8f51-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a8f51-118">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8f51-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8f51-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8f51-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="a8f51-120">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a8f51-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a8f51-121">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a8f51-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
