---
title: Contexto de instância durável
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 40af70c69438fc5eaa688963db6710fa6fde0a42
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425552"
---
# <a name="durable-instance-context"></a>Contexto de instância durável

Este exemplo demonstra como personalizar o tempo de execução do Windows Communication Foundation (WCF) para permitir que os contextos de instância durável. Ele usa o SQL Server 2005 como seu armazenamento de backup (SQL Server 2005 Express neste caso). No entanto, ele também fornece uma maneira de acessar os mecanismos de armazenamento personalizado.

> [!NOTE]
> As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

Este exemplo envolve estendendo a camada de canais e camada de modelo de serviço do WCF. Portanto é necessário entender os conceitos subjacentes antes de entrar em detalhes de implementação.

Contextos de instância durável frequentemente podem ser encontrados nos cenários do mundo real. Um aplicativo de carrinho de compras, por exemplo, tem a capacidade de pausar na metade de compras por meio e continuá-lo em outro dia. Para que quando estamos visita o carrinho de compras no dia seguinte, o nosso contexto original será restaurado. É importante observar que o aplicativo de carrinho de compras (no servidor) não mantém a instância de carrinho de compras enquanto estamos estão desconectados. Em vez disso, ele persiste seu estado em uma mídia de armazenamento durável e usa-o ao construir uma nova instância para o contexto restaurado. Portanto a instância de serviço pode de serviço para o mesmo contexto não é o mesmo que a instância anterior (ou seja, ele não tem o mesmo endereço de memória).

Contexto de instância durável é possibilitado por um protocolo pequeno que uma ID de contexto entre o cliente e o serviço de troca. Essa ID de contexto é criado no cliente e transmitida ao serviço. Quando a instância do serviço é criada, o tempo de execução do serviço tenta carregar o estado persistente que corresponde a essa ID de contexto de um armazenamento persistente (por padrão é um banco de dados do SQL Server 2005). Se nenhum estado está disponível a nova instância tem seu estado padrão. A implementação de serviço usa um atributo personalizado para marcar as operações que alteram o estado da implementação do serviço para que o tempo de execução pode salvar a instância de serviço depois de chamá-las.

Por descrição anterior, duas etapas sejam facilmente diferenciáveis para atingir a meta:

1. Alterar a mensagem que vai durante a transmissão para transportar o ID de contexto.

2. Altere o comportamento de local de serviço para implementar uma lógica personalizada de instanciação.

Como o primeiro na lista afeta as mensagens durante a transmissão, ele deve ser implementado como um canal personalizado e ser vinculado a camada do canal. A última opção só afeta o comportamento de serviço local e, portanto, pode ser implementado ao estender a vários pontos de extensibilidade do serviço. As próximas seções, cada uma dessas extensões são discutidos.

## <a name="durable-instancecontext-channel"></a>Canal de InstanceContext duráveis

A primeira coisa a observar é uma extensão de camada do canal. A primeira etapa ao escrever um canal personalizado é decidir a estrutura de comunicação do canal. Como um novo protocolo de transmissão está sendo introduzido o canal deve funcionar com praticamente qualquer outro canal na pilha de canais. Portanto, ele deve dar suporte a todos os padrões de troca de mensagem. No entanto, a funcionalidade básica do canal é o mesmo, independentemente de sua estrutura de comunicação. Mais especificamente, do cliente, ele deve gravar a ID de contexto às mensagens e do serviço deve ler esta ID de contexto de mensagens e passá-lo para os níveis superiores. Por causa disso, um `DurableInstanceContextChannelBase` classe é criada que atua como a classe base abstrata para todas as implementações de canal de contexto de instância durável. Essa classe contém as funções comuns de gerenciamento de máquina de estado e dois membros protegidos para aplicar e ler as informações de contexto para e de mensagens.

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

Esses dois métodos fazem uso de `IContextManager` implementações para gravar e ler a ID de contexto da mensagem. (`IContextManager` é uma interface personalizada usada para definir o contrato para todos os gerenciadores de contexto.) O canal pode incluir a ID de contexto em um cabeçalho SOAP personalizado ou em um cabeçalho de cookie HTTP. Cada implementação do Gerenciador de contexto herda a `ContextManagerBase` classe que contém a funcionalidade comum para todos os gerenciadores de contexto. O `GetContextId` método nessa classe é usado para se originar a ID do contexto do cliente. Quando um contexto de que ID é originada pela primeira vez, esse método salva em um arquivo de texto cujo nome é criado pelo endereço do ponto de extremidade remoto (os caracteres de nome de arquivo inválido nos URIs típicos são substituídos com @ caracteres).

Mais tarde quando a ID de contexto é necessária para o mesmo ponto de extremidade remoto, ele verifica se existe um arquivo apropriado. Em caso afirmativo, ele lê a ID de contexto e o retorna. Caso contrário, ele retorna uma ID de contexto recém-gerado e salva-o em um arquivo. Com a configuração padrão, esses arquivos são colocados em um diretório chamado ContextStore, que reside no diretório temporário do usuário atual. No entanto, esse local é configurável usando o elemento de associação.

O mecanismo usado para a ID do contexto de transporte é configurável. Isso poderia ser escrito tanto para o cabeçalho de cookie HTTP ou um cabeçalho SOAP personalizado. A abordagem de cabeçalho SOAP personalizada torna possível usar esse protocolo com protocolos não HTTP (por exemplo, TCP ou Pipes nomeados). Há duas classes, ou seja, `MessageHeaderContextManager` e `HttpCookieContextManager`, que implementam essas duas opções.

Os dois gravam a ID de contexto na mensagem adequadamente. Por exemplo, o `MessageHeaderContextManager` classe grava-o em um cabeçalho SOAP no `WriteContext` método.

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

Tanto a `ApplyContext` e `ReadContextId` métodos na `DurableInstanceContextChannelBase` classe chamar o `IContextManager.ReadContext` e `IContextManager.WriteContext`, respectivamente. No entanto, esses gerenciadores de contexto não são diretamente criadas pelo `DurableInstanceContextChannelBase` classe. Em vez disso, ele usa o `ContextManagerFactory` classe para fazer esse trabalho.

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

O `ApplyContext` método é invocado por canais de envio. Ele injeta a ID de contexto para as mensagens de saída. O `ReadContextId` método é invocado por canais de recebimento. Esse método garante que a ID de contexto está disponível nas mensagens recebidas e adiciona-o para o `Properties` coleção do `Message` classe. Ele também gera um `CommunicationException` em caso de falha ao ler a ID de contexto e, portanto, faz com que o canal a ser anulada.

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

Antes de continuar, é importante entender o uso do `Properties` coleta no `Message` classe. Normalmente, esse `Properties` coleção é usada quando passando dados para baixo para os níveis superiores da camada de canal. Dessa forma os dados desejados podem ser fornecidos para os níveis superiores de maneira consistente, independentemente dos detalhes de protocolo. Em outras palavras, a camada de canais pode enviar e receber a ID de contexto como um cabeçalho SOAP ou um cabeçalho de cookie HTTP. Mas não é necessário para conhecer esses detalhes como a camada de canal torna essas informações disponíveis em níveis superiores a `Properties` coleção.

Agora com o `DurableInstanceContextChannelBase` classe in-loco, os dez as interfaces necessárias (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) deve ser implementada. Eles se parecer com cada padrão de troca de mensagens disponíveis (datagrama simplex, duplex e suas variantes de sessão). Cada uma dessas implementações herdam a classe base descritos anteriormente e chama `ApplyContext` e `ReadContextId` adequadamente. Por exemplo, `DurableInstanceContextOutputChannel` - que implementa a interface IOutputChannel - chama o `ApplyContext` método de cada método que envia as mensagens.

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

Por outro lado, `DurableInstanceContextInputChannel` -que implementa o `IInputChannel` interface - chamadas a `ReadContextId` método em cada método que recebe as mensagens.

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

Além disso, essas implementações de canal delegam invocações de método para o canal abaixo na pilha de canais. No entanto, as variantes de sessão têm uma lógica básica para certificar-se de que a ID de contexto é enviada e é lido apenas para a primeira mensagem que faz com que a sessão a ser criado.

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

Essas implementações de canal, em seguida, são adicionadas ao tempo de execução de canal WCF pela `DurableInstanceContextBindingElement` classe e `DurableInstanceContextBindingElementSection` classe adequadamente. Consulte a [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) documentação de exemplo para obter mais detalhes sobre os elementos de associação e seções de elementos de associação de canal.

## <a name="service-model-layer-extensions"></a>Extensões de camada de modelo de serviço

Agora que a ID de contexto tem percorrida por meio da camada de canal, o comportamento de serviço pode ser implementado para personalizar a instanciação. Neste exemplo, um Gerenciador de armazenamento é usado para carregar e salvar o estado de ou para o armazenamento persistente. Conforme explicado anteriormente, este exemplo fornece um Gerenciador de armazenamento que usa o SQL Server 2005 como seu armazenamento de backup. No entanto, também é possível adicionar os mecanismos de armazenamento personalizado para essa extensão. Para fazer isso em uma interface pública é declarado, que deve ser implementado por todos os gerenciadores de armazenamento.

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

O `SqlServerStorageManager` classe contém o padrão `IStorageManager` implementação. No seu `SaveInstance` método determinado objeto é serializado usando XmlSerializer e é salvo no banco de dados do SQL Server.

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

No `GetInstance` método os dados serializados é lido para uma ID de contexto fornecido e o objeto construído a partir dele é retornado ao chamador.

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

Usuários desses gerenciadores de não deveria ser instanciá-las diretamente de armazenamento. Eles usam o `StorageManagerFactory` classe, que abstrai dos detalhes de criação do Gerenciador de armazenamento. Essa classe tem um membro estático, `GetStorageManager`, que cria uma instância de um tipo de Gerenciador de armazenamento específica. Se o parâmetro de tipo é `null`, esse método cria uma instância padrão do `SqlServerStorageManager` de classe e o retorna. Ele também valida o tipo fornecido para certificar-se de que ele implementa o `IStorageManager` interface.

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

A infraestrutura necessária para ler e gravar as instâncias do armazenamento persistente é implementada. Agora, as etapas necessárias para alterar o comportamento de serviço precisam ser retirados.

Como a primeira etapa desse processo, precisamos salvar a ID de contexto, o que vem por meio da camada de canais para o InstanceContext atual. InstanceContext é um componente de tempo de execução que atua como o link entre o dispatcher do WCF e a instância do serviço. Ele pode ser usado para fornecer o estado adicional e o comportamento para a instância do serviço. Isso é essencial porque na comunicação de sessão, a ID de contexto é enviada somente com a primeira mensagem.

O WCF permite que estender seu componente de tempo de execução InstanceContext adicionando um novo estado e comportamento usando o padrão de objeto extensível. O padrão de objeto extensível é usado no WCF para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado para um objeto. Existem três interfaces no padrão de objeto extensível - IExtensibleObject\<T >, IExtension\<T > e IExtensionCollection\<T >:

- O IExtensibleObject\<T > interface é implementada por objetos que permitem que as extensões que personalizar sua funcionalidade.

- O IExtension\<T > interface é implementada por objetos que são extensões de classes do tipo T.

- O IExtensionCollection\<T > interface é uma coleção de IExtensions que permite recuperar IExtensions por tipo.

Portanto, uma classe InstanceContextExtension deve ser criada que implementa a interface de IExtension e define o estado necessário para salvar a ID de contexto. Essa classe também fornece o estado para manter o armazenamento manager que está sendo usado. Depois que o novo estado é salvo, ele não deve ser possível modificá-lo. Portanto, o estado é fornecido e salvo na instância no momento em que ele está sendo construído e, em seguida, só pode ser acessado usando propriedades somente leitura.

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

A classe InstanceContextInitializer implementa a interface IInstanceContextInitializer e adiciona a extensão de contexto de instância para a coleção de extensões do InstanceContext que está sendo construído.

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

Conforme descrito anteriormente a ID de contexto é lido a partir de `Properties` coleção do `Message` de classe e passado para o construtor da classe de extensão. Isso demonstra como as informações podem ser trocadas entre as camadas de maneira consistente.

A próxima etapa importante está substituindo o processo de criação de instância de serviço. WCF permite que a implementação de comportamentos personalizados de instanciação e vinculando-os até o tempo de execução usando a interface IInstanceProvider. O novo `InstanceProvider` classe é implementada para fazer esse trabalho. No construtor, o tipo de serviço esperado do provedor de instância é aceito. Posteriormente, isso é usado para criar novas instâncias. No `GetInstance` implementação de uma instância de um Gerenciador de armazenamento é criada procurando por uma instância persistida. Se ele retornar `null` uma nova instância do tipo de serviço será instanciada e retornada ao chamador.

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    if (instance == null)
    {
        instance = Activator.CreateInstance(serviceType);
    }

    return instance;
}
```

A próxima etapa importante é instalar o `InstanceContextExtension`, `InstanceContextInitializer` e `InstanceProvider` classes no tempo de execução de modelo de serviço. Um atributo personalizado pode ser usado para marcar as classes de implementação de serviço para o comportamento da instalação. O `DurableInstanceContextAttribute` contém a implementação para esse atributo e implementa o `IServiceBehavior` interface para estender o tempo de execução de todo o serviço.

Essa classe tem uma propriedade que aceita o tipo do Gerenciador de armazenamento a ser usado. Dessa forma, a implementação permite que os usuários especifiquem suas próprias `IStorageManager` implementação como parâmetro desse atributo.

No `ApplyDispatchBehavior` implementação de `InstanceContextMode` atual `ServiceBehavior` atributo está sendo verificado. Se essa propriedade é definida como Singleton, permitindo a criação de instância durável não é possível e um `InvalidOperationException` é gerada para notificar o host.

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

Depois das instâncias do Gerenciador de armazenamento, o inicializador de contexto de instância e o provedor de instância são criadas e instaladas no `DispatchRuntime` criado para cada ponto de extremidade.

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

Em resumo até agora, este exemplo produz um canal que habilitado o protocolo de transmissão personalizado para o exchange de ID de contexto personalizado e ele também substitui o padrão de comportamento para carregar as instâncias do armazenamento persistente de instâncias.

O que resta é uma maneira de salvar a instância de serviço para o armazenamento persistente. Conforme discutido anteriormente, já existe a funcionalidade necessária para salvar o estado em um `IStorageManager` implementação. Vamos agora deve se integrar isso o tempo de execução do WCF. Outro atributo é necessário que seja aplicável para os métodos na classe de implementação de serviço. Esse atributo deve ser aplicado aos métodos que alteram o estado da instância do serviço.

O `SaveStateAttribute` classe implementa essa funcionalidade. Ele também implementa `IOperationBehavior` classe para modificar o tempo de execução do WCF para cada operação. Quando um método é marcado com esse atributo, o tempo de execução do WCF chama o `ApplyBehavior` método enquanto apropriado `DispatchOperation` está sendo construído. Nessa implementação de método há uma única linha de código:

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

Essa instrução cria uma instância de `OperationInvoker` de tipo e a atribui a `Invoker` propriedade do `DispatchOperation` que está sendo construído. O `OperationInvoker` classe é um wrapper para o chamador de operação padrão criado para o `DispatchOperation`. Essa classe implementa o `IOperationInvoker` interface. No `Invoke` implementação do método de invocação do método real é delegada para o chamador da operação interna. No entanto, antes de retornar os resultados no Gerenciador de armazenamento no `InstanceContext` é usado para salvar a instância de serviço.

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a>Usando a extensão

A camada de canais e extensões de camada de modelo de serviço são feitas tanto eles agora podem ser usados em aplicativos do WCF. Serviços têm que adicionar o canal à pilha de canal usando uma ligação personalizada e, em seguida, marcar as classes de implementação de serviço com os atributos apropriados.

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

Aplicativos cliente devem adicionar o DurableInstanceContextChannel à pilha de canal usando uma associação personalizada. Para configurar o canal de forma declarativa no arquivo de configuração, a seção do elemento de associação deve ser adicionado à coleção de extensões de elemento de associação.

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
```

Agora, o elemento de associação pode ser usado com uma ligação personalizada, assim como outros elementos de associação padrão:

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a>Conclusão

Este exemplo mostrou como criar um canal de protocolo personalizado e como personalizar o comportamento de serviço para habilitá-lo.

A extensão pode ser aprimorada ainda mais, permitindo que os usuários especificam o `IStorageManager` implementação usando uma seção de configuração. Isso torna possível modificar o repositório de backup sem recompilar o código de serviço.

Além disso, você pode tentar implementar uma classe (por exemplo, `StateBag`), que encapsula o estado da instância. Essa classe é responsável por manter o estado sempre que ele é alterado. Dessa forma, você pode evitar o uso de `SaveState` de atributos e executar o trabalho de persistência com mais precisão (por exemplo, você pode persistir o estado quando o estado é alterado, na verdade, em vez de salvá-lo cada vez que quando um método com o `SaveState` atributo é chamado).

Quando você executar o exemplo, a seguinte saída é exibida. O cliente adiciona dois itens ao seu carrinho de compras e, em seguida, obtém a lista de itens em seu carrinho de compras do serviço. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.

```
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> Recriar o serviço substituirá o arquivo de banco de dados. Para observar o estado preservado entre várias execuções do exemplo, não se esqueça de não recompilar o exemplo entre as execuções.

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!NOTE]
> Você deve estar executando o SQL Server 2005 ou SQL Express 2005 para executar este exemplo. Se você estiver executando o SQL Server 2005, você deve modificar a configuração de cadeia de caracteres de conexão do serviço. Ao executar várias máquinas, o SQL Server é necessário apenas na máquina do servidor.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
