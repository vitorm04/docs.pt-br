---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 6e91078a24a950c6de027d57e3883e38f19447d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945448"
---
# <a name="activitystatequeries"></a><span data-ttu-id="94f7e-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="94f7e-101">\<activityStateQueries></span></span>
<span data-ttu-id="94f7e-102">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="94f7e-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="94f7e-103">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="94f7e-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="94f7e-104">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="94f7e-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="94f7e-105">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="94f7e-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="94f7e-106">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="94f7e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="94f7e-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="94f7e-107">\<system.serviceModel></span></span>  
<span data-ttu-id="94f7e-108">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="94f7e-108">\<tracking></span></span>  
<span data-ttu-id="94f7e-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="94f7e-109">\<trackingProfile></span></span>  
<span data-ttu-id="94f7e-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="94f7e-110">\<workflow></span></span>  
<span data-ttu-id="94f7e-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="94f7e-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f7e-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94f7e-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94f7e-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94f7e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="94f7e-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94f7e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94f7e-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="94f7e-115">Attributes</span></span>  
 <span data-ttu-id="94f7e-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="94f7e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94f7e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94f7e-117">Child Elements</span></span>  
  
|<span data-ttu-id="94f7e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="94f7e-118">Element</span></span>|<span data-ttu-id="94f7e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="94f7e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94f7e-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="94f7e-120">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="94f7e-121">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="94f7e-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="94f7e-122">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="94f7e-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94f7e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94f7e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="94f7e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="94f7e-124">Element</span></span>|<span data-ttu-id="94f7e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="94f7e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94f7e-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="94f7e-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="94f7e-127">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="94f7e-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94f7e-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94f7e-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="94f7e-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="94f7e-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="94f7e-130">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="94f7e-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
