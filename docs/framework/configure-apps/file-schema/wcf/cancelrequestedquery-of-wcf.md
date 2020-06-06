---
title: <cancelRequestedQuery>do WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850056"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="9fdec-102">\<cancelRequestedQuery>do WCF</span><span class="sxs-lookup"><span data-stu-id="9fdec-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="9fdec-103">Representa uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="9fdec-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9fdec-104">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="9fdec-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="9fdec-105">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9fdec-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="9fdec-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fdec-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fdec-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9fdec-107">Attributes and elements</span></span>

<span data-ttu-id="9fdec-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9fdec-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fdec-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9fdec-109">Attributes</span></span>  
  
|<span data-ttu-id="9fdec-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="9fdec-110">Attribute</span></span>|<span data-ttu-id="9fdec-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fdec-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="9fdec-112">Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="9fdec-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="9fdec-113">Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="9fdec-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fdec-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9fdec-114">Child elements</span></span>

<span data-ttu-id="9fdec-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9fdec-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="9fdec-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9fdec-116">Parent elements</span></span>
  
|<span data-ttu-id="9fdec-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="9fdec-117">Element</span></span>|<span data-ttu-id="9fdec-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fdec-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="9fdec-119">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="9fdec-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fdec-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="9fdec-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9fdec-121">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9fdec-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9fdec-122">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="9fdec-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
