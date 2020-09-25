---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a50e9965a595fce64c383313091334e883dcfbfa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189481"
---
# \<cancelRequestedQuery>

<span data-ttu-id="707aa-101">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="707aa-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="707aa-102">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="707aa-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="707aa-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="707aa-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="707aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="707aa-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="707aa-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="707aa-105">Attributes and Elements</span></span>  

 <span data-ttu-id="707aa-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="707aa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="707aa-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="707aa-107">Attributes</span></span>  
  
|<span data-ttu-id="707aa-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="707aa-108">Attribute</span></span>|<span data-ttu-id="707aa-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="707aa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="707aa-110">activityName</span><span class="sxs-lookup"><span data-stu-id="707aa-110">activityName</span></span>|<span data-ttu-id="707aa-111">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="707aa-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="707aa-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="707aa-112">childActivityName</span></span>|<span data-ttu-id="707aa-113">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="707aa-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="707aa-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="707aa-114">Child Elements</span></span>  

 <span data-ttu-id="707aa-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="707aa-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="707aa-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="707aa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="707aa-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="707aa-117">Element</span></span>|<span data-ttu-id="707aa-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="707aa-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="707aa-119">Representa uma lista de elementos de configuração que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="707aa-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="707aa-120">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="707aa-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="707aa-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="707aa-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="707aa-122">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="707aa-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="707aa-123">Controlando perfis</span><span class="sxs-lookup"><span data-stu-id="707aa-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
