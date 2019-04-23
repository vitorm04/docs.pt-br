---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: 60847f423c61b9e7f49a4a7594c965fb75354714
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140173"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="7045b-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="7045b-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="7045b-102">Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="7045b-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="7045b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7045b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7045b-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7045b-104">\<behaviors></span></span>  
<span data-ttu-id="7045b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7045b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="7045b-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7045b-106">\<behavior></span></span>  
<span data-ttu-id="7045b-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="7045b-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7045b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7045b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7045b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7045b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7045b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7045b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7045b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7045b-111">Attributes</span></span>  
  
|<span data-ttu-id="7045b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7045b-112">Attribute</span></span>|<span data-ttu-id="7045b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7045b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7045b-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="7045b-114">allowUnsafeCaching</span></span>|<span data-ttu-id="7045b-115">Um valor booliano que indica se deve ativar o cache.</span><span class="sxs-lookup"><span data-stu-id="7045b-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="7045b-116">Se o serviço de fluxo de trabalho tiver ligações personalizadas ou comportamentos personalizados, o cache pode ser insegura e, portanto, está desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="7045b-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="7045b-117">No entanto, se você quiser ativar o cache em Defina esta propriedade como **verdadeira**.</span><span class="sxs-lookup"><span data-stu-id="7045b-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7045b-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7045b-118">Child Elements</span></span>  
  
|<span data-ttu-id="7045b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="7045b-119">Element</span></span>|<span data-ttu-id="7045b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="7045b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7045b-121">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="7045b-121">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="7045b-122">Especifica as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="7045b-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="7045b-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="7045b-123">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="7045b-124">Especifica as configurações de cache da fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="7045b-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7045b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7045b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7045b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="7045b-126">Element</span></span>|<span data-ttu-id="7045b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="7045b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7045b-128">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7045b-128">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7045b-129">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="7045b-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7045b-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="7045b-130">Remarks</span></span>  
 <span data-ttu-id="7045b-131">Esse comportamento de serviço destina-se a fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="7045b-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="7045b-132">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7045b-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="7045b-133">Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagem é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache).</span><span class="sxs-lookup"><span data-stu-id="7045b-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="7045b-134">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="7045b-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="7045b-135">O cache é desabilitado por padrão para qualquer atividade de envio do fluxo de trabalho que tem pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="7045b-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="7045b-136">Para obter mais informações sobre como alterar o cache padrão do compartilhamento níveis e configurações de cache para a fábrica de canais e cache de canal, consulte [alterando os níveis de compartilhamento de Cache para enviar atividades](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="7045b-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7045b-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7045b-137">Example</span></span>  
 <span data-ttu-id="7045b-138">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7045b-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="7045b-139">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="7045b-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="7045b-140">O exemplo a seguir mostra o conteúdo de um arquivo de configuração que contém o **MyChannelCacheBehavior** comportamento de serviço com as configurações de cache de canal e do cache de fábrica personalizada.</span><span class="sxs-lookup"><span data-stu-id="7045b-140">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="7045b-141">Esse comportamento de serviço é adicionado ao serviço por meio de **behaviorConfiguarion** atributo.</span><span class="sxs-lookup"><span data-stu-id="7045b-141">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7045b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7045b-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="7045b-143">Alterar o nível de compartilhamento de cache para atividades de envio</span><span class="sxs-lookup"><span data-stu-id="7045b-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
