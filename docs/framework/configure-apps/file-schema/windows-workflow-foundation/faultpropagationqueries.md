---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152125"
---
# \<faultPropagationQueries>
<span data-ttu-id="e24bb-101">Representa uma coleção de consultas que são usadas para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e24bb-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e24bb-102">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="e24bb-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e24bb-103">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e24bb-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e24bb-104">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="e24bb-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e24bb-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e24bb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="e24bb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e24bb-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e24bb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e24bb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e24bb-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e24bb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e24bb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e24bb-109">Attributes</span></span>  
 <span data-ttu-id="e24bb-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e24bb-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e24bb-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e24bb-111">Child Elements</span></span>  
  
|<span data-ttu-id="e24bb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e24bb-112">Element</span></span>|<span data-ttu-id="e24bb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e24bb-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="e24bb-114">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e24bb-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e24bb-115">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="e24bb-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e24bb-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e24bb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e24bb-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="e24bb-117">Element</span></span>|<span data-ttu-id="e24bb-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e24bb-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="e24bb-119">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="e24bb-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e24bb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="e24bb-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e24bb-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e24bb-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e24bb-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e24bb-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
