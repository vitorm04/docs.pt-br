---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397589"
---
# \<variables>
<span data-ttu-id="24090-101">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="24090-101">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="24090-102">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="24090-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**  
  
## <a name="syntax"></a><span data-ttu-id="24090-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24090-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24090-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="24090-104">Attributes and Elements</span></span>  
 <span data-ttu-id="24090-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="24090-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24090-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="24090-106">Attributes</span></span>  
 <span data-ttu-id="24090-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="24090-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24090-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="24090-108">Child Elements</span></span>  
  
|<span data-ttu-id="24090-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="24090-109">Element</span></span>|<span data-ttu-id="24090-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="24090-110">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="24090-111">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="24090-111">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24090-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="24090-112">Parent Elements</span></span>  
  
|<span data-ttu-id="24090-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="24090-113">Element</span></span>|<span data-ttu-id="24090-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="24090-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="24090-115">Representa um elemento de configuração que é usado para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="24090-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="24090-116">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="24090-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24090-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="24090-117">Remarks</span></span>  
 <span data-ttu-id="24090-118">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="24090-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="24090-119">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="24090-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="24090-120">Você pode usar os [\<arguments>](arguments.md) [\<states>](states.md) elementos e [\<states>](states.md) para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="24090-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="24090-121">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="24090-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="24090-122">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="24090-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24090-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="24090-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="24090-124">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="24090-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="24090-125">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="24090-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
