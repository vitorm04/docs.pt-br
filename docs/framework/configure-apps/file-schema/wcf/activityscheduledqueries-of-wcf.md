---
title: <activityScheduledQueries> do WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 86f196437b2230d6541570aa8994d99e7b340f66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151188"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="8ac24-102">\<activityScheduledQueries> do WCF</span><span class="sxs-lookup"><span data-stu-id="8ac24-102">\<activityScheduledQueries> of WCF</span></span>

<span data-ttu-id="8ac24-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="8ac24-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="8ac24-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="8ac24-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="8ac24-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8ac24-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="8ac24-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ac24-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ac24-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8ac24-107">Attributes and elements</span></span>  

<span data-ttu-id="8ac24-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8ac24-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ac24-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8ac24-109">Attributes</span></span>  

<span data-ttu-id="8ac24-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8ac24-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ac24-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8ac24-111">Child elements</span></span>  
  
|<span data-ttu-id="8ac24-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ac24-112">Element</span></span>|<span data-ttu-id="8ac24-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ac24-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="8ac24-114">Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="8ac24-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ac24-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8ac24-115">Parent elements</span></span>  
  
|<span data-ttu-id="8ac24-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ac24-116">Element</span></span>|<span data-ttu-id="8ac24-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ac24-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="8ac24-118">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ac24-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ac24-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ac24-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="8ac24-120">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8ac24-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8ac24-121">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="8ac24-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
