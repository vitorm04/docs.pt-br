---
title: Agrupamento
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 6554ec9c5eaefaf8c9e39d2a8d92982716cc18c5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="pooling"></a>Agrupamento
Este exemplo demonstra como estender o Windows Communication Foundation (WCF) para dar suporte a pool de objetos. O exemplo demonstra como criar um atributo que é sintaticamente e semanticamente semelhante do `ObjectPoolingAttribute` funcionalidade de serviços corporativos de atributo. Pool de objetos pode fornecer um aumento significativo no desempenho do aplicativo. No entanto, ele pode ter o efeito oposto, se ele não está sendo usado corretamente. Pool de objetos ajuda a reduzir a sobrecarga de recriar os objetos usados com frequência que requerem inicialização ampla. No entanto, se uma chamada para um método em um objeto de pool leva uma quantidade considerável de tempo para concluir, pool de objetos enfileira solicitações adicionais assim que o tamanho máximo do pool for atingido. Portanto, pode falhar atender solicitações de criação de um objeto lançando uma exceção de tempo limite.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A primeira etapa na criação de uma extensão do WCF é decidir o ponto de extensibilidade para usar.  
  
 No WCF o termo *dispatcher* refere-se a um componente de tempo de execução responsável pela conversão de mensagens de entrada em invocações do método no serviço do usuário e para converter valores de retorno de método em uma mensagem de saída. Um serviço WCF cria um dispatcher para cada ponto de extremidade. Um cliente WCF deve usar um distribuidor se o contrato associado com esse cliente é um contrato duplex.  
  
 Os distribuidores de canal e o ponto de extremidade oferecem canal- e extensibilidade de todo o contrato ao expor várias propriedades que controlam o comportamento do dispatcher. O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> propriedade também permite que você inspecione, modificar ou personalizar o processo de distribuição. Este exemplo enfoca o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.  
  
## <a name="the-iinstanceprovider"></a>O IInstanceProvider  
 No WCF, o dispatcher cria instâncias de classe de serviço usando um <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, que implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface. Essa interface possui três métodos:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Quando uma mensagem chega as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método para criar uma instância da classe de serviço para processar a mensagem. A frequência de chamadas a este método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade. Por exemplo, se o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> está definida como <xref:System.ServiceModel.InstanceContextMode.PerCall> uma nova instância da classe de serviço é criada para processar cada mensagem que chega, isso <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> é chamado sempre que uma mensagem chega.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Isso é idêntico ao método anterior, exceto que isso é invocado quando não há nenhum argumento de mensagem.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Quando decorrido o tempo de vida de uma instância serviço, as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> método. Assim como para o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método, a frequência de chamadas a este método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.  
  
## <a name="the-object-pool"></a>O Pool de objetos  
 Um personalizado <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação fornece o objeto necessário pooling semântica para um serviço. Portanto, este exemplo tem um `ObjectPoolingInstanceProvider` tipo que fornece uma implementação personalizada de <xref:System.ServiceModel.Dispatcher.IInstanceProvider> para o pool. Quando o `Dispatcher` chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória. Se houver um disponível, ele será retornado. Caso contrário, um novo objeto é criado. A implementação para `GetInstance` é mostrado no código de exemplo a seguir.  
  
```  
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
  
 Personalizado `ReleaseInstance` implementação adiciona a instância liberada para o pool e diminui o `ActiveObjectsCount` valor. O `Dispatcher` pode chamar esses métodos de diversos threads e sincronizado, portanto, o acesso a membros de nível de classe no `ObjectPoolingInstanceProvider` classe é necessária.  
  
```  
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
  
 O `ReleaseInstance` método fornece um recurso de "Limpar inicialização". Normalmente o pool mantém um número mínimo de objetos para o tempo de vida do pool. No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração. Finalmente, quando o pool se torna menos ativo, esses objetos excedentes podem se tornar uma sobrecarga extra. Portanto, quando o `activeObjectsCount` atingir zero, um timer de ociosidade é iniciado, gatilhos e executa um ciclo de limpeza.  
  
## <a name="adding-the-behavior"></a>Adicionando o comportamento  
 Extensões de camada do Dispatcher são conectadas usando os seguintes comportamentos:  
  
-   Comportamentos de serviço. Eles permitem a personalização do tempo de execução de todo o serviço.  
  
-   Comportamentos de ponto de extremidade. Isso permite a personalização de pontos de extremidade de serviço, especificamente um canal e o Dispatcher do ponto de extremidade.  
  
-   Comportamentos de contrato. Eles permitem a personalização de ambos <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes no cliente e o serviço, respectivamente.  
  
 Com a finalidade de um objeto de extensão do pool um comportamento de serviço deve ser criado. Comportamentos de serviço são criados com a implementação de <xref:System.ServiceModel.Description.IServiceBehavior> interface. Há várias maneiras de tornar o modelo de serviço com reconhecimento de comportamentos personalizados:  
  
-   Usando um atributo personalizado.  
  
-   Imperativa adicionado à coleção de comportamentos da descrição de serviço.  
  
-   Extensão do arquivo de configuração.  
  
 Este exemplo usa um atributo personalizado. Quando o <xref:System.ServiceModel.ServiceHost> é criado ele examina os atributos usados na definição de tipo de serviço e adiciona os comportamentos disponíveis para a coleção de comportamentos da descrição de serviço.  
  
 A interface <xref:System.ServiceModel.Description.IServiceBehavior> tem três métodos em-- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. O <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> método é usado para garantir que o comportamento pode ser aplicado ao serviço. Neste exemplo, a implementação garante que o serviço não está configurado com <xref:System.ServiceModel.InstanceContextMode.Single>. O <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> método é usado para configurar as ligações de serviço. Não é necessário neste cenário. O <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> é usado para configurar os distribuidores do serviço. Este método é chamado pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado. Os seguintes parâmetros são passados para este método:  
  
-   `Description`: Este argumento fornece a descrição do serviço para o serviço inteiro. Isso pode ser usado para inspecionar dados descrição sobre pontos de extremidade do serviço e outros dados, associações e contratos.  
  
-   `ServiceHostBase`: Este argumento fornece o <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializado.  
  
 Em personalizado <xref:System.ServiceModel.Description.IServiceBehavior> uma nova instância da implementação de `ObjectPoolingInstanceProvider` é criada e atribuída ao <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada <xref:System.ServiceModel.Dispatcher.DispatchRuntime> em ServiceHostBase.  
  
```  
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
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
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
  
 Além de um <xref:System.ServiceModel.Description.IServiceBehavior> implementação o <xref:System.EnterpriseServices.ObjectPoolingAttribute> classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo. Esses membros incluem <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, e <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, para coincidir com o conjunto de recursos fornecido pelo .NET Enterprise Services ao pool de objetos.  
  
 O comportamento de pooling de objeto pode ser adicionado a um serviço WCF, anotando a implementação do serviço com o recém-criado personalizado `ObjectPooling` atributo.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 O exemplo demonstra os benefícios de desempenho que podem ser obtidos usando o pool de objetos em determinados cenários.  
  
 O aplicativo de serviço implementa dois serviços – `WorkService` e `ObjectPooledWorkService`. Os serviços compartilham a mesma implementação – eles requerem inicialização cara tanto expõem um `DoWork()` método que é relativamente barato. A única diferença é que o `ObjectPooledWorkService` tem o pool de objetos configurados:  
  
```  
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
  
 Quando você executa o cliente, o tempo que chama o `WorkService` 5 vezes. Tempo, em seguida, chamar o `ObjectPooledWorkService` 5 vezes. A diferença de tempo, em seguida, é exibida:  
  
```  
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
>  Na primeira vez em que o cliente é executar ambos os serviços parecem levar aproximadamente a mesma quantidade de tempo. Se você executar novamente o exemplo, você pode ver que o `ObjectPooledWorkService` retorna muito mais rápida porque já existe uma instância desse objeto no pool.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a>Consulte também
