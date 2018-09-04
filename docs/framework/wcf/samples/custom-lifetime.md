---
title: Tempo de vida personalizado
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1946608c69401fb08f6eb458a8adabea24563963
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520765"
---
# <a name="custom-lifetime"></a>Tempo de vida personalizado

Este exemplo demonstra como escrever uma extensão do Windows Communication Foundation (WCF) para fornecer serviços de tempo de vida personalizado para instâncias de serviço compartilhados do WCF.

> [!NOTE]
> As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste artigo.

## <a name="shared-instancing"></a>Compartilhado de instanciação

O WCF oferece vários modos de instanciação para suas instâncias de serviço. O modo de instanciação compartilhado abordado neste artigo fornece uma maneira de compartilhar uma instância de serviço entre os vários canais. Os clientes possam entre em contato com um método de fábrica no serviço e criar um novo canal para iniciar a comunicação. O trecho de código a seguir mostra como um aplicativo cliente cria um novo canal para uma instância de serviço existente:

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

Ao contrário de outros modos de instanciação, o modo de instanciação compartilhado tem uma maneira exclusiva de liberar as instâncias de serviço. Por padrão, quando todos os canais são fechados para um <xref:System.ServiceModel.InstanceContext>, o tempo de execução do serviço WCF verifica se o serviço <xref:System.ServiceModel.InstanceContextMode> é configurado para <xref:System.ServiceModel.InstanceContextMode.PerCall> ou <xref:System.ServiceModel.InstanceContextMode.PerSession>e se então libera a instância e os recursos de declarações. Se um personalizado <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> está sendo usado, o WCF chama o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método da implementação do provedor antes de liberar a instância. Se <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> retorna `true` a instância é liberada, caso contrário, o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação é responsável por notificar a `Dispatcher` do estado ocioso, usando um método de retorno de chamada. Isso é feito chamando o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método do provedor.

Este exemplo demonstra como você pode atrasar a liberar o <xref:System.ServiceModel.InstanceContext> com um tempo limite de ociosidade de 20 segundos.

## <a name="extending-the-instancecontext"></a>Estendendo o InstanceContext

No WCF, <xref:System.ServiceModel.InstanceContext> é o vínculo entre a instância de serviço e o `Dispatcher`. O WCF permite que você estenda este componente de tempo de execução, adicionando o novo estado ou comportamento por meio de seu padrão de objeto extensível. O padrão de objeto extensível é usado no WCF para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado para um objeto. Existem três interfaces no padrão de objeto extensível: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, e <xref:System.ServiceModel.IExtensionCollection%601>.

O <xref:System.ServiceModel.IExtensibleObject%601> interface é implementada por objetos para permitir que as extensões que personalizar sua funcionalidade.

O <xref:System.ServiceModel.IExtension%601> interface é implementada por objetos que podem ser extensões de classes do tipo `T`.

E, finalmente, o <xref:System.ServiceModel.IExtensionCollection%601> interface é uma coleção de <xref:System.ServiceModel.IExtension%601> implementações que permite a recuperação de uma implementação de <xref:System.ServiceModel.IExtension%601> por tipo.

Portanto, para estender a <xref:System.ServiceModel.InstanceContext>, você deve implementar o <xref:System.ServiceModel.IExtension%601> interface. Neste projeto de exemplo, o `CustomLeaseExtension` classe contém essa implementação.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

O <xref:System.ServiceModel.IExtension%601> interface tem dois métodos <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A>. Como seus nomes já dizem, esses dois métodos são chamados quando o tempo de execução anexa e Desanexa a extensão a uma instância da <xref:System.ServiceModel.InstanceContext> classe. Neste exemplo, o `Attach` método é usado para controlar o <xref:System.ServiceModel.InstanceContext> objeto ao qual pertence a instância atual da extensão.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Além disso, você deve adicionar a implementação necessária para a extensão para fornecer o suporte estendido do tempo de vida. Portanto, o `ICustomLease` interface é declarado com os métodos desejados e é implementado de `CustomLeaseExtension` classe.

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

Quando o WCF chama o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método na <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação, essa chamada for roteada para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método da `CustomLeaseExtension`. Em seguida, o `CustomLeaseExtension` verifica o estado particular para ver se o <xref:System.ServiceModel.InstanceContext> está ocioso. Se estiver ocioso, ele retorna `true`. Caso contrário, ele inicia um cronômetro para um determinado período de tempo de vida estendido.

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

Do timer `Elapsed` evento, a função de retorno de chamada no Dispatcher é chamada para iniciar outro ciclo de limpeza.

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

Não é possível renovar o temporizador em execução quando uma nova mensagem chega para a instância que está sendo movida para o estado ocioso.

A amostra implementa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> interceptar as chamadas para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método e a rota para o `CustomLeaseExtension`. O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação está contida no `CustomLifetimeLease` classe. O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método é invocado quando o WCF está prestes a liberar a instância do serviço. No entanto, há apenas uma instância de um determinado `ISharedSessionInstance` implementação no ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> coleção. Isso significa que não há nenhuma maneira de saber se o <xref:System.ServiceModel.InstanceContext> é fechada no momento em que o WCF verifica o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método. Portanto, este exemplo usa o thread de bloqueio para serializar as solicitações para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.

> [!IMPORTANT]
> Usando o bloqueio de thread não é uma abordagem recomendada porque a serialização pode afetar gravemente o desempenho do seu aplicativo.

Um campo de membro privado é usado na `CustomLifetimeLease` de classe para controlar o estado ocioso e é retornado pelo <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método. Cada vez que o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método é chamado, o `isIdle` campo é retornado e redefinido como `false`.  É essencial para definir esse valor como `false` para garantir que as chamadas de Dispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método.

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

Se o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> retorn `false`, o Dispatcher registra uma função de retorno de chamada usando o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método. Esse método recebe uma referência para o <xref:System.ServiceModel.InstanceContext> sendo lançada. Portanto, o código de exemplo pode consultar a `ICustomLease` digite a extensão e marque o `ICustomLease.IsIdle` propriedade no estado estendido.

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

Antes do `ICustomLease.IsIdle` propriedade estiver marcada, a propriedade de retorno de chamada precisa ser definido como isso é essencial para `CustomLeaseExtension` para notificar o Dispatcher quando ele se torna ocioso. Se `ICustomLease.IsIdle` retorna `true`, o `isIdle` membro privado é simplesmente definido `CustomLifetimeLease` para `true` e chama o método de retorno de chamada. Como o código mantém um bloqueio, outros threads não é possível alterar o valor desse membro privado. E na próxima vez em que o Dispatcher chama a <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, ele retorna `true` e permite que o Dispatcher liberar a instância.

Agora que as bases para a extensão personalizada for concluída, ele deve ser vinculada ao modelo de serviço. Para ligar os `CustomLeaseExtension` implementação para o <xref:System.ServiceModel.InstanceContext>, o WCF fornece o <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface para executar a inicialização de <xref:System.ServiceModel.InstanceContext>. No exemplo, o `CustomLeaseInitializer` classe implementa essa interface e adiciona uma instância do `CustomLeaseExtension` para o <xref:System.ServiceModel.InstanceContext.Extensions%2A> coleção da inicialização único método. Esse método é chamado pelo Dispatcher ao inicializar o <xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Por fim o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação é ligada ao modelo de serviço usando o <xref:System.ServiceModel.Description.IServiceBehavior> implementação. Essa implementação é colocada na `CustomLeaseTimeAttribute` classe e ele também deriva o `Attribute` classe para expor esse comportamento como um atributo base.

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

Esse comportamento pode ser adicionado a uma classe de serviço de exemplo, anotando-o com o `CustomLeaseTime` atributo.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Quando você executar o exemplo, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você executou o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](building-the-samples.md).

3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
