---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398951"
---
# \<activityStateQueries>
<span data-ttu-id="ec6f7-101">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ec6f7-102">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ec6f7-103">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ec6f7-104">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="ec6f7-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ec6f7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="ec6f7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec6f7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec6f7-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec6f7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ec6f7-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec6f7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec6f7-109">Attributes</span></span>  
 <span data-ttu-id="ec6f7-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec6f7-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec6f7-111">Child Elements</span></span>  
  
|<span data-ttu-id="ec6f7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec6f7-112">Element</span></span>|<span data-ttu-id="ec6f7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec6f7-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="ec6f7-114">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ec6f7-115">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="ec6f7-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec6f7-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec6f7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ec6f7-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec6f7-117">Element</span></span>|<span data-ttu-id="ec6f7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec6f7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="ec6f7-119">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="ec6f7-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec6f7-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec6f7-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ec6f7-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ec6f7-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ec6f7-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="ec6f7-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
