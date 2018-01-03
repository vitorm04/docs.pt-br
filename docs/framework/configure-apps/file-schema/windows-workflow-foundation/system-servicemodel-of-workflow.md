---
title: '&lt;System. ServiceModel&gt; de fluxo de trabalho'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54f8ae10491ebeed683a2ec289e60b9a90afd43b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemservicemodelgt-of-workflow"></a><span data-ttu-id="d6e4d-102">&lt;System. ServiceModel&gt; de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d6e4d-102">&lt;system.serviceModel&gt; of workflow</span></span>
<span data-ttu-id="d6e4d-103">Esta seção de configuração contém todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e4d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6e4d-104">Syntax</span></span>  
  
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
          honstLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionaction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6e4d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6e4d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d6e4d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6e4d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6e4d-107">Attributes</span></span>  
 <span data-ttu-id="d6e4d-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d6e4d-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6e4d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6e4d-109">Child Elements</span></span>  
  
|<span data-ttu-id="d6e4d-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6e4d-110">Element</span></span>|<span data-ttu-id="d6e4d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6e4d-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6e4d-112">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d6e4d-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="d6e4d-113">Esta seção define o **serviceBehaviors** coleção.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="d6e4d-114">Cada elemento na coleção define elementos de comportamento consumidos por serviços.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="d6e4d-115">Cada elemento de comportamento é identificado por seu exclusivo **nome** atributo.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="d6e4d-116">\<controle ></span><span class="sxs-lookup"><span data-stu-id="d6e4d-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="d6e4d-117">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="d6e4d-118">Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configurar rastreamento para um fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d6e4d-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6e4d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6e4d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d6e4d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6e4d-120">Element</span></span>|<span data-ttu-id="d6e4d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6e4d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6e4d-122">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d6e4d-122">\<configuration></span></span>|<span data-ttu-id="d6e4d-123">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
