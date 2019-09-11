---
title: <activityStateQueries>do WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850577"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="65566-102">\<activityStateQueries > do WCF</span><span class="sxs-lookup"><span data-stu-id="65566-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="65566-103">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65566-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="65566-104">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65566-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="65566-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="65566-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="65566-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="65566-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="65566-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="65566-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="65566-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65566-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="65566-109">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="65566-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="65566-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="65566-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="65566-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<perfis >** </span><span class="sxs-lookup"><span data-stu-id="65566-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="65566-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="65566-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="65566-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="65566-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="65566-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> activityStateQueries**</span><span class="sxs-lookup"><span data-stu-id="65566-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65566-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65566-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="65566-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="65566-116">Attributes and elements</span></span>

<span data-ttu-id="65566-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="65566-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="65566-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="65566-118">Attributes</span></span>  

<span data-ttu-id="65566-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="65566-119">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="65566-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="65566-120">Child elements</span></span>

|<span data-ttu-id="65566-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="65566-121">Element</span></span>|<span data-ttu-id="65566-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="65566-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65566-123">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="65566-123">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="65566-124">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="65566-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="65566-125">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="65566-125">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="65566-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="65566-126">Parent elements</span></span>

|<span data-ttu-id="65566-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="65566-127">Element</span></span>|<span data-ttu-id="65566-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="65566-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65566-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="65566-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="65566-130">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="65566-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="65566-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65566-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="65566-132">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="65566-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="65566-133">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="65566-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
