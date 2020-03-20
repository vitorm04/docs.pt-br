---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152125"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="0158c-101">\<falhasPropagaçõesQueções></span><span class="sxs-lookup"><span data-stu-id="0158c-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="0158c-102">Representa uma coleção de consultas que são usadas para rastrear o manuseio de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0158c-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0158c-103">Esse evento ocorre cada vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0158c-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="0158c-104">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0158c-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0158c-105">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="0158c-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="0158c-106">Para obter mais informações sobre o rastreamento de consultas de perfil, consulte [Perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0158c-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0158c-107">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0158c-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0158c-108">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0158c-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0158c-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="0158c-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="0158c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="0158c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="0158c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0158c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="0158c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<falhasPropagaçãoQueries>**</span><span class="sxs-lookup"><span data-stu-id="0158c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0158c-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0158c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0158c-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0158c-114">Attributes and Elements</span></span>  
 <span data-ttu-id="0158c-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0158c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0158c-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="0158c-116">Attributes</span></span>  
 <span data-ttu-id="0158c-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0158c-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0158c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0158c-118">Child Elements</span></span>  
  
|<span data-ttu-id="0158c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="0158c-119">Element</span></span>|<span data-ttu-id="0158c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0158c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0158c-121">\<falhaPropagaçãoquery></span><span class="sxs-lookup"><span data-stu-id="0158c-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="0158c-122">Uma consulta que é usada para rastrear o manuseio de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0158c-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0158c-123">Esse evento ocorre cada vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0158c-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0158c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0158c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0158c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="0158c-125">Element</span></span>|<span data-ttu-id="0158c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="0158c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0158c-127">\<>de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0158c-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="0158c-128">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="0158c-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0158c-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="0158c-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0158c-130">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0158c-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0158c-131">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="0158c-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
