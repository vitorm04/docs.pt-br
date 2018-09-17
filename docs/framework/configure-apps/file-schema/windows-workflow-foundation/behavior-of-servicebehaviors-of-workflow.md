---
title: '&lt;comportamento&gt; dos &lt;serviceBehaviors&gt; de fluxo de trabalho'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 9b16aad6138d79d3dbff4994250f05d617d54140
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749823"
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="985b5-102">&lt;comportamento&gt; dos &lt;serviceBehaviors&gt; de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="985b5-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="985b5-103">O **comportamento** elemento contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="985b5-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="985b5-104">Cada comportamento é indexado por seus **nome**.</span><span class="sxs-lookup"><span data-stu-id="985b5-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="985b5-105">Serviços podem vincular a cada comportamento por esse nome usando o **behaviorConfiguration** atributo da [ \<ponto de extremidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="985b5-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="985b5-106">Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="985b5-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="985b5-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="985b5-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="985b5-108">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="985b5-108">\<behaviors></span></span>  
<span data-ttu-id="985b5-109">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="985b5-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="985b5-110">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="985b5-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985b5-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="985b5-111">Syntax</span></span>  
  
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
                                  honstLockRenewalPeriod="TimeSpan" 
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="985b5-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="985b5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="985b5-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="985b5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="985b5-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="985b5-114">Attributes</span></span>  
  
|<span data-ttu-id="985b5-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="985b5-115">Attribute</span></span>|<span data-ttu-id="985b5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="985b5-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="985b5-117">name</span><span class="sxs-lookup"><span data-stu-id="985b5-117">name</span></span>|<span data-ttu-id="985b5-118">Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento.</span><span class="sxs-lookup"><span data-stu-id="985b5-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="985b5-119">Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.</span><span class="sxs-lookup"><span data-stu-id="985b5-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="985b5-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="985b5-120">Child Elements</span></span>  
  
|<span data-ttu-id="985b5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="985b5-121">Element</span></span>|<span data-ttu-id="985b5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="985b5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="985b5-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="985b5-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="985b5-124">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="985b5-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="985b5-125">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="985b5-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="985b5-126">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="985b5-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="985b5-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="985b5-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="985b5-128">Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="985b5-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="985b5-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="985b5-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="985b5-130">Um comportamento de serviço que permite configurar o recurso <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, que dá suporte a informações de estado persistentes para instâncias de serviço de fluxo de trabalho em um banco de dados do SQL Server 2005 ou do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="985b5-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="985b5-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="985b5-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="985b5-132">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="985b5-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="985b5-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="985b5-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="985b5-134">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="985b5-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="985b5-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="985b5-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="985b5-136">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="985b5-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="985b5-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="985b5-137">Parent Elements</span></span>  
  
|<span data-ttu-id="985b5-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="985b5-138">Element</span></span>|<span data-ttu-id="985b5-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="985b5-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="985b5-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="985b5-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="985b5-141">Uma coleção de elementos de comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="985b5-141">A collection of service behavior elements.</span></span>|
