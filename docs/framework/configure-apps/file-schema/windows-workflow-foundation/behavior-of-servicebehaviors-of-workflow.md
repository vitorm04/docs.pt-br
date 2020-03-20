---
title: <behavior>de <serviceBehaviors> fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152314"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="b5d92-102">\<comportamento> \<de serviçosComportamentos> do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b5d92-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="b5d92-103">O elemento **comportamento** contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="b5d92-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="b5d92-104">Cada comportamento é indexado pelo seu **nome.**</span><span class="sxs-lookup"><span data-stu-id="b5d92-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="b5d92-105">Os serviços podem vincular-se a cada comportamento [ \<](../wcf/endpoint-element.md) através deste nome usando o atributo **comportamentoConfiguração** do ponto final>elemento.</span><span class="sxs-lookup"><span data-stu-id="b5d92-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="b5d92-106">Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="b5d92-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="b5d92-107">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b5d92-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b5d92-108">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b5d92-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b5d92-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamentos>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b5d92-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b5d92-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçocomportamentos>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b5d92-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b5d92-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportamento>**</span><span class="sxs-lookup"><span data-stu-id="b5d92-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5d92-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5d92-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5d92-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b5d92-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b5d92-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b5d92-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5d92-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5d92-115">Attributes</span></span>  
  
|<span data-ttu-id="b5d92-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b5d92-116">Attribute</span></span>|<span data-ttu-id="b5d92-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5d92-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5d92-118">name</span><span class="sxs-lookup"><span data-stu-id="b5d92-118">name</span></span>|<span data-ttu-id="b5d92-119">Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento.</span><span class="sxs-lookup"><span data-stu-id="b5d92-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="b5d92-120">Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.</span><span class="sxs-lookup"><span data-stu-id="b5d92-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5d92-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b5d92-121">Child Elements</span></span>  
  
|<span data-ttu-id="b5d92-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5d92-122">Element</span></span>|<span data-ttu-id="b5d92-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5d92-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5d92-124">\<bufferReceba></span><span class="sxs-lookup"><span data-stu-id="b5d92-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="b5d92-125">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="b5d92-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="b5d92-126">\<roteamento></span><span class="sxs-lookup"><span data-stu-id="b5d92-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="b5d92-127">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b5d92-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="b5d92-128">\<enviarMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="b5d92-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="b5d92-129">Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="b5d92-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="b5d92-130">\<sqlWorkflow></span><span class="sxs-lookup"><span data-stu-id="b5d92-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="b5d92-131">Um comportamento de serviço que permite configurar o recurso <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, que dá suporte a informações de estado persistentes para instâncias de serviço de fluxo de trabalho em um banco de dados do SQL Server 2005 ou do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b5d92-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="b5d92-132">\<fluxo de trabalho>de risada</span><span class="sxs-lookup"><span data-stu-id="b5d92-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="b5d92-133">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="b5d92-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="b5d92-134">\<trabalhogerenciamento de trabalho></span><span class="sxs-lookup"><span data-stu-id="b5d92-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="b5d92-135">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="b5d92-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="b5d92-136">\<fluxo de trabalhoUnhandledException></span><span class="sxs-lookup"><span data-stu-id="b5d92-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="b5d92-137">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b5d92-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5d92-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b5d92-138">Parent Elements</span></span>  
  
|<span data-ttu-id="b5d92-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5d92-139">Element</span></span>|<span data-ttu-id="b5d92-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5d92-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5d92-141">\<serviçocomportamentos></span><span class="sxs-lookup"><span data-stu-id="b5d92-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="b5d92-142">Uma coleção de elementos de comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="b5d92-142">A collection of service behavior elements.</span></span>|
