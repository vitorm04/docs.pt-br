---
title: Inicialização de instancialização
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 1414908025416f4cdd6e5b51c052799631ab52cd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322180"
---
# <a name="instancing-initialization"></a>Inicialização de instancialização
Este exemplo amplia a [Pooling](../../../../docs/framework/wcf/samples/pooling.md) exemplo definindo uma interface `IObjectControl`, que personaliza a inicialização de um objeto, ativando e desativando-lo. O cliente invoca métodos que retornam o objeto para o pool e que não retornam o objeto para o pool.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="extensibility-points"></a>Pontos de extensibilidade  
 A primeira etapa na criação de uma extensão do Windows Communication Foundation (WCF) é decidir o ponto de extensibilidade para usar. No WCF, o termo *EndpointDispatcher* refere-se a um responsável para converter as mensagens de entrada para invocações de método no serviço do usuário e para converter valores de retorno de método em uma mensagem de saída de componente de tempo de execução . Um serviço WCF cria um EndpointDispatcher para cada ponto de extremidade.  
  
 EndpointDispatcher oferece extensibilidade de escopo (para todas as mensagens recebidas ou enviadas pelo serviço) de ponto de extremidade usando o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> classe. Essa classe permite que você personalizar várias propriedades que controlam o comportamento do EndpointDispatcher. Este exemplo destaca o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 No WCF, EndpointDispatcher cria instâncias de uma classe de serviço usando um provedor de instância que implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface. Essa interface tem apenas dois métodos:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Quando uma mensagem chega, as chamadas de Dispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método para criar uma instância da classe de serviço para processar a mensagem. A frequência das chamadas para esse método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade. Por exemplo se o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> estiver definida como <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, uma nova instância da classe de serviço é criada para processar cada mensagem que chega, isso <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> é chamado sempre que uma mensagem chega.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Quando a instância de serviço termina de processar a mensagem, EndpointDispatcher chama o <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> método. Como mostra a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, a frequência das chamadas para esse método é determinada pelo <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade.  
  
## <a name="the-object-pool"></a>O Pool de objetos  
 O `ObjectPoolInstanceProvider` classe contém a implementação para o pool de objetos. Essa classe implementa o <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface para interagir com a camada de modelo de serviço. Quando chama EndpointDispatcher a <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória. Se houver um disponível, ele será retornado. Caso contrário, `ObjectPoolInstanceProvider` verifica se o `ActiveObjectsCount` propriedade (número de objetos retornados do pool) atingiu o tamanho máximo do pool. Se não, uma nova instância é criada e retornada ao chamador e `ActiveObjectsCount` subsequentemente é incrementado. Caso contrário, uma solicitação de criação do objeto foi enfileirada para um período de tempo configurado. A implementação para `GetObjectFromThePool` é mostrado no código de exemplo a seguir.  
  
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
  
 O custom `ReleaseInstance` implementação adiciona a instância liberada para o pool e diminui a `ActiveObjectsCount` valor. EndpointDispatcher pode chamar esses métodos de diversos threads e sincronizado, portanto, o acesso a membros de nível de classe no `ObjectPoolInstanceProvider` classe é necessária.  
  
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
  
 O `ReleaseInstance` método fornece uma *Limpar inicialização* recurso. Normalmente o pool mantém um número mínimo de objetos para o tempo de vida do pool. No entanto, pode haver períodos de uso excessivo que exigem a criação de objetos adicionais no pool para alcançar o limite máximo especificado na configuração. Eventualmente, quando o pool se torna menos ativo esses objetos de excedente podem se tornar uma sobrecarga extra. Portanto, quando o `activeObjectsCount` chegar a zero um timer de ociosidade é iniciado e que aciona e executa um ciclo de limpeza.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Extensões de camada de ServiceModel são conectadas usando os seguintes comportamentos:  
  
-   Comportamentos de serviço: Eles permitem a personalização do tempo de execução de todo o serviço.  
  
-   Comportamentos de ponto de extremidade: Eles permitem a personalização de um ponto de extremidade de serviço específico, incluindo EndpointDispatcher.  
  
-   Comportamentos de contrato: Eles permitem a personalização de um <xref:System.ServiceModel.Dispatcher.ClientRuntime> ou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes no cliente ou o serviço, respectivamente.  
  
-   Comportamentos de operação: Eles permitem a personalização de um <xref:System.ServiceModel.Dispatcher.ClientOperation> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes no cliente ou o serviço, respectivamente.  
  
 Com a finalidade de um objeto de extensão do pool, um comportamento de ponto de extremidade ou um comportamento de serviço pode ser criado. Neste exemplo, usamos um comportamento de serviço, que se aplica a capacidade de cada ponto de extremidade do serviço ao pool de objetos. Comportamentos de serviço são criados com a implementação de <xref:System.ServiceModel.Description.IServiceBehavior> interface. Há várias maneiras de tornar o ServiceModel cientes dos comportamentos personalizados:  
  
-   Usando um atributo personalizado.  
  
-   Imperativamente adicionando-o à coleção de comportamentos da descrição do serviço.  
  
-   Estendendo o arquivo de configuração.  
  
 Este exemplo usa um atributo personalizado. Quando o <xref:System.ServiceModel.ServiceHost> é construído, ele examina os atributos usados na definição de tipo de serviço e adiciona os comportamentos disponíveis para a coleção de comportamentos da descrição do serviço.  
  
 O <xref:System.ServiceModel.Description.IServiceBehavior> interface possui três métodos: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Esses métodos são chamados pelo WCF quando o <xref:System.ServiceModel.ServiceHost> está sendo inicializado. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> é chamado pela primeira vez; Ele permite que o serviço a ser inspecionado para detectar inconsistências. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> é chamado em seguida; Esse método só é necessário em cenários muito avançados. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> é chamado pela última vez e é responsável por configurar o tempo de execução. Os seguintes parâmetros são passados para <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Esse parâmetro fornece a descrição do serviço para o serviço inteiro. Isso pode ser usado para inspecionar os dados de descrição sobre pontos de extremidade do serviço, contratos, associações e outros dados associados ao serviço.  
  
-   `ServiceHostBase`: Esse parâmetro fornece o <xref:System.ServiceModel.ServiceHostBase> que está sendo inicializado.  
  
 O personalizado <xref:System.ServiceModel.Description.IServiceBehavior> implementação, uma nova instância da `ObjectPoolInstanceProvider` será instanciado e atribuído ao <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> que é anexado ao <xref:System.ServiceModel.ServiceHostBase>.  
  
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
  
 Além uma <xref:System.ServiceModel.Description.IServiceBehavior> implementação de `ObjectPoolingAttribute` classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo. Esses membros incluem `MaxSize`, `MinSize`, `Enabled` e `CreationTimeout`, para coincidir com o conjunto de recursos fornecido pelo .NET Enterprise Services ao pool de objetos.  
  
 O comportamento do pooling de objeto pode ser adicionado a um serviço WCF, anotando a implementação do serviço com o recém-criado personalizado `ObjectPooling` atributo.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Vinculando a ativação e desativação  
 O objetivo principal do pool de objetos é otimizar com a criação relativamente cara e inicialização de objetos de curta duração. Portanto, ele pode fornecer um aumento de desempenho significativo a um aplicativo se usados corretamente. Porque o objeto é retornado do pool, o construtor é chamado apenas uma vez. No entanto, alguns aplicativos exigem algum nível de controle para que eles possam inicializar e limpar os recursos usados durante um único contexto. Por exemplo, um objeto que está sendo usado para um conjunto de cálculos pode redefinir seus campos privados antes de processar o próximo cálculo. Enterprise Services habilitado esse tipo de inicialização de contexto específico, permitindo que o desenvolvedor de objeto substituir `Activate` e `Deactivate` métodos a partir de <xref:System.EnterpriseServices.ServicedComponent> classe base.  
  
 As chamadas de pool do objeto a `Activate` método antes de retornar o objeto do pool. `Deactivate` é chamado quando o objeto retorna ao pool. O <xref:System.EnterpriseServices.ServicedComponent> classe base também tem uma `boolean` propriedade chamada `CanBePooled`, que pode ser usado para notificar o pool se o objeto pode ser agrupado ainda mais.  
  
 Para simular essa funcionalidade, o exemplo declara uma interface pública (`IObjectControl`) que tem os membros mencionados anteriormente. Essa interface implementada por classes destinadas a fornecer a inicialização de contexto específico de serviço. O <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação deve ser modificada para atender a esses requisitos. Agora, sempre que você obtenha um objeto chamando o `GetInstance` método, você deve verificar se o objeto implementa `IObjectControl.` em caso afirmativo, você deve chamar o `Activate` método adequadamente.  
  
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
  
 Porque o desenvolvedor de serviço pode decidir se um objeto pode ser colocado em pool, a contagem de objetos em um pool em um determinado momento pode ir abaixo do tamanho mínimo. Portanto, você deve verificar se a contagem de objeto ficar abaixo do nível mínimo e execute a inicialização necessária do procedimento de limpeza.  
  
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
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente. Pressione Enter em cada janela de console para desligar o serviço e o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
