---
title: '&lt;faultPropagationQuery&gt; of WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: fe3dd90a5c6b26537ab461b4bf4993df5be625a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747353"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="a526a-102">&lt;faultPropagationQuery&gt; of WCF</span><span class="sxs-lookup"><span data-stu-id="a526a-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="a526a-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="a526a-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a526a-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="a526a-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a526a-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="a526a-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a526a-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="a526a-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="a526a-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a526a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="a526a-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a526a-108">\<system.serviceModel></span></span>  
<span data-ttu-id="a526a-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="a526a-109">\<tracking></span></span>  
<span data-ttu-id="a526a-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a526a-110">\<trackingProfile></span></span>  
<span data-ttu-id="a526a-111">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a526a-111">\<workflow></span></span>  
<span data-ttu-id="a526a-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="a526a-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="a526a-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="a526a-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a526a-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a526a-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a526a-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a526a-115">Attributes and Elements</span></span>  
 <span data-ttu-id="a526a-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a526a-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a526a-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="a526a-117">Attributes</span></span>  
  
|<span data-ttu-id="a526a-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="a526a-118">Attribute</span></span>|<span data-ttu-id="a526a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a526a-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a526a-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="a526a-120">activityName</span></span>|<span data-ttu-id="a526a-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="a526a-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="a526a-122">O padrão é \*, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="a526a-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="a526a-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="a526a-123">faultHandlerActivityName</span></span>|<span data-ttu-id="a526a-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="a526a-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a526a-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a526a-125">Child Elements</span></span>  
 <span data-ttu-id="a526a-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a526a-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a526a-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a526a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a526a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="a526a-128">Element</span></span>|<span data-ttu-id="a526a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="a526a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a526a-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="a526a-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="a526a-131">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="a526a-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a526a-132">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="a526a-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a526a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a526a-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="a526a-134">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a526a-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a526a-135">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a526a-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
