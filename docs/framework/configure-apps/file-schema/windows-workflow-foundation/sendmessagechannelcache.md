---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: ac38a43b39496bdeee59a591f7b8f5bc4dd30de0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398691"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="8a91f-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="8a91f-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="8a91f-102">Um comportamento de serviço que permite a personalização dos níveis de compartilhamento de cache, as configurações do cache de fábrica de canais e as configurações do cache de canal para fluxos de trabalho que enviam mensagens para pontos de extremidade de serviço usando atividades de envio de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8a91f-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="8a91f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8a91f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8a91f-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8a91f-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="8a91f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8a91f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="8a91f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8a91f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="8a91f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8a91f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="8a91f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> sendMessageChannelCache**</span><span class="sxs-lookup"><span data-stu-id="8a91f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a91f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a91f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a91f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8a91f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8a91f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8a91f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a91f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8a91f-112">Attributes</span></span>  
  
|<span data-ttu-id="8a91f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8a91f-113">Attribute</span></span>|<span data-ttu-id="8a91f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a91f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a91f-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="8a91f-115">allowUnsafeCaching</span></span>|<span data-ttu-id="8a91f-116">Um valor booliano que indica se deve ativar o cache.</span><span class="sxs-lookup"><span data-stu-id="8a91f-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="8a91f-117">Se o serviço de fluxo de trabalho tiver ligações personalizadas ou comportamentos personalizados, o cache pode ser insegura e, portanto, está desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="8a91f-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="8a91f-118">No entanto, se você quiser ativar o armazenamento em cache, defina essa propriedade como **true**.</span><span class="sxs-lookup"><span data-stu-id="8a91f-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a91f-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8a91f-119">Child Elements</span></span>  
  
|<span data-ttu-id="8a91f-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8a91f-120">Element</span></span>|<span data-ttu-id="8a91f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a91f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a91f-122">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="8a91f-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="8a91f-123">Especifica as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="8a91f-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="8a91f-124">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="8a91f-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="8a91f-125">Especifica as configurações de cache da fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="8a91f-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8a91f-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8a91f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="8a91f-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="8a91f-127">Element</span></span>|<span data-ttu-id="8a91f-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a91f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a91f-129">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="8a91f-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8a91f-130">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="8a91f-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a91f-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a91f-131">Remarks</span></span>  
 <span data-ttu-id="8a91f-132">Esse comportamento de serviço destina-se a fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="8a91f-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="8a91f-133">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8a91f-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="8a91f-134">Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagem é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache).</span><span class="sxs-lookup"><span data-stu-id="8a91f-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="8a91f-135">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="8a91f-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="8a91f-136">O cache é desabilitado por padrão para qualquer atividade de envio do fluxo de trabalho que tem pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="8a91f-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="8a91f-137">Para obter mais informações sobre como alterar os níveis de compartilhamento de cache padrão e as configurações de cache para a fábrica de canais e o cache de canal, consulte [alterando os níveis de compartilhamento de cache para atividades de envio](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="8a91f-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a91f-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a91f-138">Example</span></span>  
 <span data-ttu-id="8a91f-139">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a91f-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="8a91f-140">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="8a91f-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="8a91f-141">O exemplo a seguir mostra o conteúdo de um arquivo de configuração que `MyChannelCacheBehavior` contém o comportamento do serviço com o cache de fábrica personalizado e as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="8a91f-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="8a91f-142">Esse comportamento de serviço é adicionado ao serviço por meio `behaviorConfiguration` do atributo.</span><span class="sxs-lookup"><span data-stu-id="8a91f-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a91f-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a91f-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="8a91f-144">Alterar o nível de compartilhamento de cache para atividades de envio</span><span class="sxs-lookup"><span data-stu-id="8a91f-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
