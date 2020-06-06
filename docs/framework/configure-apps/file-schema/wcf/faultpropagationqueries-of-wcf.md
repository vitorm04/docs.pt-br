---
title: <faultPropagationQueries>do WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855271"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="38b7b-102">\<faultPropagationQueries>do WCF</span><span class="sxs-lookup"><span data-stu-id="38b7b-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="38b7b-103">Representa uma coleção de consultas que são usadas para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="38b7b-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="38b7b-104">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="38b7b-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="38b7b-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="38b7b-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="38b7b-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="38b7b-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="38b7b-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="38b7b-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="38b7b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38b7b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38b7b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38b7b-109">Attributes and elements</span></span>

<span data-ttu-id="38b7b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38b7b-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="38b7b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="38b7b-111">Attributes</span></span>

<span data-ttu-id="38b7b-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="38b7b-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="38b7b-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38b7b-113">Child elements</span></span>

|<span data-ttu-id="38b7b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="38b7b-114">Element</span></span>|<span data-ttu-id="38b7b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="38b7b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="38b7b-116">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="38b7b-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="38b7b-117">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="38b7b-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38b7b-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38b7b-118">Parent elements</span></span>  
  
|<span data-ttu-id="38b7b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="38b7b-119">Element</span></span>|<span data-ttu-id="38b7b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="38b7b-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="38b7b-121">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="38b7b-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38b7b-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="38b7b-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="38b7b-123">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="38b7b-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="38b7b-124">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="38b7b-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
