---
title: Inicialização de instancialização
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183602"
---
# <a name="instancing-initialization"></a>Inicialização de instancialização
Esta amostra estende a amostra de `IObjectControl` [Pooling definindo](../../../../docs/framework/wcf/samples/pooling.md) uma interface, que personaliza a inicialização de um objeto ativando-o e desativando-o. O cliente invoca métodos que retornam o objeto para o pool e que não retornam o objeto para o pool.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="extensibility-points"></a>Pontos de Extensibilidade  
 O primeiro passo para criar uma extensão da Windows Communication Foundation (WCF) é decidir o ponto de extensibilidade a ser usado. No WCF, o termo *EndpointDispatcher* refere-se a um componente de tempo de execução responsável por converter mensagens recebidas em invocações de método no serviço do usuário e converter valores de retorno desse método para uma mensagem de saída. Um serviço WCF cria um EndpointDispatcher para cada ponto final.  
  
 O EndpointDispatcher oferece extensibilidade de escopo de ponto final (para <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> todas as mensagens recebidas ou enviadas pelo serviço) usando a classe. Esta classe permite personalizar várias propriedades que controlam o comportamento do EndpointDispatcher. Esta amostra se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> concentra na propriedade que aponta para o objeto que fornece as instâncias da classe de serviço.  
  
## <a name="iinstanceprovider"></a>Iinstanceprovider  
 No WCF, o EndpointDispatcher cria instâncias de uma classe <xref:System.ServiceModel.Dispatcher.IInstanceProvider> de serviço usando um provedor de instâncias que implementa a interface. Esta interface tem apenas dois métodos:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Quando uma mensagem chega, <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> o Despachante chama o método para criar uma instância da classe de serviço para processar a mensagem. A frequência das chamadas para este <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> método é determinada pela propriedade. Por exemplo, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> se a <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>propriedade estiver definida como , uma nova instância de <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> classe de serviço é criada para processar cada mensagem que chega, por isso é chamado sempre que uma mensagem chega.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Quando a instância de serviço termina o processamento da <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> mensagem, o EndpointDispatcher chama o método. Como no <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> método, a frequência das chamadas para <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> este método é determinada pela propriedade.  
  
## <a name="the-object-pool"></a>O Pool de Objetos  
 A `ObjectPoolInstanceProvider` classe contém a implementação para o pool de objetos. Esta classe implementa a <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface para interagir com a camada do modelo de serviço. Quando o EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> chama o método, em vez de criar uma nova instância, a implementação personalizada procura um objeto existente em um pool de memória. Se um estiver disponível, é devolvido. Caso contrário, `ObjectPoolInstanceProvider` verifica `ActiveObjectsCount` se a propriedade (número de objetos devolvidos do pool) atingiu o tamanho máximo da piscina. Caso não, uma nova instância é criada e `ActiveObjectsCount` devolvida ao chamador e, posteriormente, incrementada. Caso contrário, uma solicitação de criação de objeto saem na fila por um período de tempo configurado. A implementação `GetObjectFromThePool` é mostrada no seguinte código de amostra.  
  
```csharp
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
  
 A `ReleaseInstance` implementação personalizada adiciona a instância liberada de `ActiveObjectsCount` volta ao pool e decreta o valor. O EndpointDispatcher pode chamar esses métodos de diferentes segmentos e, portanto, o acesso sincronizado aos membros do nível de classe na `ObjectPoolInstanceProvider` classe é necessário.  
  
```csharp
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
  
 O `ReleaseInstance` método fornece um recurso *de inicialização* de limpeza. Normalmente, a piscina mantém um número mínimo de objetos durante a vida útil da piscina. No entanto, pode haver períodos de uso excessivo que requerem a criação de objetos adicionais no pool para atingir o limite máximo especificado na configuração. Eventualmente, quando a piscina se torna menos ativa, esses objetos excedentes podem se tornar uma sobrecarga extra. Portanto, quando `activeObjectsCount` o atinge zero um temporizador ocioso é iniciado que aciona e executa um ciclo de limpeza.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 As extensões de camada serviceModel são ligadas usando os seguintes comportamentos:  
  
- Comportamentos de serviço: Estes permitem a personalização de todo o tempo de execução do serviço.  
  
- Comportamentos de ponto final: Estes permitem a personalização de um ponto final de serviço específico, incluindo o EndpointDispatcher.  
  
- Comportamentos contratuais: Estes permitem a <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> personalização de qualquer ou classes sobre o cliente ou o serviço, respectivamente.  
  
- Comportamentos de operação: Estes permitem <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> personalização de qualquer ou classes sobre o cliente ou o serviço, respectivamente.  
  
 Para fins de uma extensão de agrupamento de objetos, um comportamento de ponto final ou um comportamento de serviço podem ser criados. Neste exemplo, usamos um comportamento de serviço, que aplica a capacidade de agrupamento de objetos em todos os pontos finais do serviço. Os comportamentos de serviço são <xref:System.ServiceModel.Description.IServiceBehavior> criados implementando a interface. Existem várias maneiras de conscientizar o ServiceModel sobre os comportamentos personalizados:  
  
- Usando um atributo personalizado.  
  
- Adicioná-lo imperativamente à coleção de comportamentos da descrição do serviço.  
  
- Estendendo o arquivo de configuração.  
  
 Esta amostra usa um atributo personalizado. Quando <xref:System.ServiceModel.ServiceHost> o é construído, examina os atributos utilizados na definição do tipo do serviço e adiciona os comportamentos disponíveis à coleção de comportamentos da descrição do serviço.  
  
 A <xref:System.ServiceModel.Description.IServiceBehavior> interface tem três <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>métodos: e . Esses métodos são chamados pelo <xref:System.ServiceModel.ServiceHost> WCF quando o está sendo inicializado. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>é chamado primeiro; permite que o serviço seja inspecionado por inconsistências. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>é chamado de próximo; este método só é necessário em cenários muito avançados. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>é chamado de último e é responsável pela configuração do tempo de execução. Os seguintes parâmetros são passados em: <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>  
  
- `Description`: Este parâmetro fornece a descrição do serviço para todo o serviço. Isso pode ser usado para inspecionar dados de descrição sobre os pontos finais do serviço, contratos, vinculações e outros dados associados ao serviço.  
  
- `ServiceHostBase`: Este parâmetro <xref:System.ServiceModel.ServiceHostBase> fornece o que está sendo inicializado.  
  
 Na <xref:System.ServiceModel.Description.IServiceBehavior> implementação personalizada, uma `ObjectPoolInstanceProvider` nova instância é instanciada e atribuída à <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedade em cada uma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> das que está anexada ao <xref:System.ServiceModel.ServiceHostBase>.  
  
```csharp
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
  
 Além de <xref:System.ServiceModel.Description.IServiceBehavior> uma `ObjectPoolingAttribute` implementação, a classe tem vários membros para personalizar o pool de objetos usando os argumentos de atributo. Esses membros `MaxSize` `MinSize`incluem `Enabled` `CreationTimeout`, e , para corresponder ao conjunto de recursos de pooling de objetos fornecido pelo .NET Enterprise Services.  
  
 O comportamento de pooling de objetos agora pode ser adicionado a um serviço `ObjectPooling` WCF anotando a implementação do serviço com o atributo personalizado recém-criado.  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Ativação e desativação de ganchos  
 O objetivo principal do agrupamento de objetos é otimizar objetos de curta duração com criação e inicialização relativamente caras. Portanto, ele pode dar um aumento dramático de desempenho para uma aplicação se usado corretamente. Como o objeto é devolvido da piscina, o construtor é chamado apenas uma vez. No entanto, alguns aplicativos exigem algum nível de controle para que possam inicializar e limpar os recursos usados durante um único contexto. Por exemplo, um objeto que está sendo usado para um conjunto de cálculos pode redefinir seus campos privados antes de processar o próximo cálculo. Os Serviços Corporativos permitiram esse tipo de inicialização `Activate` `Deactivate` específica do <xref:System.EnterpriseServices.ServicedComponent> contexto, permitindo que o desenvolvedor de objetos se sobreponha e os métodos da classe base.  
  
 O pool de `Activate` objetos chama o método pouco antes de devolver o objeto da piscina. `Deactivate`é chamado quando o objeto retorna para a piscina. A <xref:System.EnterpriseServices.ServicedComponent> classe base `boolean` também `CanBePooled`tem uma propriedade chamada , que pode ser usada para notificar o pool se o objeto pode ser agrupado ainda mais.  
  
 Para imitar essa funcionalidade, a amostra declara`IObjectControl`uma interface pública ( ) que tem os membros acima mencionados. Essa interface é então implementada por classes de serviço destinadas a fornecer inicialização específica do contexto. A <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementação deve ser modificada para atender a esses requisitos. Agora, cada vez que você `GetInstance` recebe um objeto chamando o `IObjectControl.` método, você deve `Activate` verificar se o objeto implementa Se ele faz, você deve chamar o método apropriadamente.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Ao devolver um objeto à piscina, é `CanBePooled` necessária uma verificação para a propriedade antes de adicionar o objeto de volta à piscina.  
  
```csharp  
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
  
 Como o desenvolvedor do serviço pode decidir se um objeto pode ser agrupado, a contagem de objetos no pool em um determinado momento pode ficar abaixo do tamanho mínimo. Portanto, você deve verificar se a contagem de objetos foi abaixo do nível mínimo e realizar a inicialização necessária no procedimento de limpeza.  
  
```csharp  
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
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas nas janelas do serviço e do console cliente. Pressione Enter em cada janela do console para desligar o serviço e o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
