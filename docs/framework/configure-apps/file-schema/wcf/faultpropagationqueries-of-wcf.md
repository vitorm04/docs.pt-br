---
title: <faultPropagationQueries>do WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855271"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="0b993-102">\<faultPropagationQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="0b993-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="0b993-103">Representa uma coleção de consultas que são usadas para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0b993-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0b993-104">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0b993-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="0b993-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0b993-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0b993-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="0b993-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="0b993-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0b993-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0b993-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0b993-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0b993-109">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0b993-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0b993-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0b993-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="0b993-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="0b993-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="0b993-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0b993-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="0b993-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0b993-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="0b993-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> faultPropagationQueries**</span><span class="sxs-lookup"><span data-stu-id="0b993-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b993-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b993-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b993-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b993-116">Attributes and elements</span></span>

<span data-ttu-id="0b993-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b993-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="0b993-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b993-118">Attributes</span></span>

<span data-ttu-id="0b993-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b993-119">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="0b993-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b993-120">Child elements</span></span>

|<span data-ttu-id="0b993-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b993-121">Element</span></span>|<span data-ttu-id="0b993-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b993-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b993-123">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="0b993-123">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="0b993-124">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0b993-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0b993-125">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0b993-125">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b993-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b993-126">Parent elements</span></span>  
  
|<span data-ttu-id="0b993-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b993-127">Element</span></span>|<span data-ttu-id="0b993-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b993-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b993-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0b993-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="0b993-130">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0b993-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b993-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b993-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0b993-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0b993-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0b993-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0b993-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
