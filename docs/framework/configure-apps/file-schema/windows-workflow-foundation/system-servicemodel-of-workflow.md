---
title: < o > System. serviceModel do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 757a7a132a6e765e257097d251a110297c6a40bf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398607"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="c1116-102">\<> de sistema. serviceModel do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c1116-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="c1116-103">Esta seção de configuração contém todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c1116-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="c1116-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1116-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1116-105">&nbsp;&nbsp; **\<sistema. > ServiceModel**</span><span class="sxs-lookup"><span data-stu-id="c1116-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1116-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1116-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1116-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1116-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c1116-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1116-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1116-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1116-109">Attributes</span></span>  
 <span data-ttu-id="c1116-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c1116-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1116-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1116-111">Child Elements</span></span>  
  
|<span data-ttu-id="c1116-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1116-112">Element</span></span>|<span data-ttu-id="c1116-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1116-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1116-114">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="c1116-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="c1116-115">Esta seção define a coleção de **Percomportamentos** .</span><span class="sxs-lookup"><span data-stu-id="c1116-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="c1116-116">Cada elemento na coleção define elementos de comportamento consumidos por serviços.</span><span class="sxs-lookup"><span data-stu-id="c1116-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="c1116-117">Cada elemento de comportamento é identificado por seu atributo de **nome** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="c1116-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="c1116-118">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c1116-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="c1116-119">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c1116-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="c1116-120">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte rastreamento [e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="c1116-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1116-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1116-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c1116-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1116-122">Element</span></span>|<span data-ttu-id="c1116-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1116-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1116-124">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c1116-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="c1116-125">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="c1116-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
