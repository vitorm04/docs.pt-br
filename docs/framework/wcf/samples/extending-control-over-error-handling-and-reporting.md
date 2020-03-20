---
title: Controle estendido através de relatórios e tratamento de erro
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 68f3381e8db9d7c0222720dda335b47e30f57ac7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183677"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Controle estendido através de relatórios e tratamento de erro
Esta amostra demonstra como estender o controle sobre o manuseio de erros e <xref:System.ServiceModel.Dispatcher.IErrorHandler> relatórios de erros em um serviço WCF (Windows Communication Foundation) usando a interface. A amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) com algum código adicional adicionado ao serviço para lidar com erros. O cliente força várias condições de erro. O serviço intercepta os erros e os registra em um arquivo.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Os serviços podem interceptar erros, realizar processamento e <xref:System.ServiceModel.Dispatcher.IErrorHandler> afetar a forma como os erros são relatados usando a interface. A interface tem dois métodos <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> que <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>podem ser implementados: e . O <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> método permite adicionar, modificar ou suprimir uma mensagem de falha gerada em resposta a uma exceção. O <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> método permite que o processamento de erros ocorra no caso de um erro e controla se o manuseio adicional de erros pode ser executado.  
  
 Nesta amostra, `CalculatorErrorHandler` o tipo <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementa a interface. No  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>método, `CalculatorErrorHandler` a grava um registro do erro em um arquivo de texto Error.txt em c:\logs. Observe que a amostra registra a falha e não a suprime, permitindo que ela seja reportada de volta ao cliente.  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 O `ErrorBehaviorAttribute` existe como um mecanismo para registrar um manipulador de erros com um serviço. Este atributo requer um parâmetro de tipo único. Esse tipo deve <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementar a interface e deve ter um construtor público e vazio. O atributo então instancia uma instância desse tipo de manipulador de erros e o instala no serviço. Ele faz isso implementando a <xref:System.ServiceModel.Description.IServiceBehavior> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> interface e, em seguida, usando o método para adicionar instâncias do manipulador de erros ao serviço.  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 A amostra implementa um serviço de calculadora. O cliente deliberadamente faz com que dois erros ocorram no serviço, fornecendo parâmetros com valores ilegais. O `CalculatorErrorHandler` uso <xref:System.ServiceModel.Dispatcher.IErrorHandler> da interface para registrar os erros em um arquivo local e, em seguida, permite que eles sejam reportados de volta ao cliente. O cliente força uma divisão por zero e uma condição de discussão fora de alcance.  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Você vê a divisão por zero e as condições de discussão fora de alcance sendo relatadas como falhas. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 O arquivo c:\logs\errors.txt contém as informações registradas sobre os erros do serviço. Observe que para o serviço escrever no diretório você deve ter certeza de que o processo em que o serviço está sendo executado (normalmente ASP.NET ou Serviço de Rede) tem permissão para escrever no diretório.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Certifique-se de ter criado o diretório c:\logs para o arquivo error.txt. Ou modificar o nome `CalculatorErrorHandler.HandleError`do arquivo usado em .  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
