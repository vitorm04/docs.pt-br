---
title: <behavior> do <serviceBehaviors> fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 14c528746963a3078e0ab377d095414d2fca0dbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189611"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="1cfe4-102">\<behavior> do \<serviceBehaviors> fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1cfe4-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>

<span data-ttu-id="1cfe4-103">O elemento **Behavior** contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="1cfe4-104">Cada comportamento é indexado por seu **nome**.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="1cfe4-105">Os serviços podem vincular a cada comportamento por meio desse nome usando o atributo **behaviorConfiguration** do [\<endpoint>](../wcf/endpoint-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="1cfe4-106">Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="1cfe4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cfe4-107">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String"
                                  hostLockRenewalPeriod="TimeSpan"
                                  instanceCompletionAction="DeleteNothing/DeleteAll"
                                  instanceEncodingAction="None/GZip"
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan"
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cfe4-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1cfe4-108">Attributes and Elements</span></span>  

 <span data-ttu-id="1cfe4-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cfe4-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1cfe4-110">Attributes</span></span>  
  
|<span data-ttu-id="1cfe4-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="1cfe4-111">Attribute</span></span>|<span data-ttu-id="1cfe4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cfe4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1cfe4-113">name</span><span class="sxs-lookup"><span data-stu-id="1cfe4-113">name</span></span>|<span data-ttu-id="1cfe4-114">Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-114">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="1cfe4-115">Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-115">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cfe4-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1cfe4-116">Child Elements</span></span>  
  
|<span data-ttu-id="1cfe4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="1cfe4-117">Element</span></span>|<span data-ttu-id="1cfe4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cfe4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="1cfe4-119">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-119">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="1cfe4-120">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-120">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="1cfe4-121">Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-121">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="1cfe4-122">Um comportamento de serviço que permite configurar o recurso <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, que dá suporte a informações de estado persistentes para instâncias de serviço de fluxo de trabalho em um banco de dados do SQL Server 2005 ou do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-122">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="1cfe4-123">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-123">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="1cfe4-124">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-124">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="1cfe4-125">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-125">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1cfe4-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1cfe4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1cfe4-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="1cfe4-127">Element</span></span>|<span data-ttu-id="1cfe4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cfe4-128">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="1cfe4-129">Uma coleção de elementos de comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="1cfe4-129">A collection of service behavior elements.</span></span>|
