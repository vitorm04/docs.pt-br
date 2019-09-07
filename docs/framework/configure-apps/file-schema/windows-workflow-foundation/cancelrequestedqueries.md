---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 0d08612ce5d74f4f7f505c538187ddecea610132
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398820"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="78ad7-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="78ad7-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="78ad7-102">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="78ad7-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="78ad7-103">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="78ad7-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="78ad7-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="78ad7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="78ad7-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="78ad7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="78ad7-106">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="78ad7-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="78ad7-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="78ad7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="78ad7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="78ad7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="78ad7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="78ad7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="78ad7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> cancelRequestedQueries**</span><span class="sxs-lookup"><span data-stu-id="78ad7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ad7-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78ad7-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78ad7-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="78ad7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="78ad7-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="78ad7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78ad7-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="78ad7-114">Attributes</span></span>  
 <span data-ttu-id="78ad7-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="78ad7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78ad7-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="78ad7-116">Child Elements</span></span>  
  
|<span data-ttu-id="78ad7-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="78ad7-117">Element</span></span>|<span data-ttu-id="78ad7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="78ad7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78ad7-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="78ad7-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="78ad7-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="78ad7-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78ad7-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="78ad7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="78ad7-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="78ad7-122">Element</span></span>|<span data-ttu-id="78ad7-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="78ad7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78ad7-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="78ad7-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="78ad7-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="78ad7-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78ad7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78ad7-126">See also</span></span>

- [<span data-ttu-id="78ad7-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="78ad7-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="78ad7-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="78ad7-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
