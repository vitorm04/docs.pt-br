---
title: Agrupamento
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183398"
---
# <a name="pooling"></a>Agrupamento
Esta amostra demonstra como estender o Windows Communication Foundation (WCF) para suportar o pool de objetos. A amostra demonstra como criar um atributo que seja sintática `ObjectPoolingAttribute` e semanticamente semelhante à funcionalidade de atributo dos Serviços Corporativos. O pool de objetos pode fornecer um impulso dramático ao desempenho de um aplicativo. No entanto, pode ter o efeito oposto se não for usado corretamente. O agrupamento de objetos ajuda a reduzir a sobrecarga de recriar objetos usados com freqüência que requerem uma inicialização extensiva. No entanto, se uma chamada para um método em um objeto agrupado levar um tempo considerável para ser concluída, o pool de objetos faz filas adicionais assim que o tamanho máximo da piscina for atingido. Assim, ele pode não atender a algumas solicitações de criação de objetos, lançando uma exceção de tempo.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O primeiro passo para criar uma extensão do WCF é decidir o ponto de extensibilidade a ser usado.  
  
 No WCF, o *despachante* de termo refere-se a um componente de tempo de execução responsável pela conversão de mensagens recebidas em invocações de método no serviço do usuário e por converter valores de retorno desse método para uma mensagem de saída. Um serviço WCF cria um despachante para cada ponto final. Um cliente WCF deve usar um despachante se o contrato associado a esse cliente for um contrato duplex.  
  
 Os despachantes de canais e pontos finais oferecem extensibilidade de canal e contrato, expondo várias propriedades que controlam o comportamento do despachante. A <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> propriedade também permite que você inspecione, modifique ou personalize o processo de expedição. Esta amostra se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> concentra na propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.  
  
## <a name="the-iinstanceprovider"></a>O provedor de iinstance  
 No WCF, o despachante cria <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>instâncias da <xref:System.ServiceModel.Dispatcher.IInstanceProvider> classe de serviço usando a , que implementa a interface. Esta interface tem três métodos:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Quando uma mensagem chega, o Despachante chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método para criar uma instância da classe de serviço para processar a mensagem. A frequência das chamadas para este <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> método é determinada pela propriedade. Por exemplo, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> se a <xref:System.ServiceModel.InstanceContextMode.PerCall> propriedade for definida como uma nova instância de classe <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> de serviço é criada para processar cada mensagem que chega, assim é chamada sempre que uma mensagem chega.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Este é idêntico ao método anterior, exceto que este é invocado quando não há argumento de mensagem.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Quando a vida útil de uma instância de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> serviço é decorrido, o Despachante chama o método. Assim como <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> para o método, a frequência das chamadas <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> para este método é determinada pela propriedade.  
  
## <a name="the-object-pool"></a>O Pool de Objetos  
 Uma <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação personalizada fornece a semântica de pool de objetos necessária para um serviço. Portanto, esta amostra `ObjectPoolingInstanceProvider` tem um tipo <xref:System.ServiceModel.Dispatcher.IInstanceProvider> que fornece implementação personalizada para pooling. Quando `Dispatcher` o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método chama, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória. Se um estiver disponível, é devolvido. Caso contrário, um novo objeto é criado. A implementação `GetInstance` é mostrada no seguinte código de amostra.  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 A `ReleaseInstance` implementação personalizada adiciona a instância liberada de `ActiveObjectsCount` volta ao pool e decreta o valor. É `Dispatcher` necessário chamar esses métodos de diferentes segmentos e, portanto, `ObjectPoolingInstanceProvider` é necessário acesso sincronizado aos membros do nível de classe na classe.  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 O `ReleaseInstance` método fornece um recurso de "limpeza inicialização". Normalmente, a piscina mantém um número mínimo de objetos durante a vida útil da piscina. No entanto, pode haver períodos de uso excessivo que requerem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração. Eventualmente, quando a piscina se torna menos ativa, esses objetos excedentes podem se tornar uma sobrecarga extra. Portanto, quando `activeObjectsCount` o tempo chega a zero, é iniciado um temporizador ocioso que aciona e realiza um ciclo de limpeza.  
  
## <a name="adding-the-behavior"></a>Adicionando o Comportamento  
 As extensões da camada do despachante são ligadas usando os seguintes comportamentos:  
  
- Comportamentos de serviço. Isso permite a personalização de todo o tempo de execução do serviço.  
  
- Comportamentos de ponto final. Estes permitem a personalização de pontos finais de serviço, especificamente um Despachante de Canais e Endpoint.  
  
- Comportamentos contratuais. Estes permitem a personalização de ambos <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes sobre o cliente e o serviço, respectivamente.  
  
 Para efeitos de uma extensão de agrupamento de objetos, um comportamento de serviço deve ser criado. Os comportamentos de serviço são <xref:System.ServiceModel.Description.IServiceBehavior> criados implementando a interface. Existem várias maneiras de conscientizar o modelo de serviço sobre os comportamentos personalizados:  
  
- Usando um atributo personalizado.  
  
- Adicioná-lo imperativamente à coleção de comportamentos da descrição do serviço.  
  
- Estendendo o arquivo de configuração.  
  
 Esta amostra usa um atributo personalizado. Quando <xref:System.ServiceModel.ServiceHost> o é construído, examina os atributos utilizados na definição do tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.  
  
 A <xref:System.ServiceModel.Description.IServiceBehavior> interface tem três métodos <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>nele <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>e. O <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> método é usado para garantir que o comportamento possa ser aplicado ao serviço. Nesta amostra, a implementação garante que o <xref:System.ServiceModel.InstanceContextMode.Single>serviço não esteja configurado com . O <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> método é usado para configurar as vinculações do serviço. Não é necessário neste cenário. O <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> é usado para configurar os despachantes do serviço. Este método é chamado pelo <xref:System.ServiceModel.ServiceHost> WCF quando o está sendo inicializado. Os seguintes parâmetros são passados para este método:  
  
- `Description`: Este argumento fornece a descrição do serviço para todo o serviço. Isso pode ser usado para inspecionar dados de descrição sobre os pontos finais do serviço, contratos, vinculações e outros dados.  
  
- `ServiceHostBase`: Este argumento <xref:System.ServiceModel.ServiceHostBase> fornece o que está sendo inicializado.  
  
 Na implementação <xref:System.ServiceModel.Description.IServiceBehavior> personalizada, `ObjectPoolingInstanceProvider` uma nova instância é instanciada e atribuída à <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada uma <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na ServiceHostBase.  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 Além de <xref:System.ServiceModel.Description.IServiceBehavior> uma <xref:System.EnterpriseServices.ObjectPoolingAttribute> implementação, a classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo. Esses membros <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>incluem <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, e , para corresponder ao conjunto de recursos de pooling de objetos fornecido pelo .NET Enterprise Services.  
  
 O comportamento de pooling de objetos agora pode ser adicionado a um serviço `ObjectPooling` WCF anotando a implementação do serviço com o atributo personalizado recém-criado.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 A amostra demonstra os benefícios de desempenho que podem ser obtidos usando o agrupamento de objetos em determinados cenários.  
  
 O aplicativo de serviço implementa dois serviços -- `WorkService` e `ObjectPooledWorkService`. Ambos os serviços compartilham a mesma implementação -- `DoWork()` ambos exigem inicialização cara e, em seguida, expõem um método que é relativamente barato. A única diferença `ObjectPooledWorkService` é que o pool de objetos está configurado:  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 Quando você executa o cliente, ele vezes liga ndo as `WorkService` 5 vezes. Em seguida, `ObjectPooledWorkService` vezes liga ndo as 5 vezes. A diferença de tempo é então exibida:  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> A primeira vez que o cliente é executado ambos os serviços parecem levar cerca da mesma quantidade de tempo. Se você reexecutar a amostra, você `ObjectPooledWorkService` pode ver que o retorno muito mais rápido porque uma instância desse objeto já existe na piscina.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
