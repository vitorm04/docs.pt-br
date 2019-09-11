---
title: <cancelRequestedQueries>do WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850089"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="99be4-102">\<cancelRequestedQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="99be4-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="99be4-103">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="99be4-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="99be4-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="99be4-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="99be4-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="99be4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="99be4-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="99be4-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99be4-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="99be4-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="99be4-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="99be4-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="99be4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="99be4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="99be4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="99be4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="99be4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="99be4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="99be4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> cancelRequestedQueries**</span><span class="sxs-lookup"><span data-stu-id="99be4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99be4-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99be4-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99be4-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99be4-114">Attributes and elements</span></span>  

<span data-ttu-id="99be4-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="99be4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99be4-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="99be4-116">Attributes</span></span>

<span data-ttu-id="99be4-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="99be4-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="99be4-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="99be4-118">Child elements</span></span>
  
|<span data-ttu-id="99be4-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="99be4-119">Element</span></span>|<span data-ttu-id="99be4-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="99be4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99be4-121">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="99be4-121">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="99be4-122">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="99be4-122">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99be4-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="99be4-123">Parent elements</span></span>  
  
|<span data-ttu-id="99be4-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="99be4-124">Element</span></span>|<span data-ttu-id="99be4-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="99be4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99be4-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="99be4-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="99be4-127">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> propriedade.</span><span class="sxs-lookup"><span data-stu-id="99be4-127">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99be4-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99be4-128">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="99be4-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="99be4-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="99be4-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="99be4-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
