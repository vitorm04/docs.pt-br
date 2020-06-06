---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398726"
---
# \<faultPropagationQuery>

<span data-ttu-id="94d4b-101">Representa uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="94d4b-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="94d4b-102">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="94d4b-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="94d4b-103">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="94d4b-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="94d4b-104">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="94d4b-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="94d4b-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="94d4b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="94d4b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94d4b-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="94d4b-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94d4b-107">Attributes and Elements</span></span>

<span data-ttu-id="94d4b-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94d4b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="94d4b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="94d4b-109">Attributes</span></span>

|<span data-ttu-id="94d4b-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="94d4b-110">Attribute</span></span>|<span data-ttu-id="94d4b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="94d4b-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="94d4b-112">activityName</span><span class="sxs-lookup"><span data-stu-id="94d4b-112">activityName</span></span>|<span data-ttu-id="94d4b-113">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagaram a falha.</span><span class="sxs-lookup"><span data-stu-id="94d4b-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="94d4b-114">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="94d4b-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="94d4b-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="94d4b-115">faultHandlerActivityName</span></span>|<span data-ttu-id="94d4b-116">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="94d4b-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="94d4b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94d4b-117">Child Elements</span></span>

<span data-ttu-id="94d4b-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="94d4b-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94d4b-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94d4b-119">Parent Elements</span></span>

|<span data-ttu-id="94d4b-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="94d4b-120">Element</span></span>|<span data-ttu-id="94d4b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="94d4b-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="94d4b-122">Representa uma lista de elementos de configuração que são usados para rastrear a manipulação de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="94d4b-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="94d4b-123">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="94d4b-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="94d4b-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="94d4b-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="94d4b-125">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="94d4b-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="94d4b-126">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="94d4b-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
