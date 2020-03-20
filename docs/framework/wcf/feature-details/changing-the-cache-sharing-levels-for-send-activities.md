---
title: Alterando os níveis de compartilhamento de cache para enviar atividades
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185389"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="b6ba1-102">Alterando os níveis de compartilhamento de cache para enviar atividades</span><span class="sxs-lookup"><span data-stu-id="b6ba1-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="b6ba1-103">A <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão permite personalizar os níveis de compartilhamento de cache, as configurações do cache de fábrica do canal e <xref:System.ServiceModel.Activities.Send> as configurações do cache do canal para fluxos de trabalho que enviam mensagens para pontos finais de serviço usando atividades de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="b6ba1-104">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="b6ba1-105">O cache da fábrica <xref:System.ServiceModel.ChannelFactory%601> do canal contém objetos armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="b6ba1-106">O cache do canal contém canais armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6ba1-107">Os fluxos <xref:System.ServiceModel.Activities.Send> de trabalho podem usar atividades de mensagens para enviar mensagens ou parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="b6ba1-108">O tempo de execução do fluxo de trabalho <xref:System.ServiceModel.Channels.IRequestChannel> adiciona fábricas <xref:System.ServiceModel.Activities.ReceiveReply> de <xref:System.ServiceModel.Activities.Send> canais ao <xref:System.ServiceModel.Channels.IOutputChannel> cache que <xref:System.ServiceModel.Activities.Send> criam canais de tipo quando você usa uma atividade com uma atividade, e quando apenas usa uma atividade (não <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="b6ba1-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="b6ba1-109">Os níveis de compartilhamento de cache</span><span class="sxs-lookup"><span data-stu-id="b6ba1-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="b6ba1-110">Por padrão, em um fluxo <xref:System.ServiceModel.WorkflowServiceHost> de trabalho <xref:System.ServiceModel.Activities.Send> hospedado por um cache usado por atividades de mensagens é compartilhado em todas as instâncias de <xref:System.ServiceModel.WorkflowServiceHost> fluxo de trabalho no (cache em nível de host).</span><span class="sxs-lookup"><span data-stu-id="b6ba1-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="b6ba1-111">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="b6ba1-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="b6ba1-112">O cache só <xref:System.ServiceModel.Activities.Send> está disponível para atividades que não usam pontos finais definidos na configuração, a menos que o cache inseguro esteja ativado.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="b6ba1-113">A seguir estão os diferentes <xref:System.ServiceModel.Activities.Send> níveis de compartilhamento de cache disponíveis para atividades em um fluxo de trabalho e seu uso recomendado:</span><span class="sxs-lookup"><span data-stu-id="b6ba1-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="b6ba1-114">**Nível do host**: No nível de compartilhamento de host, o cache está disponível apenas para as instâncias de fluxo de trabalho hospedadas no host de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="b6ba1-115">Um cache também pode ser compartilhado entre hosts de serviço de fluxo de trabalho em um cache em todo o processo.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="b6ba1-116">**Nível de instância**: No nível de compartilhamento de instâncias, o cache está disponível para uma instância específica do fluxo de trabalho durante toda a sua vida, mas o cache não está disponível para outras instâncias do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="b6ba1-117">**Sem cache**: O cache é desligado por padrão se você tiver um fluxo de trabalho que usa pontos finais definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="b6ba1-118">Também é recomendável manter o cache desligado neste caso, porque ligá-lo pode ser inseguro.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="b6ba1-119">Por exemplo, se uma identidade diferente (credenciais diferentes ou usando personificação) for necessária para cada envio.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="b6ba1-120">Alterando o nível de compartilhamento de cache para um fluxo de trabalho do cliente</span><span class="sxs-lookup"><span data-stu-id="b6ba1-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="b6ba1-121">Para definir o compartilhamento de cache em um <xref:System.ServiceModel.Activities.SendMessageChannelCache> fluxo de trabalho do cliente, adicione uma instância da classe como uma extensão ao conjunto desejado de instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="b6ba1-122">Isso resulta no compartilhamento do cache em todas as instâncias do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="b6ba1-123">Os exemplos de código a seguir mostram como executar essas etapas.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="b6ba1-124">Primeiro, declare uma <xref:System.ServiceModel.Activities.SendMessageChannelCache>instância do tipo .</span><span class="sxs-lookup"><span data-stu-id="b6ba1-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="b6ba1-125">Em seguida, adicione a extensão de cache a cada instância de fluxo de trabalho do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="b6ba1-126">Alterando o nível de compartilhamento de cache para um serviço de fluxo de trabalho hospedado</span><span class="sxs-lookup"><span data-stu-id="b6ba1-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="b6ba1-127">Para definir o compartilhamento de cache em um serviço <xref:System.ServiceModel.Activities.SendMessageChannelCache> de fluxo de trabalho hospedado, adicione uma instância da classe como uma extensão para todos os hosts de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="b6ba1-128">Isso resulta no compartilhamento do cache em todos os hosts de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="b6ba1-129">Os exemplos de código a seguir mostram para executar essas etapas.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="b6ba1-130">Primeiro, declare uma <xref:System.ServiceModel.Activities.SendMessageChannelCache> instância de tipo no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="b6ba1-131">Em seguida, adicione a extensão de cache estático a cada host de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="b6ba1-132">Para definir o compartilhamento de cache em um serviço de `Func<SendMessageChannelCache>` fluxo de trabalho hospedado ao nível de instância, adicione um delegado como uma <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão ao host de serviço de fluxo de trabalho e atribua esse delegado ao código que instancia uma nova instância da classe.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="b6ba1-133">Isso resulta em um cache diferente para cada instância de fluxo de trabalho individual, em vez de um único cache compartilhado por todas as instâncias de fluxo de trabalho no host de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="b6ba1-134">O exemplo de código a seguir mostra como conseguir isso <xref:System.ServiceModel.Activities.SendMessageChannelCache> usando uma expressão lambda para definir diretamente a extensão que o delegado aponta.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="b6ba1-135">Personalização das configurações de cache</span><span class="sxs-lookup"><span data-stu-id="b6ba1-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="b6ba1-136">Você pode personalizar as configurações de cache para o cache de fábrica do canal e o cache do canal.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="b6ba1-137">As configurações de cache <xref:System.ServiceModel.Activities.ChannelCacheSettings> são definidas na classe.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="b6ba1-138">A <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe define as configurações de cache padrão para o cache de fábrica do canal e o cache do canal em seu construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="b6ba1-139">A tabela a seguir lista os valores padrão dessas configurações de cache para cada tipo de cache.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="b6ba1-140">Configurações</span><span class="sxs-lookup"><span data-stu-id="b6ba1-140">Settings</span></span>|<span data-ttu-id="b6ba1-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="b6ba1-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="b6ba1-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="b6ba1-142">IdleTimeout (min)</span></span>|<span data-ttu-id="b6ba1-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="b6ba1-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="b6ba1-144">Padrão de cache de fábrica</span><span class="sxs-lookup"><span data-stu-id="b6ba1-144">Factory Cache Default</span></span>|<span data-ttu-id="b6ba1-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="b6ba1-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="b6ba1-146">2</span><span class="sxs-lookup"><span data-stu-id="b6ba1-146">2</span></span>|<span data-ttu-id="b6ba1-147">16</span><span class="sxs-lookup"><span data-stu-id="b6ba1-147">16</span></span>|  
|<span data-ttu-id="b6ba1-148">Padrão de cache do canal</span><span class="sxs-lookup"><span data-stu-id="b6ba1-148">Channel Cache Default</span></span>|<span data-ttu-id="b6ba1-149">5</span><span class="sxs-lookup"><span data-stu-id="b6ba1-149">5</span></span>|<span data-ttu-id="b6ba1-150">2</span><span class="sxs-lookup"><span data-stu-id="b6ba1-150">2</span></span>|<span data-ttu-id="b6ba1-151">16</span><span class="sxs-lookup"><span data-stu-id="b6ba1-151">16</span></span>|  
  
 <span data-ttu-id="b6ba1-152">Para personalizar as configurações de cache de <xref:System.ServiceModel.Activities.SendMessageChannelCache> fábrica e de canal, instanciar a classe usando o construtor parametrizado <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> e passar uma nova instância do <xref:System.ServiceModel.Activities.ChannelCacheSettings> com valores personalizados para cada um dos `factorySettings` parâmetros. `channelSettings`</span><span class="sxs-lookup"><span data-stu-id="b6ba1-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="b6ba1-153">Em seguida, adicione a nova instância desta classe como uma extensão a um host de serviço de fluxo de trabalho ou a uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="b6ba1-154">O exemplo de código a seguir mostra como executar essas etapas para uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b6ba1-155">Para habilitar o cache quando o serviço de fluxo <xref:System.ServiceModel.Activities.SendMessageChannelCache> de trabalho tiver pontos <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> finais `allowUnsafeCaching` definidos na `true`configuração, instanciar a classe usando o construtor parametrizado com o parâmetro definido para .</span><span class="sxs-lookup"><span data-stu-id="b6ba1-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="b6ba1-156">Em seguida, adicione a nova instância desta classe como uma extensão a um host de serviço de fluxo de trabalho ou a uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="b6ba1-157">O exemplo de código a seguir mostra como ativar o cache de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="b6ba1-158">Para desativar completamente o cache para as fábricas de canais e os canais, desative o cache da fábrica do canal.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="b6ba1-159">Ao fazer isso, também desliga o cache do canal, pois os canais são de propriedade de suas fábricas de canais correspondentes.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="b6ba1-160">Para desativar o cache da `factorySettings` fábrica do <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> canal, passe o <xref:System.ServiceModel.Activities.ChannelCacheSettings> parâmetro <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> para o construtor inicializado para uma instância com um valor de 0.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="b6ba1-161">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="b6ba1-162">Você pode optar por usar apenas o cache de fábrica `channelSettings` do canal <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> e desativar o <xref:System.ServiceModel.Activities.ChannelCacheSettings> cache <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do canal passando o parâmetro para o construtor inicializado para uma instância com um valor de 0.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="b6ba1-163">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="b6ba1-164">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="b6ba1-165">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="b6ba1-166">O exemplo a seguir mostra o conteúdo `MyChannelCacheBehavior` de um arquivo de configuração que contém o comportamento do serviço com as configurações personalizadas de cache de fábrica e cache de canal.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="b6ba1-167">Esse comportamento de serviço é `behaviorConfiguration` adicionado ao serviço através do atributo.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
