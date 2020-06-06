---
title: <workflowInstanceQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854735"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="a7ba3-102">\<workflowInstanceQuery>do WCF</span><span class="sxs-lookup"><span data-stu-id="a7ba3-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="a7ba3-103">Representa uma consulta que controla as alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="a7ba3-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="a7ba3-104">Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a7ba3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a7ba3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7ba3-105">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7ba3-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a7ba3-106">Attributes and elements</span></span>  

<span data-ttu-id="a7ba3-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a7ba3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7ba3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7ba3-108">Attributes</span></span>  

<span data-ttu-id="a7ba3-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a7ba3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7ba3-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a7ba3-110">Child elements</span></span>  
  
|<span data-ttu-id="a7ba3-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7ba3-111">Element</span></span>|<span data-ttu-id="a7ba3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7ba3-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="a7ba3-113">Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.</span><span class="sxs-lookup"><span data-stu-id="a7ba3-113">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7ba3-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a7ba3-114">Parent elements</span></span>  
  
|<span data-ttu-id="a7ba3-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7ba3-115">Element</span></span>|<span data-ttu-id="a7ba3-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7ba3-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="a7ba3-117">Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="a7ba3-117">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7ba3-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7ba3-118">Remarks</span></span>  

<span data-ttu-id="a7ba3-119"><xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:</span><span class="sxs-lookup"><span data-stu-id="a7ba3-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="a7ba3-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7ba3-120">Example</span></span>  

<span data-ttu-id="a7ba3-121">A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.</span><span class="sxs-lookup"><span data-stu-id="a7ba3-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="a7ba3-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7ba3-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a7ba3-123">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a7ba3-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a7ba3-124">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="a7ba3-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
