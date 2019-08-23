---
title: < o > System. serviceModel do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: faa8154c4d7ac5c6aa2f9f1707cf8f0d39eefad5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947362"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="0274e-102">\<> de sistema. serviceModel do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0274e-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="0274e-103">Esta seção de configuração contém todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0274e-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0274e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0274e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0274e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0274e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0274e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0274e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0274e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0274e-107">Attributes</span></span>  
 <span data-ttu-id="0274e-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0274e-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0274e-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0274e-109">Child Elements</span></span>  
  
|<span data-ttu-id="0274e-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="0274e-110">Element</span></span>|<span data-ttu-id="0274e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0274e-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0274e-112">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="0274e-112">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="0274e-113">Esta seção define a coleção de percomportamentos.</span><span class="sxs-lookup"><span data-stu-id="0274e-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="0274e-114">Cada elemento na coleção define elementos de comportamento consumidos por serviços.</span><span class="sxs-lookup"><span data-stu-id="0274e-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="0274e-115">Cada elemento de comportamento é identificado por seu atributo de **nome** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="0274e-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="0274e-116">\<tracking></span><span class="sxs-lookup"><span data-stu-id="0274e-116">\<tracking></span></span>](tracking.md)|<span data-ttu-id="0274e-117">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0274e-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="0274e-118">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte rastreamento [e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="0274e-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0274e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0274e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0274e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="0274e-120">Element</span></span>|<span data-ttu-id="0274e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0274e-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0274e-122">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0274e-122">\<configuration></span></span>|<span data-ttu-id="0274e-123">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="0274e-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
