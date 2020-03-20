---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152301"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="6fb03-101">\<cancelarConsultas solicitadas></span><span class="sxs-lookup"><span data-stu-id="6fb03-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="6fb03-102">Representa uma coleção de consultas que são usados para controlar solicitações cancelar uma atividade filho pela atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6fb03-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6fb03-103">A consulta é necessária para um participante de rastreamento inscrever-se para Cancelar solicitação objetos de registro.</span><span class="sxs-lookup"><span data-stu-id="6fb03-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="6fb03-104">Para obter mais informações sobre o rastreamento de consultas de perfil, consulte [Perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6fb03-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6fb03-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6fb03-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6fb03-106">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6fb03-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="6fb03-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="6fb03-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="6fb03-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de rastreamentoPerfil**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="6fb03-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="6fb03-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de fluxo de trabalho**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6fb03-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="6fb03-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelarConsultas solicitadas>**</span><span class="sxs-lookup"><span data-stu-id="6fb03-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb03-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fb03-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fb03-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6fb03-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6fb03-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6fb03-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fb03-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6fb03-114">Attributes</span></span>  
 <span data-ttu-id="6fb03-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6fb03-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6fb03-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6fb03-116">Child Elements</span></span>  
  
|<span data-ttu-id="6fb03-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fb03-117">Element</span></span>|<span data-ttu-id="6fb03-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fb03-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fb03-119">\<cancelar>de Quequery Solicitado</span><span class="sxs-lookup"><span data-stu-id="6fb03-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="6fb03-120">Uma consulta que é usada para controlar solicitações cancelar uma atividade filho pela atividade pai</span><span class="sxs-lookup"><span data-stu-id="6fb03-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fb03-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6fb03-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6fb03-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fb03-122">Element</span></span>|<span data-ttu-id="6fb03-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fb03-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fb03-124">\<>de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6fb03-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="6fb03-125">Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="6fb03-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fb03-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="6fb03-126">See also</span></span>

- [<span data-ttu-id="6fb03-127">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6fb03-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6fb03-128">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="6fb03-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
