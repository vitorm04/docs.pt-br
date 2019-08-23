---
title: Alterando os níveis de compartilhamento de cache para enviar atividades
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 587440bd343513aeff51f1ed0947573fbe612f22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952583"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="c5bc3-102">Alterando os níveis de compartilhamento de cache para enviar atividades</span><span class="sxs-lookup"><span data-stu-id="c5bc3-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="c5bc3-103">A <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão permite que você personalize os níveis de compartilhamento de cache, as configurações do cache da fábrica de canais e as configurações do cache do canal para fluxos de trabalho que enviam mensagens para pontos <xref:System.ServiceModel.Activities.Send> de extremidade de serviço usando atividades de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="c5bc3-104">Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="c5bc3-105">O cache da fábrica de canais contém <xref:System.ServiceModel.ChannelFactory%601> objetos armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="c5bc3-106">O cache do canal contém canais armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5bc3-107">Os fluxos de trabalho <xref:System.ServiceModel.Activities.Send> podem usar atividades de mensagens para enviar mensagens ou parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="c5bc3-108">O tempo de execução do fluxo de trabalho adiciona fábricas de canal ao cache <xref:System.ServiceModel.Channels.IRequestChannel> que cria canais do <xref:System.ServiceModel.Activities.ReceiveReply> tipo quando você <xref:System.ServiceModel.Activities.Send> usa uma atividade com <xref:System.ServiceModel.Channels.IOutputChannel> uma atividade e um <xref:System.ServiceModel.Activities.Send> ao usar apenas <xref:System.ServiceModel.Activities.ReceiveReply>uma atividade (não).</span><span class="sxs-lookup"><span data-stu-id="c5bc3-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="c5bc3-109">Os níveis de compartilhamento de cache</span><span class="sxs-lookup"><span data-stu-id="c5bc3-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="c5bc3-110">Por padrão, em um fluxo de trabalho hospedado <xref:System.ServiceModel.WorkflowServiceHost> por um cache usado <xref:System.ServiceModel.Activities.Send> pelas atividades de mensagens é compartilhado entre <xref:System.ServiceModel.WorkflowServiceHost> todas as instâncias de fluxo de trabalho no (cache de nível de host).</span><span class="sxs-lookup"><span data-stu-id="c5bc3-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="c5bc3-111">Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância).</span><span class="sxs-lookup"><span data-stu-id="c5bc3-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="c5bc3-112">O cache só está disponível para <xref:System.ServiceModel.Activities.Send> atividades que não usam pontos de extremidade definidos na configuração, a menos que o cache não seguro esteja habilitado.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="c5bc3-113">A seguir estão os diferentes níveis de compartilhamento de cache <xref:System.ServiceModel.Activities.Send> disponíveis para atividades em um fluxo de trabalho e seu uso recomendado:</span><span class="sxs-lookup"><span data-stu-id="c5bc3-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="c5bc3-114">**Nível do host**: No nível de compartilhamento de host, o cache está disponível somente para as instâncias de fluxo de trabalho hospedadas no host do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="c5bc3-115">Um cache também pode ser compartilhado entre hosts do serviço de fluxo de trabalho em um cache de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="c5bc3-116">**Nível de instância**: No nível de compartilhamento de instância, o cache está disponível para uma instância de fluxo de trabalho específica durante seu tempo de vida, mas o cache não está disponível para outras instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="c5bc3-117">**Sem cache**: O cache será desativado por padrão se você tiver um fluxo de trabalho que usa pontos de extremidade definidos na configuração.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="c5bc3-118">Também é recomendável manter o cache desativado nesse caso porque ativá-lo pode não ser seguro.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="c5bc3-119">Por exemplo, se uma identidade diferente (credenciais diferentes ou o uso da representação) for necessária para cada envio.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="c5bc3-120">Alterando o nível de compartilhamento do cache para um fluxo de trabalho do cliente</span><span class="sxs-lookup"><span data-stu-id="c5bc3-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="c5bc3-121">Para definir o compartilhamento de cache em um fluxo de trabalho de cliente, adicione <xref:System.ServiceModel.Activities.SendMessageChannelCache> uma instância da classe como uma extensão para o conjunto desejado de instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="c5bc3-122">Isso resulta no compartilhamento do cache em todas as instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="c5bc3-123">Os exemplos de código a seguir mostram como executar essas etapas.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="c5bc3-124">Primeiro, declare uma instância do tipo <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="c5bc3-125">Em seguida, adicione a extensão de cache a cada instância de fluxo de trabalho do cliente.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="c5bc3-126">Alterando o nível de compartilhamento do cache para um serviço de fluxo de trabalho hospedado</span><span class="sxs-lookup"><span data-stu-id="c5bc3-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="c5bc3-127">Para definir o compartilhamento de cache em um serviço de fluxo de trabalho hospedado, adicione <xref:System.ServiceModel.Activities.SendMessageChannelCache> uma instância da classe como uma extensão a todos os hosts do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="c5bc3-128">Isso resulta no compartilhamento do cache em todos os hosts do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="c5bc3-129">Os exemplos de código a seguir mostram como executar essas etapas.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="c5bc3-130">Primeiro, declare uma instância do tipo <xref:System.ServiceModel.Activities.SendMessageChannelCache> no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="c5bc3-131">Em seguida, adicione a extensão de cache estático a cada host de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="c5bc3-132">Para definir o compartilhamento de cache em um serviço de fluxo de trabalho hospedado para o nível `Func<SendMessageChannelCache>` de instância, adicione um delegado como uma extensão ao host do serviço de fluxo de trabalho e atribua esse delegado ao código que <xref:System.ServiceModel.Activities.SendMessageChannelCache> instancia uma nova instância da classe.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="c5bc3-133">Isso resulta em um cache diferente para cada instância de fluxo de trabalho individual, em vez de um único cache compartilhado por todas as instâncias de fluxo de trabalho no host do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="c5bc3-134">O exemplo de código a seguir mostra como conseguir isso usando uma expressão lambda para definir diretamente a <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão à qual o delegado aponta.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="c5bc3-135">Personalizando configurações de cache</span><span class="sxs-lookup"><span data-stu-id="c5bc3-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="c5bc3-136">Você pode personalizar as configurações de cache para o cache de fábrica do canal e o cache do canal.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="c5bc3-137">As configurações de cache são definidas na <xref:System.ServiceModel.Activities.ChannelCacheSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="c5bc3-138">A <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe define as configurações de cache padrão para o cache de fábrica de canais e o cache de canal em seu construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="c5bc3-139">A tabela a seguir lista os valores padrão dessas configurações de cache para cada tipo de cache.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="c5bc3-140">Configurações</span><span class="sxs-lookup"><span data-stu-id="c5bc3-140">Settings</span></span>|<span data-ttu-id="c5bc3-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="c5bc3-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="c5bc3-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="c5bc3-142">IdleTimeout (min)</span></span>|<span data-ttu-id="c5bc3-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="c5bc3-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="c5bc3-144">Padrão de cache de fábrica</span><span class="sxs-lookup"><span data-stu-id="c5bc3-144">Factory Cache Default</span></span>|<span data-ttu-id="c5bc3-145">TimeSpan. MaxValue</span><span class="sxs-lookup"><span data-stu-id="c5bc3-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="c5bc3-146">2</span><span class="sxs-lookup"><span data-stu-id="c5bc3-146">2</span></span>|<span data-ttu-id="c5bc3-147">16</span><span class="sxs-lookup"><span data-stu-id="c5bc3-147">16</span></span>|  
|<span data-ttu-id="c5bc3-148">Padrão de cache do canal</span><span class="sxs-lookup"><span data-stu-id="c5bc3-148">Channel Cache Default</span></span>|<span data-ttu-id="c5bc3-149">5</span><span class="sxs-lookup"><span data-stu-id="c5bc3-149">5</span></span>|<span data-ttu-id="c5bc3-150">2</span><span class="sxs-lookup"><span data-stu-id="c5bc3-150">2</span></span>|<span data-ttu-id="c5bc3-151">16</span><span class="sxs-lookup"><span data-stu-id="c5bc3-151">16</span></span>|  
  
 <span data-ttu-id="c5bc3-152">Para personalizar o cache de fábrica e as configurações de cache do <xref:System.ServiceModel.Activities.SendMessageChannelCache> canal, crie uma instância da <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> classe usando o construtor <xref:System.ServiceModel.Activities.ChannelCacheSettings> `channelSettings` com parâmetros e passe uma nova instância do com valores `factorySettings` personalizados para cada um dos parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="c5bc3-153">Em seguida, adicione a nova instância dessa classe como uma extensão a um host do serviço de fluxo de trabalho ou a uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="c5bc3-154">O exemplo de código a seguir mostra como executar essas etapas para uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
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
  
 <span data-ttu-id="c5bc3-155">Para habilitar o Caching quando seu serviço de fluxo de trabalho tiver pontos de extremidade definidos na <xref:System.ServiceModel.Activities.SendMessageChannelCache> configuração, crie uma instância da <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> classe usando `allowUnsafeCaching` o construtor com `true`parâmetros com o parâmetro definido como.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="c5bc3-156">Em seguida, adicione a nova instância dessa classe como uma extensão a um host do serviço de fluxo de trabalho ou a uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="c5bc3-157">O exemplo de código a seguir mostra como habilitar o Caching para uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="c5bc3-158">Para desabilitar completamente o cache para as fábricas de canal e os canais, desabilite o cache da fábrica de canais.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="c5bc3-159">Fazer isso também desativa o cache do canal à medida que os canais são de propriedade de suas fábricas de canal correspondentes.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="c5bc3-160">Para desabilitar o cache da fábrica de canais, `factorySettings` passe o parâmetro <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> para o Construtor inicializado para uma <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> instância com um valor de 0.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="c5bc3-161">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="c5bc3-162">Você pode optar por usar apenas o cache da fábrica do canal e desabilitar o cache do canal `channelSettings` passando o parâmetro <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> para o Construtor inicializado para uma <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> instância com um valor de 0.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="c5bc3-163">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="c5bc3-164">Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="c5bc3-165">Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="c5bc3-166">O exemplo a seguir mostra o conteúdo de um arquivo de configuração que `MyChannelCacheBehavior` contém o comportamento do serviço com o cache de fábrica personalizado e as configurações de cache do canal.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="c5bc3-167">Esse comportamento de serviço é adicionado ao serviço por meio `behaviorConfiguration` do atributo.</span><span class="sxs-lookup"><span data-stu-id="c5bc3-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
