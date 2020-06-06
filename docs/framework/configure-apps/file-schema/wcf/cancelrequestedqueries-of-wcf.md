---
title: <cancelRequestedQueries>do WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850089"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="19f83-102">\<cancelRequestedQueries>do WCF</span><span class="sxs-lookup"><span data-stu-id="19f83-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="19f83-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="19f83-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="19f83-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="19f83-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="19f83-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="19f83-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="19f83-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19f83-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19f83-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="19f83-107">Attributes and elements</span></span>  

<span data-ttu-id="19f83-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="19f83-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19f83-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="19f83-109">Attributes</span></span>

<span data-ttu-id="19f83-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19f83-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="19f83-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="19f83-111">Child elements</span></span>
  
|<span data-ttu-id="19f83-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="19f83-112">Element</span></span>|<span data-ttu-id="19f83-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="19f83-113">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="19f83-114">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="19f83-114">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19f83-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="19f83-115">Parent elements</span></span>  
  
|<span data-ttu-id="19f83-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="19f83-116">Element</span></span>|<span data-ttu-id="19f83-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="19f83-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="19f83-118">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> propriedade.</span><span class="sxs-lookup"><span data-stu-id="19f83-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19f83-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="19f83-119">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="19f83-120">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="19f83-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="19f83-121">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="19f83-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
