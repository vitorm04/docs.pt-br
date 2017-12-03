---
title: tempo de vida personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2538a9c483b949dfef1c60bd2225f5daf4e01117
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-lifetime"></a>tempo de vida personalizado
Este exemplo demonstra como gravar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extensão para fornecer serviços de tempo de vida personalizado para compartilhado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] instâncias de serviço.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="shared-instancing"></a>Compartilhado de instanciação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece vários modos de instância para suas instâncias de serviço. O modo compartilhado instanciação abordado neste tópico fornece uma maneira de compartilhar uma instância de serviço entre vários canais. Os clientes podem resolver o endereço de ponto de extremidade da instância local ou entre em contato com um método de fábrica no serviço para obter o endereço de ponto de extremidade de uma instância em execução. Depois que ele tem o endereço de ponto de extremidade, ele pode criar um novo canal e iniciar a comunicação. O trecho de código a seguir mostra como um aplicativo cliente cria um novo canal para uma instância de serviço existente.  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 Ao contrário de outros modos de instância, o modo de instanciamento compartilhado tem forma singular de liberação as instâncias de serviço. Quando todos os canais são fechados para uma instância, o serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução inicia um cronômetro. Se ninguém faz uma conexão antes do tempo limite expirar, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] libera a instância e os recursos de declarações. Como parte do procedimento subdivisão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoca o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método de todos os <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementações antes de liberar a instância. Se todos eles retornarem `true` a instância é liberada. Caso contrário, o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação é responsável por notificar o `Dispatcher` do estado ocioso, usando um método de retorno de chamada.  
  
 Por padrão, o valor de tempo limite de ociosidade de <xref:System.ServiceModel.InstanceContext> é um minuto. No entanto, este exemplo demonstra como você pode estender esse usando uma extensão personalizada.  
  
## <a name="extending-the-instancecontext"></a>Estendendo o InstanceContext  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> é o vínculo entre a instância de serviço e o `Dispatcher`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]permite que você estenda a esse componente de tempo de execução, adicionando o novo estado ou comportamento usando o padrão de objeto extensível. O padrão de objeto extensível é usado em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar novos recursos de estado para um objeto. Existem três interfaces no padrão de objeto extensível: `IExtensibleObject<T>`, `IExtension<T>`, e `IExtensionCollection<T>`.  
  
 O `IExtensibleObject<T>` interface é implementada por objetos para permitir extensões que personalizar sua funcionalidade.  
  
 O `IExtension<T>` interface é implementada por objetos que podem ser extensões de classes do tipo `T`.  
  
 E, finalmente, o `IExtensionCollection<T>` interface é uma coleção de `IExtensions` que permite recuperar `IExtensions` por seu tipo.  
  
 Portanto, para estender o <xref:System.ServiceModel.InstanceContext> você deve implementar o `IExtension` interface. Neste projeto de exemplo de `CustomLeaseExtension` classe contém essa implementação.  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 O `IExtension` interface tem dois métodos `Attach` e `Detach`. Como seus nomes sugerem, esses dois métodos são chamados quando o tempo de execução se conecta e desconecta a extensão a uma instância do <xref:System.ServiceModel.InstanceContext> classe. Neste exemplo, o `Attach` método é usado para controlar o <xref:System.ServiceModel.InstanceContext> objeto ao qual pertence a instância atual da extensão.  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 Além disso, adicione a implementação necessária para a extensão para fornecer o suporte de tempo de vida estendida. Portanto, o `ICustomLease` interface é declarada com os métodos desejados e é implementada no `CustomLeaseExtension` classe.  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 Quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoca o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método no <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação esta chamada é roteada para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método o `CustomLeaseExtension`. Em seguida, o `CustomLeaseExtension` verifica seu estado particular para ver se o <xref:System.ServiceModel.InstanceContext> está ocioso. Se ele estiver ocioso ele retorna `true`. Caso contrário, ele inicia um temporizador para um determinado período de tempo de vida estendido.  
  
```  
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
  
 Do timer `Elapsed` a função de retorno de chamada no Dispatcher de evento é chamada para iniciar outro ciclo de limpeza.  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 Não é possível renovar o timer de execução quando uma nova mensagem chega para a instância que está sendo movida para o estado ocioso.  
  
 O exemplo implementa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> para interceptar as chamadas para o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> rota e o método para o `CustomLeaseExtension`. O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementação está contida no `CustomLifetimeLease` classe. O <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método é invocado quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está prestes a liberar a instância do serviço. No entanto, há apenas uma instância de um determinado `ISharedSessionInstance` implementação no ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> coleção. Isso significa que não há maneira de saber o <xref:System.ServiceModel.InstanceContext> que está sendo fechado no momento [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] verifica o <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método. Portanto, este exemplo usa o thread para serializar as solicitações de bloqueio de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> método.  
  
> [!IMPORTANT]
>  Usando o bloqueio de thread não é uma abordagem recomendada porque a serialização pode afetar seriamente o desempenho do seu aplicativo.  
  
 Uma variável de membro privado é usada no `CustomLeaseExtension` classe para rastrear o `IsIdle` valor. Cada vez que o valor de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> é recuperado do `IsIdle` membro privado é retornado e redefinir a `false`. É essencial para definir esse valor como `false` para garantir que as chamadas de Dispatcher de <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> método.  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 Se o `ISharedSessionLifetime.IsIdle` propriedade retorna `false` o Dispatcher registra uma função de retorno de chamada usando o `NotifyIdle` método. Este método recebe uma referência para o <xref:System.ServiceModel.InstanceContext> sendo lançada. Portanto o código de exemplo pode consultar o `ICustomLease` tipo de extensão e verifique o `ICustomLease.IsIdle` propriedade no estado estendido.  
  
```  
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
  
 Antes do `ICustomLease.IsIdle` propriedade estiver marcada, a propriedade de retorno de chamada precisa ser definida como isso é essencial para `CustomLeaseExtension` para notificar o Dispatcher quando ele estiver ocioso. Se `ICustomLease.IsIdle` retorna `true`, o `isIdle` membro privado simplesmente é definido `CustomLifetimeLease` para `true` e chama o método de retorno de chamada. Como o código mantém um bloqueio, outros threads não é possível alterar o valor desse membro privado. E na próxima vez em que o distribuidor verifica o `ISharedSessionLifetime.IsIdle`, ele retorna `true` e permite que o Dispatcher liberar a instância.  
  
 Agora que a base para a extensão personalizada é concluída, ele deve ser vinculada ao modelo de serviço. Para ligar o `CustomLeaseExtension` implementação para o <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece o <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> para executar a inicialização de <xref:System.ServiceModel.InstanceContext>. No exemplo, o `CustomLeaseInitializer` classe implementa essa interface e adiciona uma instância de `CustomLeaseExtension` para o <xref:System.ServiceModel.InstanceContext.Extensions%2A> coleção de inicialização o único método. Este método é chamado pelo Dispatcher ao inicializar o <xref:System.ServiceModel.InstanceContext>.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 Por fim o `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` e <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> são implementações é gancho até o modelo de serviço usando o <xref:System.ServiceModel.Description.IServiceBehavior> implementação. Essa implementação é colocada no `CustomLeaseTimeAttribute` classe e ele também deriva o `Attribute` classe para expor esse comportamento como um atributo base. No `IServiceBehavior.ApplyBehavior` método, instâncias de <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> e `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementações são adicionadas para o `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` e <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> coleções do <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectivamente.  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 Esse comportamento pode ser adicionado a uma classe de serviço de exemplo, anotando-o com o `CustomLeaseTime` atributo.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>Consulte também
