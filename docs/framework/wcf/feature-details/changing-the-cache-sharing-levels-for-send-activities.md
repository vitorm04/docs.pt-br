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
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Alterando os níveis de compartilhamento de cache para enviar atividades
A <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão permite personalizar os níveis de compartilhamento de cache, as configurações do cache de fábrica do canal e <xref:System.ServiceModel.Activities.Send> as configurações do cache do canal para fluxos de trabalho que enviam mensagens para pontos finais de serviço usando atividades de mensagens. Esses fluxos de trabalho normalmente são fluxos de trabalho do cliente, mas também pode ser o serviços de fluxo de trabalho que são hospedados em um <xref:System.ServiceModel.WorkflowServiceHost>. O cache da fábrica <xref:System.ServiceModel.ChannelFactory%601> do canal contém objetos armazenados em cache. O cache do canal contém canais armazenados em cache.  
  
> [!NOTE]
> Os fluxos <xref:System.ServiceModel.Activities.Send> de trabalho podem usar atividades de mensagens para enviar mensagens ou parâmetros. O tempo de execução do fluxo de trabalho <xref:System.ServiceModel.Channels.IRequestChannel> adiciona fábricas <xref:System.ServiceModel.Activities.ReceiveReply> de <xref:System.ServiceModel.Activities.Send> canais ao <xref:System.ServiceModel.Channels.IOutputChannel> cache que <xref:System.ServiceModel.Activities.Send> criam canais de tipo quando você usa uma atividade com uma atividade, e quando apenas usa uma atividade (não <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Os níveis de compartilhamento de cache  
 Por padrão, em um fluxo <xref:System.ServiceModel.WorkflowServiceHost> de trabalho <xref:System.ServiceModel.Activities.Send> hospedado por um cache usado por atividades de mensagens é compartilhado em todas as instâncias de <xref:System.ServiceModel.WorkflowServiceHost> fluxo de trabalho no (cache em nível de host). Um fluxo de trabalho de cliente não é hospedado por um <xref:System.ServiceModel.WorkflowServiceHost>, o cache está disponível somente para a instância de fluxo de trabalho (cache de nível de instância). O cache só <xref:System.ServiceModel.Activities.Send> está disponível para atividades que não usam pontos finais definidos na configuração, a menos que o cache inseguro esteja ativado.  
  
 A seguir estão os diferentes <xref:System.ServiceModel.Activities.Send> níveis de compartilhamento de cache disponíveis para atividades em um fluxo de trabalho e seu uso recomendado:  
  
- **Nível do host**: No nível de compartilhamento de host, o cache está disponível apenas para as instâncias de fluxo de trabalho hospedadas no host de serviço de fluxo de trabalho. Um cache também pode ser compartilhado entre hosts de serviço de fluxo de trabalho em um cache em todo o processo.  
  
- **Nível de instância**: No nível de compartilhamento de instâncias, o cache está disponível para uma instância específica do fluxo de trabalho durante toda a sua vida, mas o cache não está disponível para outras instâncias do fluxo de trabalho.  
  
- **Sem cache**: O cache é desligado por padrão se você tiver um fluxo de trabalho que usa pontos finais definidos na configuração. Também é recomendável manter o cache desligado neste caso, porque ligá-lo pode ser inseguro. Por exemplo, se uma identidade diferente (credenciais diferentes ou usando personificação) for necessária para cada envio.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Alterando o nível de compartilhamento de cache para um fluxo de trabalho do cliente  
 Para definir o compartilhamento de cache em um <xref:System.ServiceModel.Activities.SendMessageChannelCache> fluxo de trabalho do cliente, adicione uma instância da classe como uma extensão ao conjunto desejado de instâncias de fluxo de trabalho. Isso resulta no compartilhamento do cache em todas as instâncias do fluxo de trabalho. Os exemplos de código a seguir mostram como executar essas etapas.  
  
 Primeiro, declare uma <xref:System.ServiceModel.Activities.SendMessageChannelCache>instância do tipo .  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Em seguida, adicione a extensão de cache a cada instância de fluxo de trabalho do cliente.  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Alterando o nível de compartilhamento de cache para um serviço de fluxo de trabalho hospedado  
 Para definir o compartilhamento de cache em um serviço <xref:System.ServiceModel.Activities.SendMessageChannelCache> de fluxo de trabalho hospedado, adicione uma instância da classe como uma extensão para todos os hosts de serviço de fluxo de trabalho. Isso resulta no compartilhamento do cache em todos os hosts de serviço de fluxo de trabalho. Os exemplos de código a seguir mostram para executar essas etapas.  
  
 Primeiro, declare uma <xref:System.ServiceModel.Activities.SendMessageChannelCache> instância de tipo no nível de classe.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Em seguida, adicione a extensão de cache estático a cada host de serviço de fluxo de trabalho.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Para definir o compartilhamento de cache em um serviço de `Func<SendMessageChannelCache>` fluxo de trabalho hospedado ao nível de instância, adicione um delegado como uma <xref:System.ServiceModel.Activities.SendMessageChannelCache> extensão ao host de serviço de fluxo de trabalho e atribua esse delegado ao código que instancia uma nova instância da classe. Isso resulta em um cache diferente para cada instância de fluxo de trabalho individual, em vez de um único cache compartilhado por todas as instâncias de fluxo de trabalho no host de serviço de fluxo de trabalho. O exemplo de código a seguir mostra como conseguir isso <xref:System.ServiceModel.Activities.SendMessageChannelCache> usando uma expressão lambda para definir diretamente a extensão que o delegado aponta.  
  
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
  
## <a name="customizing-cache-settings"></a>Personalização das configurações de cache  
 Você pode personalizar as configurações de cache para o cache de fábrica do canal e o cache do canal. As configurações de cache <xref:System.ServiceModel.Activities.ChannelCacheSettings> são definidas na classe. A <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe define as configurações de cache padrão para o cache de fábrica do canal e o cache do canal em seu construtor sem parâmetros. A tabela a seguir lista os valores padrão dessas configurações de cache para cada tipo de cache.  
  
|Configurações|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Padrão de cache de fábrica|TimeSpan.MaxValue|2|16|  
|Padrão de cache do canal|5|2|16|  
  
 Para personalizar as configurações de cache de <xref:System.ServiceModel.Activities.SendMessageChannelCache> fábrica e de canal, instanciar a classe usando o construtor parametrizado <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> e passar uma nova instância do <xref:System.ServiceModel.Activities.ChannelCacheSettings> com valores personalizados para cada um dos `factorySettings` parâmetros. `channelSettings` Em seguida, adicione a nova instância desta classe como uma extensão a um host de serviço de fluxo de trabalho ou a uma instância de fluxo de trabalho. O exemplo de código a seguir mostra como executar essas etapas para uma instância de fluxo de trabalho.  
  
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
  
 Para habilitar o cache quando o serviço de fluxo <xref:System.ServiceModel.Activities.SendMessageChannelCache> de trabalho tiver pontos <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> finais `allowUnsafeCaching` definidos na `true`configuração, instanciar a classe usando o construtor parametrizado com o parâmetro definido para . Em seguida, adicione a nova instância desta classe como uma extensão a um host de serviço de fluxo de trabalho ou a uma instância de fluxo de trabalho. O exemplo de código a seguir mostra como ativar o cache de uma instância de fluxo de trabalho.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Para desativar completamente o cache para as fábricas de canais e os canais, desative o cache da fábrica do canal. Ao fazer isso, também desliga o cache do canal, pois os canais são de propriedade de suas fábricas de canais correspondentes. Para desativar o cache da `factorySettings` fábrica do <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> canal, passe o <xref:System.ServiceModel.Activities.ChannelCacheSettings> parâmetro <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> para o construtor inicializado para uma instância com um valor de 0. O exemplo de código a seguir mostra isso.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Você pode optar por usar apenas o cache de fábrica `channelSettings` do canal <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> e desativar o <xref:System.ServiceModel.Activities.ChannelCacheSettings> cache <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do canal passando o parâmetro para o construtor inicializado para uma instância com um valor de 0. O exemplo de código a seguir mostra isso.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Em um serviço hospedado de fluxo de trabalho, você pode especificar os cache e o canal cache configurações de fábrica no arquivo de configuração do aplicativo. Para fazer isso, adicionar um comportamento de serviço que contém as configurações de cache para cache de fábrica e o canal e adicionar esse comportamento de serviço ao seu serviço. O exemplo a seguir mostra o conteúdo `MyChannelCacheBehavior` de um arquivo de configuração que contém o comportamento do serviço com as configurações personalizadas de cache de fábrica e cache de canal. Esse comportamento de serviço é `behaviorConfiguration` adicionado ao serviço através do atributo.  
  
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
