---
title: <activityScheduledQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850469"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="77865-102">\<activityScheduledQuery>do WCF</span><span class="sxs-lookup"><span data-stu-id="77865-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="77865-103">Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="77865-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="77865-104">A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.</span><span class="sxs-lookup"><span data-stu-id="77865-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="77865-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="77865-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="77865-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77865-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77865-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="77865-107">Attributes and elements</span></span>  

<span data-ttu-id="77865-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="77865-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77865-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="77865-109">Attributes</span></span>  
  
|<span data-ttu-id="77865-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="77865-110">Attribute</span></span>|<span data-ttu-id="77865-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="77865-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="77865-112">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="77865-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="77865-113">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="77865-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77865-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="77865-114">Child elements</span></span>

<span data-ttu-id="77865-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="77865-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="77865-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="77865-116">Parent elements</span></span>  
  
|<span data-ttu-id="77865-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="77865-117">Element</span></span>|<span data-ttu-id="77865-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="77865-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="77865-119">Uma coleção de consultas que são usadas para rastrear uma atividade agendada para execução por uma atividade pai.</span><span class="sxs-lookup"><span data-stu-id="77865-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77865-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="77865-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="77865-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="77865-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="77865-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="77865-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
