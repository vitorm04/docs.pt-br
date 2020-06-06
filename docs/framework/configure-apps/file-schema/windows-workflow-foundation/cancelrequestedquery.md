---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152281"
---
# \<cancelRequestedQuery>
<span data-ttu-id="d8d92-101">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="d8d92-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d8d92-102">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="d8d92-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="d8d92-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d8d92-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="d8d92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8d92-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8d92-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d8d92-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d8d92-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d8d92-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8d92-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8d92-107">Attributes</span></span>  
  
|<span data-ttu-id="d8d92-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d8d92-108">Attribute</span></span>|<span data-ttu-id="d8d92-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8d92-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8d92-110">activityName</span><span class="sxs-lookup"><span data-stu-id="d8d92-110">activityName</span></span>|<span data-ttu-id="d8d92-111">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="d8d92-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="d8d92-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="d8d92-112">childActivityName</span></span>|<span data-ttu-id="d8d92-113">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="d8d92-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8d92-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8d92-114">Child Elements</span></span>  
 <span data-ttu-id="d8d92-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d8d92-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8d92-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d8d92-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d8d92-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8d92-117">Element</span></span>|<span data-ttu-id="d8d92-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8d92-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="d8d92-119">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="d8d92-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d8d92-120">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="d8d92-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8d92-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="d8d92-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d8d92-122">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d8d92-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d8d92-123">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d8d92-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
