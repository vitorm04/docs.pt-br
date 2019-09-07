---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: 48731e7ed8aaf7d8d543f3a303577480a29588ea
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398740"
---
# <a name="factorysettings"></a><span data-ttu-id="38f7a-101">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="38f7a-101">\<factorySettings></span></span>
<span data-ttu-id="38f7a-102">Especifica as configurações de cache da fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="38f7a-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="38f7a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38f7a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38f7a-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="38f7a-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="38f7a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="38f7a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="38f7a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="38f7a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="38f7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="38f7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="38f7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> sendMessageChannelCache**](sendmessagechannelcache.md)</span><span class="sxs-lookup"><span data-stu-id="38f7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)</span></span>\
<span data-ttu-id="38f7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> factorySettings**</span><span class="sxs-lookup"><span data-stu-id="38f7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<factorySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f7a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38f7a-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38f7a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38f7a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="38f7a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38f7a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38f7a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="38f7a-113">Attributes</span></span>  
  
|<span data-ttu-id="38f7a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="38f7a-114">Attribute</span></span>|<span data-ttu-id="38f7a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="38f7a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38f7a-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="38f7a-116">idleTimeout</span></span>|<span data-ttu-id="38f7a-117">Um valor de TimeSpan que especifica o intervalo máximo de tempo para o qual o objeto pode permanecer ocioso no cache antes de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="38f7a-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="38f7a-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="38f7a-118">leaseTimeout</span></span>|<span data-ttu-id="38f7a-119">Um valor TimeSpan que especifica o intervalo de tempo após o qual um objeto é removido do cache.</span><span class="sxs-lookup"><span data-stu-id="38f7a-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="38f7a-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="38f7a-120">maxItemsInCache</span></span>|<span data-ttu-id="38f7a-121">Um inteiro que especifica o número máximo de objetos que podem ser no cache.</span><span class="sxs-lookup"><span data-stu-id="38f7a-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38f7a-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38f7a-122">Child Elements</span></span>  
 <span data-ttu-id="38f7a-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="38f7a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38f7a-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38f7a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="38f7a-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="38f7a-125">Element</span></span>|<span data-ttu-id="38f7a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="38f7a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38f7a-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="38f7a-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="38f7a-128">Um comportamento de serviço que permite a personalização dos níveis de compartilhamento de cache, as configurações do cache de fábrica de canais e as configurações do cache de canal para fluxos de trabalho que enviam mensagens para pontos de extremidade de serviço usando atividades de envio de mensagens.</span><span class="sxs-lookup"><span data-stu-id="38f7a-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38f7a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="38f7a-129">Remarks</span></span>  
 <span data-ttu-id="38f7a-130">Esse comportamento de serviço destina-se a fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="38f7a-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="38f7a-131">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="38f7a-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="38f7a-132">Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagem é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache).</span><span class="sxs-lookup"><span data-stu-id="38f7a-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="38f7a-133">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="38f7a-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="38f7a-134">O cache é desabilitado por padrão para qualquer atividade de envio do fluxo de trabalho que tem pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="38f7a-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="38f7a-135">Para obter mais informações sobre como alterar os níveis de compartilhamento de cache padrão e as configurações de cache para a fábrica de canais e o cache de canal, consulte [alterando os níveis de compartilhamento de cache para atividades de envio](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="38f7a-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38f7a-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38f7a-136">Example</span></span>  
 <span data-ttu-id="38f7a-137">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38f7a-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="38f7a-138">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="38f7a-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="38f7a-139">O exemplo a seguir mostra o conteúdo de um arquivo de configuração que `MyChannelCacheBehavior` contém o comportamento do serviço com o cache de fábrica personalizado e as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="38f7a-139">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="38f7a-140">Esse comportamento de serviço é adicionado ao serviço por meio `behaviorConfiguration` do atributo.</span><span class="sxs-lookup"><span data-stu-id="38f7a-140">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38f7a-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38f7a-141">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="38f7a-142">Alterar o nível de compartilhamento de cache para atividades de envio</span><span class="sxs-lookup"><span data-stu-id="38f7a-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
