---
title: <states> de <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: e56df08813c091a9c9390db6fc19a7c39f2e8592
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169694"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="9897d-102">\<states> de \<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="9897d-102">\<states> of \<activityStateQuery></span></span>

<span data-ttu-id="9897d-103">Uma coleção de elementos de configuração que contêm os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="9897d-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="9897d-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9897d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="9897d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9897d-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9897d-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9897d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9897d-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9897d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9897d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9897d-108">Attributes</span></span>  

 <span data-ttu-id="9897d-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9897d-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9897d-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9897d-110">Child Elements</span></span>  
  
|<span data-ttu-id="9897d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="9897d-111">Element</span></span>|<span data-ttu-id="9897d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9897d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](state-of-states.md)|<span data-ttu-id="9897d-113">Um elemento de configuração que contém os estados da atividade inscrito para que um registro de rastreamento deve ser emitido.</span><span class="sxs-lookup"><span data-stu-id="9897d-113">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9897d-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9897d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9897d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9897d-115">Element</span></span>|<span data-ttu-id="9897d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="9897d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="9897d-117">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="9897d-117">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9897d-118">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="9897d-118">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9897d-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="9897d-119">Remarks</span></span>  

 <span data-ttu-id="9897d-120">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9897d-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9897d-121">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="9897d-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9897d-122">Você pode usar os [\<arguments>](arguments.md) [\<states>](states.md) elementos e [\<states>](states.md) para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9897d-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="9897d-123">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="9897d-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9897d-124">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="9897d-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9897d-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="9897d-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9897d-126">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9897d-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9897d-127">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="9897d-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
