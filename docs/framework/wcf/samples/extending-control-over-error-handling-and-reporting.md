---
title: Controle estendido através de relatórios e tratamento de erro
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 30b36f5373563ec9faba8e655ab1e31d47b23c99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622449"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Controle estendido através de relatórios e tratamento de erro
Este exemplo demonstra como estender o controle sobre o tratamento de erros e o relatório de erros no como um serviço do Windows Communication Foundation (WCF) usando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface. O exemplo se baseia o [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) com algum código adicional adicionado ao serviço para lidar com erros. O cliente força várias condições de erro. O serviço intercepta os erros e registra em log em um arquivo.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Serviços podem interceptar erros, executar o processamento e afetam como os erros são relatados usando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface. A interface tem dois métodos que podem ser implementados: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> e <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. O <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> método permite que você adicionar, modificar ou suprimir uma mensagem de falha é gerada em resposta a uma exceção. O <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> método permite o processamento de erro entrar em vigor no caso de controles e um erro se o tratamento de erros adicionais pode ser executados.  
  
 Neste exemplo, o `CalculatorErrorHandler` tipo implementa o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface. No  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> método, o `CalculatorErrorHandler` grava um log do erro para um arquivo de texto em c:\logs Error. Observe que o exemplo registra a falha e não suprimi-lo, permitindo que ele ser relatados de volta ao cliente.  
  
```  
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
  
 O `ErrorBehaviorAttribute` existe como um mecanismo para registrar um manipulador de erro com um serviço. Esse atributo usa um único parâmetro de tipo. Que tipo deve implementar a <xref:System.ServiceModel.Dispatcher.IErrorHandler> de interface e deve ter um construtor público vazio. O atributo, em seguida, cria uma instância desse tipo de manipulador de erro e o instala no serviço. Ele faz isso Implementando a <xref:System.ServiceModel.Description.IServiceBehavior> interface e, em seguida, usando o <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> método para adicionar instâncias do manipulador de erros para o serviço.  
  
```  
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
  
 O exemplo implementa um serviço de calculadora. O cliente deliberadamente faz com que dois erros ocorrem no serviço, fornecendo parâmetros com valores ilegais. O `CalculatorErrorHandler` usa o <xref:System.ServiceModel.Dispatcher.IErrorHandler> de interface para registrar em log os erros em um arquivo local e, em seguida, permite que eles ser relatados de volta ao cliente. O cliente força uma divisão por zero e uma condição de argumento fora do intervalo.  
  
```  
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
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Você verá a divisão por zero e as condições de argumento fora do intervalo que está sendo relatadas como falhas. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 O arquivo c:\logs\errors.txt contém as informações registradas sobre os erros pelo serviço. Observe que, para o serviço gravar no diretório, certifique-se que o processo sob a qual o serviço está em execução (normalmente ASP.NET ou serviço de rede), tem a permissão para gravar no diretório.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Certifique-se de que você criou o diretório c:\Logs. para o arquivo Error. Ou modificar o nome de arquivo usado no `CalculatorErrorHandler.HandleError`.  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a>Consulte também
