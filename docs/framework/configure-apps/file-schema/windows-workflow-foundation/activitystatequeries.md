---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 4663ccedcafb6b151de75568afd3743c83c75224
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189819"
---
# \<activityStateQueries>

<span data-ttu-id="0ed75-101">Representa uma coleção de consultas que são usados para controlar as alterações do ciclo de vida das atividades que compõem uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0ed75-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="0ed75-102">Por exemplo, talvez você queira manter o controle sempre que a atividade "enviar email" for concluída em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0ed75-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="0ed75-103">Essa consulta é necessária para um participante de rastreamento para se inscrever em objetos de registro de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="0ed75-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="0ed75-104">Os estados disponíveis para assinar são especificados em ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="0ed75-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="0ed75-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0ed75-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="0ed75-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ed75-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ed75-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ed75-107">Attributes and Elements</span></span>  

 <span data-ttu-id="0ed75-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0ed75-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ed75-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ed75-109">Attributes</span></span>  

 <span data-ttu-id="0ed75-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0ed75-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ed75-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0ed75-111">Child Elements</span></span>  
  
|<span data-ttu-id="0ed75-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ed75-112">Element</span></span>|<span data-ttu-id="0ed75-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ed75-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="0ed75-114">Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0ed75-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0ed75-115">Esse evento ocorre toda vez que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="0ed75-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ed75-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0ed75-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0ed75-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ed75-117">Element</span></span>|<span data-ttu-id="0ed75-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ed75-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="0ed75-119">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="0ed75-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ed75-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="0ed75-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0ed75-121">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0ed75-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0ed75-122">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="0ed75-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
