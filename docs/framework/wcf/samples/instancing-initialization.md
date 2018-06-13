---
title: Inicialização de instancialização
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ae01254760219f2b408ef9d9663c4158e2802be8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807916"
---
# <a name="instancing-initialization"></a>Inicialização de instancialização
Este exemplo estende o [Pooling](../../../../docs/framework/wcf/samples/pooling.md) exemplo definindo uma interface `IObjectControl`, que personaliza a inicialização de um objeto por ativando e desativando-lo. O cliente chama os métodos que retornam o objeto para o pool e que não retornam o objeto para o pool.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="extensibility-points"></a>Pontos de extensibilidade  
 A primeira etapa na criação de uma extensão do Windows Communication Foundation (WCF) é decidir o ponto de extensibilidade para usar. No WCF, o termo *EndpointDispatcher* refere-se a um componente de tempo de execução responsável pela conversão de mensagens de entrada em invocações do método no serviço do usuário e para converter valores de retorno de método em uma mensagem de saída . Um serviço WCF cria um EndpointDispatcher para cada ponto de extremidade.  
  
 EndpointDispatcher oferece extensibilidade de escopo (para todas as mensagens recebidos ou enviados pelo serviço) de ponto de extremidade usando o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> classe. Essa classe permite personalizar várias propriedades que controlam o comportamento do EndpointDispatcher. Este exemplo enfoca o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 No WCF, EndpointDispatcher cria instâncias de uma classe de serviço usando um provedor de instância que implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface. Essa interface possui apenas dois métodos:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Quando uma mensagem chega, as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método para criar uma instância da classe de serviço para processar a mensagem. A frequência de chamadas a este método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade. Por exemplo se o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> está definida como <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, uma nova instância da classe de serviço é criada para processar cada mensagem que chega, isso <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> é chamado sempre que uma mensagem chega.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Quando a instância do serviço termina de processar a mensagem, EndpointDispatcher chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método. Como no <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, a frequência de chamadas a este método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.  
  
## <a name="the-object-pool"></a>O Pool de objetos  
 O `ObjectPoolInstanceProvider` classe contém a implementação para o pool de objetos. Essa classe implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface para interagir com a camada de modelo de serviço. Quando chama EndpointDispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória. Se houver um disponível, ele será retornado. Caso contrário, `ObjectPoolInstanceProvider` verifica se o `ActiveObjectsCount` propriedade (número de objetos retornados do pool) atingiu o tamanho máximo do pool. Se não, uma nova instância é criada e retornada ao chamador e `ActiveObjectsCount` subsequentemente é incrementada. Caso contrário, uma solicitação de criação do objeto foi enfileirada para um período de tempo configurado. A implementação para `GetObjectFromThePool` é mostrado no código de exemplo a seguir.  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 Personalizado `ReleaseInstance` implementação adiciona a instância liberada para o pool e diminui o `ActiveObjectsCount` valor. EndpointDispatcher pode chamar esses métodos de diversos threads e sincronizado, portanto, o acesso a membros de nível de classe no `ObjectPoolInstanceProvider` classe é necessária.  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 O `ReleaseInstance` método fornece uma *Limpar inicialização* recurso. Normalmente o pool mantém um número mínimo de objetos para o tempo de vida do pool. No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração. Eventualmente quando o pool se torna ativo menos esses objetos excedentes podem se tornar uma sobrecarga extra. Portanto, quando o `activeObjectsCount` chegar a zero é iniciado um timer de ociosidade que dispara e executa um ciclo de limpeza.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Extensões de camada de ServiceModel são conectadas usando os seguintes comportamentos:  
  
-   Comportamentos de serviço: Eles permitem que a personalização do tempo de execução de todo o serviço.  
  
-   Comportamentos de ponto de extremidade: Eles permitem que a personalização de um ponto de extremidade de serviço específico, incluindo EndpointDispatcher.  
  
-   Comportamentos de contrato: Eles permitem a personalização do <xref:System.ServiceModel.Dispatcher.ClientRuntime> ou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes no cliente ou o serviço, respectivamente.  
  
-   Comportamentos de operação: Eles permitem a personalização do <xref:System.ServiceModel.Dispatcher.ClientOperation> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes no cliente ou o serviço, respectivamente.  
  
 Com a finalidade de um objeto de extensão do pool, um comportamento de ponto de extremidade ou um comportamento de serviço pode ser criado. Neste exemplo, usamos um comportamento de serviço, que se aplica a capacidade de cada ponto de extremidade do serviço ao pool de objetos. Comportamentos de serviço são criados com a implementação de <xref:System.ServiceModel.Description.IServiceBehavior> interface. Há várias maneiras de tornar o ServiceModel ciente dos comportamentos personalizados:  
  
-   Usando um atributo personalizado.  
  
-   Imperativa adicionado à coleção de comportamentos da descrição de serviço.  
  
-   Extensão do arquivo de configuração.  
  
 Este exemplo usa um atributo personalizado. Quando o <xref:System.ServiceModel.ServiceHost> é construída, ele examina os atributos usados na definição de tipo de serviço e adiciona os comportamentos disponíveis para a coleção de comportamentos da descrição de serviço.  
  
 O <xref:System.ServiceModel.Description.IServiceBehavior> interface tem três métodos: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Esses métodos são chamados pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> é chamado pela primeira vez; Ele permite que o serviço a ser inspecionado para detectar inconsistências. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> é chamado em seguida; Esse método só é necessário em cenários muito avançados. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> é chamado por último e é responsável por configurar o tempo de execução. Os seguintes parâmetros são passados para <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Esse parâmetro fornece a descrição do serviço para o serviço inteiro. Isso pode ser usado para inspecionar dados descrição sobre pontos de extremidade do serviço e outros dados associados ao serviço, associações e contratos.  
  
-   `ServiceHostBase`: Esse parâmetro fornece o <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializado.  
  
 Em personalizado <xref:System.ServiceModel.Description.IServiceBehavior> implementação, uma nova instância da `ObjectPoolInstanceProvider` é criada e atribuída ao <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> que está associada a <xref:System.ServiceModel.ServiceHostBase>.  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 Além de um <xref:System.ServiceModel.Description.IServiceBehavior> implementação o `ObjectPoolingAttribute` classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo. Esses membros incluem `MaxSize`, `MinSize`, `Enabled` e `CreationTimeout`, para coincidir com o conjunto de recursos fornecido pelo .NET Enterprise Services ao pool de objetos.  
  
 O comportamento de pooling de objeto pode ser adicionado a um serviço WCF, anotando a implementação do serviço com o recém-criado personalizado `ObjectPooling` atributo.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Interceptação de ativação e desativação  
 É o principal objetivo do pool de objetos otimizar a curta duração objetos com a criação relativamente cara e inicialização. Portanto, ela pode fornecer um aumento significativo de desempenho para um aplicativo se usados corretamente. Como o objeto é retornado do pool, o construtor é chamado apenas uma vez. No entanto, alguns aplicativos exigem algum nível de controle para que eles possam inicializar e limpar os recursos usados durante um único contexto. Por exemplo, um objeto que está sendo usado para um conjunto de cálculos pode redefinir seus campos particulares antes de processar o próximo cálculo. Serviços corporativos habilitado esse tipo de inicialização de contexto específico, permitindo que o desenvolvedor de objeto substituir `Activate` e `Deactivate` métodos de <xref:System.EnterpriseServices.ServicedComponent> classe base.  
  
 As chamadas de pool do objeto de `Activate` método antes de retornar o objeto do pool. `Deactivate` é chamado quando o objeto retorna para o pool. O <xref:System.EnterpriseServices.ServicedComponent> classe base também tem um `boolean` propriedade chamada `CanBePooled`, que pode ser usado para notificar o pool se o objeto pode ser agrupado ainda mais.  
  
 Para simular essa funcionalidade, o exemplo declara uma interface pública (`IObjectControl`) que tem os membros mencionados acima. Essa interface é implementada, em seguida, pelo serviço de classes deverá fornecer a inicialização de contexto específico. O <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação deve ser modificada para atender a esses requisitos. Agora, cada vez que você obtém um objeto chamando o `GetInstance` método, você deve verificar se o objeto implementa `IObjectControl.` em caso afirmativo, você deve chamar o `Activate` método adequadamente.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Ao retornar um objeto para o pool, uma verificação é necessária para o `CanBePooled` propriedade antes de adicionar o objeto de volta para o pool.  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 Como o desenvolvedor de serviço pode decidir se um objeto pode ser colocado em pool, a contagem de objeto do pool em um determinado momento pode ir abaixo do tamanho mínimo. Portanto, você deve verificar se a contagem de objetos está abaixo do nível mínimo e executar a inicialização necessária no procedimento de limpeza.  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente. Pressione Enter em cada janela de console para desligar o serviço e o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a>Consulte também
