---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: cb1f96cb6ba2643e28552c354bdd5caf4d43285c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189637"
---
# \<arguments>

<span data-ttu-id="27281-101">Representa uma coleção de argumentos associados a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="27281-101">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="27281-102">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="27281-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="27281-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27281-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27281-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27281-104">Attributes and Elements</span></span>  

 <span data-ttu-id="27281-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="27281-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27281-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="27281-106">Attributes</span></span>  

 <span data-ttu-id="27281-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="27281-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27281-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27281-108">Child Elements</span></span>  
  
|<span data-ttu-id="27281-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="27281-109">Element</span></span>|<span data-ttu-id="27281-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="27281-110">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="27281-111">Um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="27281-111">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27281-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="27281-112">Parent Elements</span></span>  
  
|<span data-ttu-id="27281-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="27281-113">Element</span></span>|<span data-ttu-id="27281-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="27281-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="27281-115">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="27281-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="27281-116">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="27281-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27281-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="27281-117">Remarks</span></span>  

 <span data-ttu-id="27281-118">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="27281-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="27281-119">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="27281-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="27281-120">Você pode usar os [\<arguments>](arguments.md) [\<states>](states.md) elementos e [\<states>](states.md) para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="27281-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="27281-121">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="27281-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="27281-122">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="27281-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27281-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="27281-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="27281-124">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="27281-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="27281-125">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="27281-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
