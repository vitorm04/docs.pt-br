---
title: '&lt;faultPropagationQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: cf582fce4e899e62daa4f34f193a0232ec19a135
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149027"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="364c0-102">&lt;faultPropagationQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="364c0-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="364c0-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="364c0-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="364c0-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="364c0-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="364c0-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="364c0-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="364c0-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="364c0-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="364c0-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="364c0-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="364c0-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="364c0-108">\<system.serviceModel></span></span>  
<span data-ttu-id="364c0-109">\<Acompanhamento ></span><span class="sxs-lookup"><span data-stu-id="364c0-109">\<tracking></span></span>  
<span data-ttu-id="364c0-110">\<perfis de ></span><span class="sxs-lookup"><span data-stu-id="364c0-110">\<profiles></span></span>  
<span data-ttu-id="364c0-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="364c0-111">\<trackingProfile></span></span>  
<span data-ttu-id="364c0-112">\<workflow></span><span class="sxs-lookup"><span data-stu-id="364c0-112">\<workflow></span></span>  
<span data-ttu-id="364c0-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="364c0-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="364c0-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="364c0-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="364c0-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="364c0-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="364c0-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="364c0-116">Attributes and elements</span></span>

<span data-ttu-id="364c0-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="364c0-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="364c0-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="364c0-118">Attributes</span></span>  
  
|<span data-ttu-id="364c0-119">Atributo</span><span class="sxs-lookup"><span data-stu-id="364c0-119">Attribute</span></span>|<span data-ttu-id="364c0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="364c0-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="364c0-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="364c0-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="364c0-122">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="364c0-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="364c0-123">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="364c0-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="364c0-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="364c0-124">Child elements</span></span>

<span data-ttu-id="364c0-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="364c0-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="364c0-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="364c0-126">Parent elements</span></span>  
  
|<span data-ttu-id="364c0-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="364c0-127">Element</span></span>|<span data-ttu-id="364c0-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="364c0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="364c0-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="364c0-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="364c0-130">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="364c0-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="364c0-131">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="364c0-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="364c0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="364c0-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="364c0-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="364c0-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="364c0-134">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="364c0-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
