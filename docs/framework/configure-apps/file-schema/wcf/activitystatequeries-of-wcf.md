---
title: <activityStateQueries>do WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850577"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="e11d8-102">\<activityStateQueries>do WCF</span><span class="sxs-lookup"><span data-stu-id="e11d8-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="e11d8-103">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e11d8-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="e11d8-104">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e11d8-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="e11d8-105">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="e11d8-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="e11d8-106">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="e11d8-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="e11d8-107">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e11d8-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="e11d8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e11d8-108">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="e11d8-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e11d8-109">Attributes and elements</span></span>

<span data-ttu-id="e11d8-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e11d8-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e11d8-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e11d8-111">Attributes</span></span>  

<span data-ttu-id="e11d8-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e11d8-112">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="e11d8-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e11d8-113">Child elements</span></span>

|<span data-ttu-id="e11d8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e11d8-114">Element</span></span>|<span data-ttu-id="e11d8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e11d8-115">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="e11d8-116">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e11d8-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e11d8-117">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="e11d8-117">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e11d8-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e11d8-118">Parent elements</span></span>

|<span data-ttu-id="e11d8-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e11d8-119">Element</span></span>|<span data-ttu-id="e11d8-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e11d8-120">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e11d8-121">Um elemento de configuração que contém todas as consultas de um fluxo de trabalho específico identificado pelo `activityDefinitionId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="e11d8-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e11d8-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="e11d8-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="e11d8-123">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e11d8-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e11d8-124">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="e11d8-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
