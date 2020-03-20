---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151995"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="b7fb3-101">\<enviar> MessageChannelCache</span><span class="sxs-lookup"><span data-stu-id="b7fb3-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="b7fb3-102">Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="b7fb3-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7fb3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7fb3-104">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b7fb3-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b7fb3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamentos>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b7fb3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b7fb3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçocomportamentos>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b7fb3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b7fb3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamento>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b7fb3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b7fb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enviarMessageChannelCache>**</span><span class="sxs-lookup"><span data-stu-id="b7fb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fb3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7fb3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7fb3-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7fb3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7fb3-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7fb3-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7fb3-112">Attributes</span></span>  
  
|<span data-ttu-id="b7fb3-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7fb3-113">Attribute</span></span>|<span data-ttu-id="b7fb3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7fb3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7fb3-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="b7fb3-115">allowUnsafeCaching</span></span>|<span data-ttu-id="b7fb3-116">Um valor booliano que indica se deve ativar o cache.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="b7fb3-117">Se o serviço de fluxo de trabalho tiver ligações personalizadas ou comportamentos personalizados, o cache pode ser insegura e, portanto, está desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="b7fb3-118">No entanto, se você quiser transformar o cache no definir esta propriedade para **verdade**.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7fb3-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7fb3-119">Child Elements</span></span>  
  
|<span data-ttu-id="b7fb3-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7fb3-120">Element</span></span>|<span data-ttu-id="b7fb3-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7fb3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7fb3-122">\<>de configurações de canal</span><span class="sxs-lookup"><span data-stu-id="b7fb3-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="b7fb3-123">Especifica as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="b7fb3-124">\<fábricaConfigurações></span><span class="sxs-lookup"><span data-stu-id="b7fb3-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="b7fb3-125">Especifica as configurações de cache da fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7fb3-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7fb3-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b7fb3-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7fb3-127">Element</span></span>|<span data-ttu-id="b7fb3-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7fb3-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7fb3-129">\<> de \<comportamento de>de serviços</span><span class="sxs-lookup"><span data-stu-id="b7fb3-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b7fb3-130">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7fb3-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7fb3-131">Remarks</span></span>  
 <span data-ttu-id="b7fb3-132">Esse comportamento de serviço destina-se a fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="b7fb3-133">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="b7fb3-134">Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagem é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache).</span><span class="sxs-lookup"><span data-stu-id="b7fb3-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="b7fb3-135">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="b7fb3-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="b7fb3-136">O cache é desabilitado por padrão para qualquer atividade de envio do fluxo de trabalho que tem pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="b7fb3-137">Para obter mais informações sobre como alterar os níveis de compartilhamento de cache padrão e as configurações de cache para a fábrica de canais e o cache do canal, consulte [Alterando os níveis de compartilhamento de cache para atividades de envio](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="b7fb3-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7fb3-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7fb3-138">Example</span></span>  
 <span data-ttu-id="b7fb3-139">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="b7fb3-140">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="b7fb3-141">O exemplo a seguir mostra o conteúdo `MyChannelCacheBehavior` de um arquivo de configuração que contém o comportamento do serviço com as configurações personalizadas de cache de fábrica e cache de canal.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="b7fb3-142">Esse comportamento de serviço é `behaviorConfiguration` adicionado ao serviço através do atributo.</span><span class="sxs-lookup"><span data-stu-id="b7fb3-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7fb3-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7fb3-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="b7fb3-144">Alterar o nível de compartilhamento de cache para atividades de envio</span><span class="sxs-lookup"><span data-stu-id="b7fb3-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
