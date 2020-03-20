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
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="40a8b-102">Controle estendido através de relatórios e tratamento de erro</span><span class="sxs-lookup"><span data-stu-id="40a8b-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="40a8b-103">Esta amostra demonstra como estender o controle sobre o manuseio de erros e <xref:System.ServiceModel.Dispatcher.IErrorHandler> relatórios de erros em um serviço WCF (Windows Communication Foundation) usando a interface.</span><span class="sxs-lookup"><span data-stu-id="40a8b-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="40a8b-104">A amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) com algum código adicional adicionado ao serviço para lidar com erros.</span><span class="sxs-lookup"><span data-stu-id="40a8b-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="40a8b-105">O cliente força várias condições de erro.</span><span class="sxs-lookup"><span data-stu-id="40a8b-105">The client forces several error conditions.</span></span> <span data-ttu-id="40a8b-106">O serviço intercepta os erros e os registra em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="40a8b-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40a8b-107">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="40a8b-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="40a8b-108">Os serviços podem interceptar erros, realizar processamento e <xref:System.ServiceModel.Dispatcher.IErrorHandler> afetar a forma como os erros são relatados usando a interface.</span><span class="sxs-lookup"><span data-stu-id="40a8b-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="40a8b-109">A interface tem dois métodos <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> que <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>podem ser implementados: e .</span><span class="sxs-lookup"><span data-stu-id="40a8b-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="40a8b-110">O <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> método permite adicionar, modificar ou suprimir uma mensagem de falha gerada em resposta a uma exceção.</span><span class="sxs-lookup"><span data-stu-id="40a8b-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="40a8b-111">O <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> método permite que o processamento de erros ocorra no caso de um erro e controla se o manuseio adicional de erros pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="40a8b-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="40a8b-112">Nesta amostra, `CalculatorErrorHandler` o tipo <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="40a8b-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="40a8b-113">No</span><span class="sxs-lookup"><span data-stu-id="40a8b-113">In the</span></span>  
  
 <span data-ttu-id="40a8b-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>método, `CalculatorErrorHandler` a grava um registro do erro em um arquivo de texto Error.txt em c:\logs.</span><span class="sxs-lookup"><span data-stu-id="40a8b-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="40a8b-115">Observe que a amostra registra a falha e não a suprime, permitindo que ela seja reportada de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="40a8b-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
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
  
 <span data-ttu-id="40a8b-116">O `ErrorBehaviorAttribute` existe como um mecanismo para registrar um manipulador de erros com um serviço.</span><span class="sxs-lookup"><span data-stu-id="40a8b-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="40a8b-117">Este atributo requer um parâmetro de tipo único.</span><span class="sxs-lookup"><span data-stu-id="40a8b-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="40a8b-118">Esse tipo deve <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementar a interface e deve ter um construtor público e vazio.</span><span class="sxs-lookup"><span data-stu-id="40a8b-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="40a8b-119">O atributo então instancia uma instância desse tipo de manipulador de erros e o instala no serviço.</span><span class="sxs-lookup"><span data-stu-id="40a8b-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="40a8b-120">Ele faz isso implementando a <xref:System.ServiceModel.Description.IServiceBehavior> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> interface e, em seguida, usando o método para adicionar instâncias do manipulador de erros ao serviço.</span><span class="sxs-lookup"><span data-stu-id="40a8b-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
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
  
 <span data-ttu-id="40a8b-121">A amostra implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="40a8b-121">The sample implements a calculator service.</span></span> <span data-ttu-id="40a8b-122">O cliente deliberadamente faz com que dois erros ocorram no serviço, fornecendo parâmetros com valores ilegais.</span><span class="sxs-lookup"><span data-stu-id="40a8b-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="40a8b-123">O `CalculatorErrorHandler` uso <xref:System.ServiceModel.Dispatcher.IErrorHandler> da interface para registrar os erros em um arquivo local e, em seguida, permite que eles sejam reportados de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="40a8b-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="40a8b-124">O cliente força uma divisão por zero e uma condição de discussão fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="40a8b-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
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
  
 <span data-ttu-id="40a8b-125">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="40a8b-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="40a8b-126">Você vê a divisão por zero e as condições de discussão fora de alcance sendo relatadas como falhas.</span><span class="sxs-lookup"><span data-stu-id="40a8b-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="40a8b-127">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="40a8b-127">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="40a8b-128">O arquivo c:\logs\errors.txt contém as informações registradas sobre os erros do serviço.</span><span class="sxs-lookup"><span data-stu-id="40a8b-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="40a8b-129">Observe que para o serviço escrever no diretório você deve ter certeza de que o processo em que o serviço está sendo executado (normalmente ASP.NET ou Serviço de Rede) tem permissão para escrever no diretório.</span><span class="sxs-lookup"><span data-stu-id="40a8b-129">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40a8b-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="40a8b-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="40a8b-131">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40a8b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="40a8b-132">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40a8b-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="40a8b-133">Certifique-se de ter criado o diretório c:\logs para o arquivo error.txt.</span><span class="sxs-lookup"><span data-stu-id="40a8b-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="40a8b-134">Ou modificar o nome `CalculatorErrorHandler.HandleError`do arquivo usado em .</span><span class="sxs-lookup"><span data-stu-id="40a8b-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="40a8b-135">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40a8b-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40a8b-136">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="40a8b-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40a8b-137">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="40a8b-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="40a8b-138">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="40a8b-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40a8b-139">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="40a8b-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
