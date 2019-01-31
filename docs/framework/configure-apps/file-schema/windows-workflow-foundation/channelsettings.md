---
title: <channelSettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
ms.openlocfilehash: 38b2ddc0134ea8c0e0f75db093b440788c5409aa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272832"
---
# <a name="channelsettings"></a><span data-ttu-id="6e13c-101">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="6e13c-101">\<channelSettings></span></span>
<span data-ttu-id="6e13c-102">Especifica as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="6e13c-102">Specifies the settings of the channel cache.</span></span>  
  
<span data-ttu-id="6e13c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6e13c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6e13c-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="6e13c-104">\<behaviors></span></span>  
<span data-ttu-id="6e13c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6e13c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="6e13c-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6e13c-106">\<behavior></span></span>  
<span data-ttu-id="6e13c-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="6e13c-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="6e13c-108">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="6e13c-108">\<channelSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e13c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e13c-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e13c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e13c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e13c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6e13c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e13c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e13c-112">Attributes</span></span>  
  
|<span data-ttu-id="6e13c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6e13c-113">Attribute</span></span>|<span data-ttu-id="6e13c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e13c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e13c-115">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="6e13c-115">idleTimeout</span></span>|<span data-ttu-id="6e13c-116">Um valor de TimeSpan que especifica o intervalo máximo de tempo para o qual o objeto pode permanecer ocioso no cache antes de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="6e13c-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="6e13c-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="6e13c-117">leaseTimeout</span></span>|<span data-ttu-id="6e13c-118">Um valor de TimeSpan que especifica o intervalo de tempo após o qual um objeto é removido do cache.</span><span class="sxs-lookup"><span data-stu-id="6e13c-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="6e13c-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="6e13c-119">maxItemsInCache</span></span>|<span data-ttu-id="6e13c-120">Um inteiro que especifica o número máximo de objetos que podem ser no cache.</span><span class="sxs-lookup"><span data-stu-id="6e13c-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e13c-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e13c-121">Child Elements</span></span>  
 <span data-ttu-id="6e13c-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6e13c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e13c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e13c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e13c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e13c-124">Element</span></span>|<span data-ttu-id="6e13c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e13c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e13c-126">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="6e13c-126">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="6e13c-127">Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="6e13c-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e13c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e13c-128">Remarks</span></span>  
 <span data-ttu-id="6e13c-129">Esse comportamento de serviço destina-se a fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="6e13c-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="6e13c-130">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6e13c-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="6e13c-131">Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagem é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache).</span><span class="sxs-lookup"><span data-stu-id="6e13c-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="6e13c-132">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="6e13c-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="6e13c-133">O cache é desabilitado por padrão para qualquer atividade de envio do fluxo de trabalho que tem pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="6e13c-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="6e13c-134">Para obter mais informações sobre como alterar o cache padrão do compartilhamento níveis e configurações de cache para a fábrica de canais e cache de canal, consulte [alterando os níveis de compartilhamento de Cache para enviar atividades](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="6e13c-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e13c-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e13c-135">Example</span></span>  
 <span data-ttu-id="6e13c-136">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6e13c-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="6e13c-137">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="6e13c-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="6e13c-138">O exemplo a seguir mostra o conteúdo de um arquivo de configuração que contém o **MyChannelCacheBehavior** comportamento de serviço com as configurações de cache de canal e do cache de fábrica personalizada.</span><span class="sxs-lookup"><span data-stu-id="6e13c-138">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="6e13c-139">Esse comportamento de serviço é adicionado ao serviço por meio de **behaviorConfiguarion** atributo.</span><span class="sxs-lookup"><span data-stu-id="6e13c-139">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e13c-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e13c-140">See also</span></span>
- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="6e13c-141">Alterar o nível de compartilhamento de cache para atividades de envio</span><span class="sxs-lookup"><span data-stu-id="6e13c-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
