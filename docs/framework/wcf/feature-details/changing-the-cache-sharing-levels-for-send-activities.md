---
title: "Alterando os níveis de compartilhamento de cache para enviar atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c6ae1ae31a5aa256844e6efca158e4702b6aba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="504f4-102">Alterando os níveis de compartilhamento de cache para enviar atividades</span><span class="sxs-lookup"><span data-stu-id="504f4-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="504f4-103">O <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão permite que você personalize o cache compartilhamento níveis, as configurações de cache da fábrica de canal, e as configurações do canal de cache para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando <xref:System.ServiceModel.Activities.Send> atividades de mensagens.</span><span class="sxs-lookup"><span data-stu-id="504f4-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="504f4-104">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="504f4-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="504f4-105">O cache de fábrica de canal contém em cache <xref:System.ServiceModel.ChannelFactory%601> objetos.</span><span class="sxs-lookup"><span data-stu-id="504f4-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="504f4-106">O cache de canal contém canais armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="504f4-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="504f4-107">Fluxos de trabalho podem usar <xref:System.ServiceModel.Activities.Send> atividades para enviar mensagens ou parâmetros de mensagens.</span><span class="sxs-lookup"><span data-stu-id="504f4-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="504f4-108">O tempo de execução do fluxo de trabalho adiciona fábricas de canais para o cache que cria canais de tipo <xref:System.ServiceModel.Channels.IRequestChannel> quando você usa um <xref:System.ServiceModel.Activities.ReceiveReply> atividade com um <xref:System.ServiceModel.Activities.Send> atividade e um <xref:System.ServiceModel.Channels.IOutputChannel> ao usar apenas um <xref:System.ServiceModel.Activities.Send> atividade (nenhum <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="504f4-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="504f4-109">Os níveis de compartilhamento de Cache</span><span class="sxs-lookup"><span data-stu-id="504f4-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="504f4-110">Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost> o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagens é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache).</span><span class="sxs-lookup"><span data-stu-id="504f4-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="504f4-111">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="504f4-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="504f4-112">O cache está disponível apenas para <xref:System.ServiceModel.Activities.Send> atividades que não usam pontos de extremidade definidos na configuração, a menos que o cache não segura está habilitado.</span><span class="sxs-lookup"><span data-stu-id="504f4-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="504f4-113">Estes são os diferente cache compartilhamento níveis disponíveis para <xref:System.ServiceModel.Activities.Send> atividades em um fluxo de trabalho e seu uso recomendado:</span><span class="sxs-lookup"><span data-stu-id="504f4-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
-   <span data-ttu-id="504f4-114">**Nível de host**: no host de nível de compartilhamento, o cache está disponível apenas para as instâncias de fluxo de trabalho hospedadas no host de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="504f4-115">Um cache também pode ser compartilhado entre os hosts de serviço de fluxo de trabalho em um cache de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="504f4-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
-   <span data-ttu-id="504f4-116">**Nível de instância**: a instância de nível de compartilhamento, o cache está disponível para uma instância de fluxo de trabalho específico durante sua vida útil, mas o cache não está disponível para outras instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
-   <span data-ttu-id="504f4-117">**Nenhum Cache**: O cache está desativado por padrão se você tiver um fluxo de trabalho que usa pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="504f4-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="504f4-118">Também é recomendável manter o cache desativado neste caso porque ativá-lo pode ser não segura.</span><span class="sxs-lookup"><span data-stu-id="504f4-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="504f4-119">Por exemplo, se uma identidade (credenciais diferentes ou usando a representação) é necessária para cada envio.</span><span class="sxs-lookup"><span data-stu-id="504f4-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="504f4-120">Alterar o nível de compartilhamento para um fluxo de trabalho do cliente de Cache</span><span class="sxs-lookup"><span data-stu-id="504f4-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="504f4-121">Para definir o cache de compartilhamento em um fluxo de trabalho do cliente, adicione uma instância do <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe como uma extensão para o conjunto desejado de instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="504f4-122">Isso resulta em cache de compartilhamento em todas as instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="504f4-123">Os exemplos de código a seguir mostram como executar essas etapas.</span><span class="sxs-lookup"><span data-stu-id="504f4-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="504f4-124">Primeiro, declare uma instância do tipo <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="504f4-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="504f4-125">Em seguida, adicione a extensão de cache para cada instância de fluxo de trabalho do cliente.</span><span class="sxs-lookup"><span data-stu-id="504f4-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="504f4-126">Alterar o nível de compartilhamento para um serviço hospedado de fluxo de trabalho de Cache</span><span class="sxs-lookup"><span data-stu-id="504f4-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="504f4-127">Para definir o cache de compartilhamento em um serviço hospedado de fluxo de trabalho, adicione uma instância do <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe como uma extensão para todos os hosts de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="504f4-128">Isso resulta no compartilhamento de cache entre todos os hosts de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="504f4-129">Os exemplos de código a seguir mostram a executar essas etapas.</span><span class="sxs-lookup"><span data-stu-id="504f4-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="504f4-130">Primeiro, declare uma instância do tipo <xref:System.ServiceModel.Activities.SendMessageChannelCache> no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="504f4-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="504f4-131">Em seguida, adicione a extensão de cache estático para cada host de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="504f4-132">Para definir o cache de compartilhamento em um serviço hospedado de fluxo de trabalho para o nível de instância, adicione um `Func<SendMessageChannelCache>` delegar como uma extensão para o host de serviço de fluxo de trabalho e atribuir esse delegado para o código que cria uma nova instância do <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe.</span><span class="sxs-lookup"><span data-stu-id="504f4-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="504f4-133">Isso resulta em um cache diferente para cada instância de fluxo de trabalho individuais, em vez de um único cache compartilhado por todas as instâncias de fluxo de trabalho no host do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="504f4-134">O exemplo de código a seguir mostra como fazer isso usando uma expressão lambda para definir diretamente a <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão aponta o delegado.</span><span class="sxs-lookup"><span data-stu-id="504f4-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```  
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings   
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings   
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="504f4-135">Personalizar as configurações de Cache</span><span class="sxs-lookup"><span data-stu-id="504f4-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="504f4-136">Você pode personalizar as configurações de cache para o cache de fábrica de canal e o cache de canal.</span><span class="sxs-lookup"><span data-stu-id="504f4-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="504f4-137">As configurações de cache são definidas de <xref:System.ServiceModel.Activities.ChannelCacheSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="504f4-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="504f4-138">O <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe define as configurações de cache padrão para o cache de fábrica de canal e o cache de canal em seu construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="504f4-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="504f4-139">A tabela a seguir lista os valores padrão dessas configurações de cache para cada tipo de cache.</span><span class="sxs-lookup"><span data-stu-id="504f4-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="504f4-140">Configurações</span><span class="sxs-lookup"><span data-stu-id="504f4-140">Settings</span></span>|<span data-ttu-id="504f4-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="504f4-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="504f4-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="504f4-142">IdleTimeout (min)</span></span>|<span data-ttu-id="504f4-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="504f4-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="504f4-144">Padrão de Cache de fábrica</span><span class="sxs-lookup"><span data-stu-id="504f4-144">Factory Cache Default</span></span>|<span data-ttu-id="504f4-145">TimeSpan. MaxValue</span><span class="sxs-lookup"><span data-stu-id="504f4-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="504f4-146">2</span><span class="sxs-lookup"><span data-stu-id="504f4-146">2</span></span>|<span data-ttu-id="504f4-147">16</span><span class="sxs-lookup"><span data-stu-id="504f4-147">16</span></span>|  
|<span data-ttu-id="504f4-148">Padrão de Cache do canal</span><span class="sxs-lookup"><span data-stu-id="504f4-148">Channel Cache Default</span></span>|<span data-ttu-id="504f4-149">5</span><span class="sxs-lookup"><span data-stu-id="504f4-149">5</span></span>|<span data-ttu-id="504f4-150">2</span><span class="sxs-lookup"><span data-stu-id="504f4-150">2</span></span>|<span data-ttu-id="504f4-151">16</span><span class="sxs-lookup"><span data-stu-id="504f4-151">16</span></span>|  
  
 <span data-ttu-id="504f4-152">Para personalizar as configurações de cache de cache e o canal de fábrica, instanciar o <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe usando o construtor com parâmetros <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> e passar uma nova instância do <xref:System.ServiceModel.Activities.ChannelCacheSettings> com valores personalizados para cada uma da `factorySettings` e `channelSettings` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="504f4-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="504f4-153">Em seguida, adicione a nova instância da classe como uma extensão a um host de serviço de fluxo de trabalho ou uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="504f4-154">O exemplo de código a seguir mostra como executar essas etapas para uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(5),   
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="504f4-155">Para habilitar o cache quando o serviço de fluxo de trabalho tem pontos de extremidade definidos na configuração, instanciar o <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe usando o construtor com parâmetros <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> com o `allowUnsafeCaching` parâmetro definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="504f4-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="504f4-156">Em seguida, adicione a nova instância da classe como uma extensão a um host de serviço de fluxo de trabalho ou uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="504f4-157">O exemplo de código a seguir mostra como habilitar o cache para uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="504f4-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="504f4-158">Para desabilitar o cache completamente para as fábricas de canais e canais, desabilite o cache de fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="504f4-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="504f4-159">Isso também desativa o cache de canal como os canais pertencem a seus fábricas de canais correspondente.</span><span class="sxs-lookup"><span data-stu-id="504f4-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="504f4-160">Para desabilitar o cache de fábrica de canal, passar o `factorySettings` parâmetro para o <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> construtor inicializada com um <xref:System.ServiceModel.Activities.ChannelCacheSettings> instância com um <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> valor de 0.</span><span class="sxs-lookup"><span data-stu-id="504f4-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="504f4-161">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="504f4-161">The following code example shows this.</span></span>  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="504f4-162">Você pode optar por usar somente o cache de fábrica de canal e desabilitar o cache de canal, passando o `channelSettings` parâmetro para o <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> construtor inicializada com um <xref:System.ServiceModel.Activities.ChannelCacheSettings> instância com um <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> valor de 0.</span><span class="sxs-lookup"><span data-stu-id="504f4-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="504f4-163">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="504f4-163">The following code example shows this.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="504f4-164">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="504f4-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="504f4-165">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="504f4-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="504f4-166">O exemplo a seguir mostra o conteúdo de um arquivo de configuração que contém o `MyChannelCacheBehavior` comportamento de serviço com as configurações de cache de cache e o canal de fábrica personalizada.</span><span class="sxs-lookup"><span data-stu-id="504f4-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="504f4-167">Esse comportamento de serviço é adicionado ao serviço através de `behaviorConfiguarion` atributo.</span><span class="sxs-lookup"><span data-stu-id="504f4-167">This service behavior is added to the service through the `behaviorConfiguarion` attribute.</span></span>  
  
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
