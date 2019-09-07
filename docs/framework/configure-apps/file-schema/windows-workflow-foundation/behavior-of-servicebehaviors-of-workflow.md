---
title: <behavior>do <serviceBehaviors> fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398887"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="f2d1f-102">\<comportamento > de \<percomportamentos > do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f2d1f-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="f2d1f-103">O elemento **Behavior** contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="f2d1f-104">Cada comportamento é indexado por seu **nome**.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="f2d1f-105">Os serviços podem vincular a cada comportamento por meio desse nome usando o atributo **behaviorConfiguration** do [ \<elemento Endpoint >](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f2d1f-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="f2d1f-106">Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="f2d1f-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2d1f-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2d1f-108">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f2d1f-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f2d1f-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f2d1f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f2d1f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f2d1f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f2d1f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de comportamento**</span><span class="sxs-lookup"><span data-stu-id="f2d1f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d1f-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2d1f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2d1f-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f2d1f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f2d1f-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2d1f-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="f2d1f-115">Attributes</span></span>  
  
|<span data-ttu-id="f2d1f-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2d1f-116">Attribute</span></span>|<span data-ttu-id="f2d1f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2d1f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2d1f-118">name</span><span class="sxs-lookup"><span data-stu-id="f2d1f-118">name</span></span>|<span data-ttu-id="f2d1f-119">Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="f2d1f-120">Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2d1f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f2d1f-121">Child Elements</span></span>  
  
|<span data-ttu-id="f2d1f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f2d1f-122">Element</span></span>|<span data-ttu-id="f2d1f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2d1f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2d1f-124">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="f2d1f-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="f2d1f-125">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="f2d1f-126">\<routing></span><span class="sxs-lookup"><span data-stu-id="f2d1f-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="f2d1f-127">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="f2d1f-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="f2d1f-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="f2d1f-129">Um comportamento de serviço que permite a personalização dos níveis de compartilhamento de cache, as configurações do cache de fábrica de canais e as configurações do cache de canal para fluxos de trabalho que enviam mensagens para pontos de extremidade de serviço usando atividades de envio de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="f2d1f-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="f2d1f-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="f2d1f-131">Um comportamento de serviço que permite configurar o recurso <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, que dá suporte a informações de estado persistentes para instâncias de serviço de fluxo de trabalho em um banco de dados do SQL Server 2005 ou do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="f2d1f-132">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="f2d1f-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="f2d1f-133">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="f2d1f-134">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="f2d1f-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="f2d1f-135">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="f2d1f-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="f2d1f-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="f2d1f-137">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2d1f-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f2d1f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="f2d1f-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="f2d1f-139">Element</span></span>|<span data-ttu-id="f2d1f-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2d1f-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2d1f-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f2d1f-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="f2d1f-142">Uma coleção de elementos de comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="f2d1f-142">A collection of service behavior elements.</span></span>|
