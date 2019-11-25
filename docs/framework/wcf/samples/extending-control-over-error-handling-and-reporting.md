---
title: Controle estendido através de relatórios e tratamento de erro
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: abb747a0deecb7e07776d9cd6ef5bc3775b1be9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281700"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="936a6-102">Controle estendido através de relatórios e tratamento de erro</span><span class="sxs-lookup"><span data-stu-id="936a6-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="936a6-103">Este exemplo demonstra como estender o controle sobre o tratamento de erros e o relatório de erros em um serviço Windows Communication Foundation (WCF) usando a interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="936a6-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="936a6-104">O exemplo se baseia na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) com algum código adicional adicionado ao serviço para lidar com erros.</span><span class="sxs-lookup"><span data-stu-id="936a6-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="936a6-105">O cliente força várias condições de erro.</span><span class="sxs-lookup"><span data-stu-id="936a6-105">The client forces several error conditions.</span></span> <span data-ttu-id="936a6-106">O serviço intercepta os erros e os registra em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="936a6-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="936a6-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="936a6-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="936a6-108">Os serviços podem interceptar erros, executar o processamento e afetar como os erros são relatados usando a interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="936a6-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="936a6-109">A interface tem dois métodos que podem ser implementados: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> e <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span><span class="sxs-lookup"><span data-stu-id="936a6-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="936a6-110">O método <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> permite adicionar, modificar ou suprimir uma mensagem de falha gerada em resposta a uma exceção.</span><span class="sxs-lookup"><span data-stu-id="936a6-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="936a6-111">O método <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> permite que o processamento de erro ocorra em caso de erro e controle se o tratamento de erros adicional pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="936a6-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="936a6-112">Neste exemplo, o tipo de `CalculatorErrorHandler` implementa a interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="936a6-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="936a6-113">No</span><span class="sxs-lookup"><span data-stu-id="936a6-113">In the</span></span>  
  
 <span data-ttu-id="936a6-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> método, o `CalculatorErrorHandler` grava um log do erro em um arquivo de texto Error. txt em c:\Logs.</span><span class="sxs-lookup"><span data-stu-id="936a6-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="936a6-115">Observe que o exemplo registra em log a falha e não a suprimi, permitindo que ela seja relatada de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="936a6-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
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
  
 <span data-ttu-id="936a6-116">O `ErrorBehaviorAttribute` existe como um mecanismo para registrar um manipulador de erro com um serviço.</span><span class="sxs-lookup"><span data-stu-id="936a6-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="936a6-117">Esse atributo usa um único parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="936a6-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="936a6-118">Esse tipo deve implementar a interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> e deve ter um construtor público e vazio.</span><span class="sxs-lookup"><span data-stu-id="936a6-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="936a6-119">Em seguida, o atributo cria uma instância desse tipo de manipulador de erros e o instala no serviço.</span><span class="sxs-lookup"><span data-stu-id="936a6-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="936a6-120">Ele faz isso implementando a interface <xref:System.ServiceModel.Description.IServiceBehavior> e, em seguida, usando o método <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> para adicionar instâncias do manipulador de erros ao serviço.</span><span class="sxs-lookup"><span data-stu-id="936a6-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
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
  
 <span data-ttu-id="936a6-121">O exemplo implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="936a6-121">The sample implements a calculator service.</span></span> <span data-ttu-id="936a6-122">O cliente deliberadamente faz com que dois erros ocorram no serviço fornecendo parâmetros com valores ilegais.</span><span class="sxs-lookup"><span data-stu-id="936a6-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="936a6-123">O `CalculatorErrorHandler` usa a interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> para registrar os erros em um arquivo local e, em seguida, permite que eles sejam relatados de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="936a6-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="936a6-124">O cliente força uma divisão por zero e uma condição fora do intervalo de argumento.</span><span class="sxs-lookup"><span data-stu-id="936a6-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
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
  
 <span data-ttu-id="936a6-125">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="936a6-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="936a6-126">Você vê a divisão por zero e as condições de argumento fora do intervalo sendo relatadas como falhas.</span><span class="sxs-lookup"><span data-stu-id="936a6-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="936a6-127">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="936a6-127">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="936a6-128">O arquivo c:\logs\errors.txt contém as informações registradas sobre os erros pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="936a6-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="936a6-129">Observe que, para o serviço gravar no diretório, você deve certificar-se de que o processo no qual o serviço está sendo executado (normalmente ASP.NET ou Network Service) tenha permissão para gravar no diretório.</span><span class="sxs-lookup"><span data-stu-id="936a6-129">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="936a6-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="936a6-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="936a6-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="936a6-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="936a6-132">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="936a6-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="936a6-133">Verifique se você criou o diretório c:\Logs para o arquivo error. txt.</span><span class="sxs-lookup"><span data-stu-id="936a6-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="936a6-134">Ou modifique o nome do arquivo usado em `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="936a6-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="936a6-135">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="936a6-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="936a6-136">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="936a6-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="936a6-137">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="936a6-137">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="936a6-138">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="936a6-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="936a6-139">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="936a6-139">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
