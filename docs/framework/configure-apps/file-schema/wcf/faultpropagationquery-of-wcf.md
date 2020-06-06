---
title: <faultPropagationQuery>do WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855335"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="73a16-102">\<faultPropagationQuery>do WCF</span><span class="sxs-lookup"><span data-stu-id="73a16-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="73a16-103">Representa uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="73a16-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="73a16-104">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="73a16-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="73a16-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="73a16-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="73a16-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="73a16-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="73a16-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="73a16-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="73a16-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73a16-108">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73a16-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73a16-109">Attributes and elements</span></span>

<span data-ttu-id="73a16-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="73a16-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="73a16-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="73a16-111">Attributes</span></span>

|<span data-ttu-id="73a16-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="73a16-112">Attribute</span></span>|<span data-ttu-id="73a16-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="73a16-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="73a16-114">Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagaram a falha.</span><span class="sxs-lookup"><span data-stu-id="73a16-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="73a16-115">O padrão é \* , que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="73a16-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="73a16-116">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="73a16-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="73a16-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73a16-117">Child elements</span></span>

<span data-ttu-id="73a16-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="73a16-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="73a16-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="73a16-119">Parent elements</span></span>

|<span data-ttu-id="73a16-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="73a16-120">Element</span></span>|<span data-ttu-id="73a16-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="73a16-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="73a16-122">Representa uma lista de elementos de configuração que são usados para rastrear a manipulação de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="73a16-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="73a16-123">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="73a16-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="73a16-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="73a16-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="73a16-125">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="73a16-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="73a16-126">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="73a16-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
