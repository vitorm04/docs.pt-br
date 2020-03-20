---
title: <sistema.serviceModelo> do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151943"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="b1f4a-102">\<system.serviceModelo> de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b1f4a-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="b1f4a-103">Esta seção de configuração contém todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="b1f4a-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1f4a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1f4a-105">&nbsp;&nbsp;**\<Sistema.>de modelo de serviço**</span><span class="sxs-lookup"><span data-stu-id="b1f4a-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f4a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1f4a-106">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore
          connectionStringName="String"
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>
     <participants>
      <add name="String"
           profileName="String"  
           type="String" />
     </participants>
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1f4a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1f4a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b1f4a-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1f4a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1f4a-109">Attributes</span></span>  
 <span data-ttu-id="b1f4a-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b1f4a-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1f4a-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1f4a-111">Child Elements</span></span>  
  
|<span data-ttu-id="b1f4a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1f4a-112">Element</span></span>|<span data-ttu-id="b1f4a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1f4a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1f4a-114">\<comportamentos></span><span class="sxs-lookup"><span data-stu-id="b1f4a-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="b1f4a-115">Esta seção define a coleção **serviceBehaviors.**</span><span class="sxs-lookup"><span data-stu-id="b1f4a-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="b1f4a-116">Cada elemento na coleção define elementos de comportamento consumidos por serviços.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="b1f4a-117">Cada elemento de comportamento é identificado pelo seu atributo **de nome** único.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="b1f4a-118">\<rastreando></span><span class="sxs-lookup"><span data-stu-id="b1f4a-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="b1f4a-119">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="b1f4a-120">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte [Rastreamento e rastreamento de fluxo de trabalho e](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b1f4a-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1f4a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1f4a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b1f4a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1f4a-122">Element</span></span>|<span data-ttu-id="b1f4a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1f4a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1f4a-124">\<>de configuração</span><span class="sxs-lookup"><span data-stu-id="b1f4a-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="b1f4a-125">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
