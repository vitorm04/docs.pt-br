---
title: Alterando os níveis de compartilhamento de cache para enviar atividades
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 359a9189cee34eeb814a2303be3d2da725456e39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494524"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Alterando os níveis de compartilhamento de cache para enviar atividades
O <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão permite que você personalize o cache compartilhamento níveis, as configurações de cache da fábrica de canal, e as configurações do canal de cache para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando <xref:System.ServiceModel.Activities.Send> atividades de mensagens. Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>. O cache de fábrica de canal contém em cache <xref:System.ServiceModel.ChannelFactory%601> objetos. O cache de canal contém canais armazenadas em cache.  
  
> [!NOTE]
>  Fluxos de trabalho podem usar <xref:System.ServiceModel.Activities.Send> atividades para enviar mensagens ou parâmetros de mensagens. O tempo de execução do fluxo de trabalho adiciona fábricas de canais para o cache que cria canais de tipo <xref:System.ServiceModel.Channels.IRequestChannel> quando você usa um <xref:System.ServiceModel.Activities.ReceiveReply> atividade com um <xref:System.ServiceModel.Activities.Send> atividade e um <xref:System.ServiceModel.Channels.IOutputChannel> ao usar apenas um <xref:System.ServiceModel.Activities.Send> atividade (nenhum <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Os níveis de compartilhamento de Cache  
 Por padrão, em um fluxo de trabalho hospedado por um <xref:System.ServiceModel.WorkflowServiceHost> o cache usado pelo <xref:System.ServiceModel.Activities.Send> atividades de mensagens é compartilhada entre todas as instâncias de fluxo de trabalho no <xref:System.ServiceModel.WorkflowServiceHost> (nível de host de cache). Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância). O cache está disponível apenas para <xref:System.ServiceModel.Activities.Send> atividades que não usam pontos de extremidade definidos na configuração, a menos que o cache não segura está habilitado.  
  
 Estes são os diferente cache compartilhamento níveis disponíveis para <xref:System.ServiceModel.Activities.Send> atividades em um fluxo de trabalho e seu uso recomendado:  
  
-   **Nível de host**: no host de nível de compartilhamento, o cache está disponível apenas para as instâncias de fluxo de trabalho hospedadas no host de serviço de fluxo de trabalho. Um cache também pode ser compartilhado entre os hosts de serviço de fluxo de trabalho em um cache de todo o processo.  
  
-   **Nível de instância**: a instância de nível de compartilhamento, o cache está disponível para uma instância de fluxo de trabalho específico durante sua vida útil, mas o cache não está disponível para outras instâncias de fluxo de trabalho.  
  
-   **Nenhum Cache**: O cache está desativado por padrão se você tiver um fluxo de trabalho que usa pontos de extremidade definidos na configuração. Também é recomendável manter o cache desativado neste caso porque ativá-lo pode ser não segura. Por exemplo, se uma identidade (credenciais diferentes ou usando a representação) é necessária para cada envio.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Alterar o nível de compartilhamento para um fluxo de trabalho do cliente de Cache  
 Para definir o cache de compartilhamento em um fluxo de trabalho do cliente, adicione uma instância do <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe como uma extensão para o conjunto desejado de instâncias de fluxo de trabalho. Isso resulta em cache de compartilhamento em todas as instâncias de fluxo de trabalho. Os exemplos de código a seguir mostram como executar essas etapas.  
  
 Primeiro, declare uma instância do tipo <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Em seguida, adicione a extensão de cache para cada instância de fluxo de trabalho do cliente.  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Alterar o nível de compartilhamento para um serviço hospedado de fluxo de trabalho de Cache  
 Para definir o cache de compartilhamento em um serviço hospedado de fluxo de trabalho, adicione uma instância do <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe como uma extensão para todos os hosts de serviço de fluxo de trabalho. Isso resulta no compartilhamento de cache entre todos os hosts de serviço de fluxo de trabalho. Os exemplos de código a seguir mostram a executar essas etapas.  
  
 Primeiro, declare uma instância do tipo <xref:System.ServiceModel.Activities.SendMessageChannelCache> no nível de classe.  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Em seguida, adicione a extensão de cache estático para cada host de serviço de fluxo de trabalho.  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Para definir o cache de compartilhamento em um serviço hospedado de fluxo de trabalho para o nível de instância, adicione um `Func<SendMessageChannelCache>` delegar como uma extensão para o host de serviço de fluxo de trabalho e atribuir esse delegado para o código que cria uma nova instância do <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe. Isso resulta em um cache diferente para cada instância de fluxo de trabalho individuais, em vez de um único cache compartilhado por todas as instâncias de fluxo de trabalho no host do serviço de fluxo de trabalho. O exemplo de código a seguir mostra como fazer isso usando uma expressão lambda para definir diretamente a <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão aponta o delegado.  
  
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
  
## <a name="customizing-cache-settings"></a>Personalizar as configurações de Cache  
 Você pode personalizar as configurações de cache para o cache de fábrica de canal e o cache de canal. As configurações de cache são definidas de <xref:System.ServiceModel.Activities.ChannelCacheSettings> classe. O <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe define as configurações de cache padrão para o cache de fábrica de canal e o cache de canal em seu construtor padrão. A tabela a seguir lista os valores padrão dessas configurações de cache para cada tipo de cache.  
  
|Configurações|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Padrão de Cache de fábrica|TimeSpan. MaxValue|2|16|  
|Padrão de Cache do canal|5|2|16|  
  
 Para personalizar as configurações de cache de cache e o canal de fábrica, instanciar o <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe usando o construtor com parâmetros <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> e passar uma nova instância do <xref:System.ServiceModel.Activities.ChannelCacheSettings> com valores personalizados para cada uma da `factorySettings` e `channelSettings` parâmetros. Em seguida, adicione a nova instância da classe como uma extensão a um host de serviço de fluxo de trabalho ou uma instância de fluxo de trabalho. O exemplo de código a seguir mostra como executar essas etapas para uma instância de fluxo de trabalho.  
  
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
  
 Para habilitar o cache quando o serviço de fluxo de trabalho tem pontos de extremidade definidos na configuração, instanciar o <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe usando o construtor com parâmetros <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> com o `allowUnsafeCaching` parâmetro definido como `true`. Em seguida, adicione a nova instância da classe como uma extensão a um host de serviço de fluxo de trabalho ou uma instância de fluxo de trabalho. O exemplo de código a seguir mostra como habilitar o cache para uma instância de fluxo de trabalho.  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Para desabilitar o cache completamente para as fábricas de canais e canais, desabilite o cache de fábrica de canal. Isso também desativa o cache de canal como os canais pertencem a seus fábricas de canais correspondente. Para desabilitar o cache de fábrica de canal, passar o `factorySettings` parâmetro para o <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> construtor inicializada com um <xref:System.ServiceModel.Activities.ChannelCacheSettings> instância com um <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> valor de 0. O exemplo de código a seguir mostra isso.  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Você pode optar por usar somente o cache de fábrica de canal e desabilitar o cache de canal, passando o `channelSettings` parâmetro para o <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> construtor inicializada com um <xref:System.ServiceModel.Activities.ChannelCacheSettings> instância com um <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> valor de 0. O exemplo de código a seguir mostra isso.  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo. Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço. O exemplo a seguir mostra o conteúdo de um arquivo de configuração que contém o `MyChannelCacheBehavior` comportamento de serviço com as configurações de cache de cache e o canal de fábrica personalizada. Esse comportamento de serviço é adicionado ao serviço através de `behaviorConfiguarion` atributo.  
  
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
