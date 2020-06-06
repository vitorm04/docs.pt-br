---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152301"
---
# \<cancelRequestedQueries>
<span data-ttu-id="c2058-101">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c2058-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c2058-102">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="c2058-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c2058-103">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c2058-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="c2058-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2058-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2058-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c2058-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c2058-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c2058-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2058-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c2058-107">Attributes</span></span>  
 <span data-ttu-id="c2058-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c2058-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2058-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c2058-109">Child Elements</span></span>  
  
|<span data-ttu-id="c2058-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2058-110">Element</span></span>|<span data-ttu-id="c2058-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2058-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="c2058-112">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="c2058-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2058-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c2058-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c2058-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2058-114">Element</span></span>|<span data-ttu-id="c2058-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2058-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="c2058-116">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="c2058-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2058-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2058-117">See also</span></span>

- [<span data-ttu-id="c2058-118">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c2058-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c2058-119">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="c2058-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
