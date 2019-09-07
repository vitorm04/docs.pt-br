---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: bc0cc5fd027da45994269b149b72496fa03becef
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398727"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="e29df-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e29df-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="e29df-102">Representa uma coleção de consultas que são usadas para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e29df-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e29df-103">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="e29df-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e29df-104">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e29df-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e29df-105">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="e29df-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e29df-106">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e29df-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e29df-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e29df-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e29df-108">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e29df-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e29df-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e29df-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e29df-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e29df-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e29df-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e29df-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e29df-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> faultPropagationQueries**</span><span class="sxs-lookup"><span data-stu-id="e29df-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="e29df-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e29df-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e29df-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e29df-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e29df-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e29df-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e29df-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="e29df-116">Attributes</span></span>  
 <span data-ttu-id="e29df-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e29df-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e29df-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e29df-118">Child Elements</span></span>  
  
|<span data-ttu-id="e29df-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e29df-119">Element</span></span>|<span data-ttu-id="e29df-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e29df-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e29df-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e29df-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="e29df-122">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e29df-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e29df-123">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="e29df-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e29df-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e29df-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e29df-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="e29df-125">Element</span></span>|<span data-ttu-id="e29df-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e29df-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e29df-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="e29df-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e29df-128">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="e29df-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e29df-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e29df-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e29df-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e29df-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e29df-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e29df-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
