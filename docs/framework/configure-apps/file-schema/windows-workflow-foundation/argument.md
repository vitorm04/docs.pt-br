---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: ed08f5533cd6b3839775d061452cb17110cc627e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398900"
---
# \<argument>
<span data-ttu-id="13583-101">Um elemento de configuração que representa um argumento associado a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="13583-101">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="13583-102">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="13583-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="13583-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13583-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13583-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13583-104">Attributes and Elements</span></span>  
 <span data-ttu-id="13583-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13583-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13583-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="13583-106">Attributes</span></span>  
  
|<span data-ttu-id="13583-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="13583-107">Attribute</span></span>|<span data-ttu-id="13583-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="13583-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13583-109">name</span><span class="sxs-lookup"><span data-stu-id="13583-109">name</span></span>|<span data-ttu-id="13583-110">Uma cadeia de caracteres que especifica o nome do argumento.</span><span class="sxs-lookup"><span data-stu-id="13583-110">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13583-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13583-111">Child Elements</span></span>  
 <span data-ttu-id="13583-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="13583-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13583-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13583-113">Parent Elements</span></span>  
  
|<span data-ttu-id="13583-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="13583-114">Element</span></span>|<span data-ttu-id="13583-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="13583-115">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="13583-116">Uma coleção de argumentos associados a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="13583-116">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13583-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="13583-117">Remarks</span></span>  
 <span data-ttu-id="13583-118">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="13583-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="13583-119">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="13583-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="13583-120">Você pode usar os [\<arguments>](arguments.md) [\<states>](states.md) elementos e [\<states>](states.md) para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="13583-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="13583-121">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="13583-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="13583-122">Variáveis e argumentos podem ser extraídos apenas com um ActivityStateRecord e, portanto, são assinados em um perfil de controle usando [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="13583-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13583-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="13583-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="13583-124">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="13583-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="13583-125">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="13583-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
