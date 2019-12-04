---
title: Pools
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: d2962004376cf6f0752067d4e03828cd894efd01
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716510"
---
# <a name="pooling"></a>Pools
Este exemplo demonstra como estender Windows Communication Foundation (WCF) para dar suporte ao pooling de objetos. O exemplo demonstra como criar um atributo que seja sintaticamente e semanticamente semelhante à funcionalidade de atributo `ObjectPoolingAttribute` dos serviços corporativos. O pooling de objetos pode fornecer um aumento considerável para o desempenho de um aplicativo. No entanto, ele pode ter o efeito oposto se não for usado corretamente. O pooling de objetos ajuda a reduzir a sobrecarga de recriação de objetos usados com frequência que exigem inicialização extensiva. No entanto, se uma chamada para um método em um objeto em pool levar um tempo considerável para ser concluída, o pooling de objetos enfileirará solicitações adicionais assim que o tamanho máximo do pool for atingido. Portanto, ele pode falhar ao fornecer algumas solicitações de criação de objeto lançando uma exceção de tempo limite.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 A primeira etapa na criação de uma extensão WCF é decidir o ponto de extensibilidade a ser usado.  
  
 No WCF, o termo *Dispatcher* refere-se a um componente de tempo de execução responsável pela conversão de mensagens de entrada em invocações de método no serviço do usuário e pela conversão de valores de retorno desse método em uma mensagem de saída. Um serviço WCF cria um Dispatcher para cada ponto de extremidade. Um cliente WCF deve usar um Dispatcher se o contrato associado a esse cliente for um contrato duplex.  
  
 Os despachantes de canal e ponto de extremidade oferecem extensibilidade de canal e de todo o contrato expondo várias propriedades que controlam o comportamento do Dispatcher. A propriedade <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> também permite que você inspecione, modifique ou personalize o processo de expedição. Este exemplo se concentra na propriedade <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> que aponta para o objeto que fornece as instâncias da classe de serviço.  
  
## <a name="the-iinstanceprovider"></a>O IInstanceProvider  
 No WCF, o Dispatcher cria instâncias da classe de serviço usando um <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, que implementa a interface <xref:System.ServiceModel.Dispatcher.IInstanceProvider>. Essa interface tem três métodos:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: quando uma mensagem chega ao dispatcher chama o método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> para criar uma instância da classe de serviço para processar a mensagem. A frequência das chamadas para esse método é determinada pela propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Por exemplo, se a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> for definida como <xref:System.ServiceModel.InstanceContextMode.PerCall> uma nova instância da classe de serviço será criada para processar cada mensagem que chega, de modo que <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> será chamado sempre que uma mensagem chegar.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: isso é idêntico ao método anterior, exceto que isso é invocado quando não há nenhum argumento de mensagem.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: quando o tempo de vida de uma instância de serviço tiver decorrido, o Dispatcher chamará o método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>. Assim como no método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, a frequência das chamadas para esse método é determinada pela propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>O pool de objetos  
 Uma implementação de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> personalizada fornece a semântica de pool de objetos necessária para um serviço. Portanto, esse exemplo tem um tipo de `ObjectPoolingInstanceProvider` que fornece implementação personalizada de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> para pooling. Quando o `Dispatcher` chama o método <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool na memória. Se houver um disponível, ele será retornado. Caso contrário, um novo objeto será criado. A implementação para `GetInstance` é mostrada no código de exemplo a seguir.  
  
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
  
 A implementação de `ReleaseInstance` personalizada adiciona a instância liberada de volta ao pool e decrementa o valor de `ActiveObjectsCount`. O `Dispatcher` pode chamar esses métodos de threads diferentes e, portanto, o acesso sincronizado aos membros de nível de classe na classe `ObjectPoolingInstanceProvider` é necessário.  
  
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
  
 O método `ReleaseInstance` fornece um recurso de "inicialização de limpeza". Normalmente, o pool mantém um número mínimo de objetos durante o tempo de vida do pool. No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para alcançar o limite máximo especificado na configuração. Eventualmente, quando o pool se torna menos ativo, esses objetos excedentes podem se tornar uma sobrecarga extra. Portanto, quando o `activeObjectsCount` chega a zero, um temporizador ocioso é iniciado que dispara e executa um ciclo de limpeza.  
  
## <a name="adding-the-behavior"></a>Adicionando o comportamento  
 As extensões de camada de Dispatcher são conectadas usando os seguintes comportamentos:  
  
- Comportamentos de serviço. Elas permitem a personalização de todo o tempo de execução do serviço.  
  
- Comportamentos de ponto de extremidade. Eles permitem a personalização de pontos de extremidade de serviço, especificamente um Dispatcher de canal e de ponto final.  
  
- Comportamentos de contrato. Eles permitem a personalização das classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> no cliente e no serviço, respectivamente.  
  
 Para a finalidade de uma extensão de pool de objetos, um comportamento de serviço deve ser criado. Os comportamentos de serviço são criados com a implementação da interface <xref:System.ServiceModel.Description.IServiceBehavior>. Há várias maneiras de fazer com que o modelo de serviço reconheça os comportamentos personalizados:  
  
- Usando um atributo personalizado.  
  
- Adicionando imperativamente à coleção de comportamentos da descrição do serviço.  
  
- Estendendo o arquivo de configuração.  
  
 Este exemplo usa um atributo personalizado. Quando o <xref:System.ServiceModel.ServiceHost> é construído, ele examina os atributos usados na definição de tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.  
  
 A interface <xref:System.ServiceModel.Description.IServiceBehavior> tem três métodos, <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. O método <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> é usado para garantir que o comportamento possa ser aplicado ao serviço. Neste exemplo, a implementação garante que o serviço não esteja configurado com <xref:System.ServiceModel.InstanceContextMode.Single>. O método <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> é usado para configurar as associações do serviço. Isso não é necessário neste cenário. O <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> é usado para configurar os expedidores do serviço. Esse método é chamado pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado. Os parâmetros a seguir são passados para este método:  
  
- `Description`: esse argumento fornece a descrição do serviço para todo o serviço. Isso pode ser usado para inspecionar dados de descrição sobre os pontos de extremidade, contratos, associações e outros dados do serviço.  
  
- `ServiceHostBase`: esse argumento fornece a <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializada no momento.  
  
 Na implementação de <xref:System.ServiceModel.Description.IServiceBehavior> personalizada, uma nova instância do `ObjectPoolingInstanceProvider` é instanciada e atribuída à propriedade <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> em cada <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na ServiceHostBase.  
  
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
  
 Além de uma implementação de <xref:System.ServiceModel.Description.IServiceBehavior>, a classe <xref:System.EnterpriseServices.ObjectPoolingAttribute> tem vários membros para personalizar o pool de objetos usando os argumentos de atributo. Esses membros incluem <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>e <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>para corresponder ao conjunto de recursos do pool de objetos fornecido pelo .NET Enterprise Services.  
  
 O comportamento do pool de objetos agora pode ser adicionado a um serviço WCF anotando a implementação do serviço com o atributo de `ObjectPooling` personalizado recém-criado.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 O exemplo demonstra os benefícios de desempenho que podem ser obtidos usando o pool de objetos em determinados cenários.  
  
 O aplicativo de serviço implementa dois serviços – `WorkService` e `ObjectPooledWorkService`. Ambos os serviços compartilham a mesma implementação – eles exigem uma inicialização cara e expõem um método de `DoWork()` relativamente barato. A única diferença é que o `ObjectPooledWorkService` tem o pool de objetos configurado:  
  
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
  
 Quando você executa o cliente, ele se esgota ao chamar o `WorkService` 5 vezes. Em seguida, as vezes chamam o `ObjectPooledWorkService` 5 vezes. A diferença no tempo é exibida:  
  
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
> Na primeira vez em que o cliente é executado, ambos os serviços parecem levar aproximadamente na mesma quantidade de tempo. Se você executar novamente o exemplo, poderá ver que o `ObjectPooledWorkService` retorna muito mais rápido porque já existe uma instância desse objeto no pool.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Se você usar svcutil. exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
