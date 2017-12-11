---
title: "Controle estendido através de relatórios e tratamento de erro"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4284f07a21a9bb176a78a8a2abefe7c7c7c6b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="f2bd4-102">Controle estendido através de relatórios e tratamento de erro</span><span class="sxs-lookup"><span data-stu-id="f2bd4-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="f2bd4-103">Este exemplo demonstra como estender o controle sobre o tratamento de erros e o relatório de erros em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de serviço usando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-103">This sample demonstrates how to extend control over error handling and error reporting in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="f2bd4-104">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) com um código adicional adicionado ao serviço para manipular erros.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="f2bd4-105">O cliente força várias condições de erro.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-105">The client forces several error conditions.</span></span> <span data-ttu-id="f2bd4-106">O serviço intercepta os erros e registra em log em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2bd4-107">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f2bd4-108">Serviços podem interceptar erros, execute um processamento e afetam como os erros são relatados usando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="f2bd4-109">A interface tem dois métodos que podem ser implementados: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> e <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="f2bd4-110">O <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> método permite que você adicionar, modificar ou suprimir uma mensagem de falha é gerada em resposta a uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="f2bd4-111">O <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> método permite o processamento de erro ocorra no caso de controles e um erro se o tratamento de erro adicional pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="f2bd4-112">Neste exemplo, o `CalculatorErrorHandler` tipo implementa o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="f2bd4-113">No</span><span class="sxs-lookup"><span data-stu-id="f2bd4-113">In the</span></span>  
  
 <span data-ttu-id="f2bd4-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>método, o `CalculatorErrorHandler` grava um log do erro para um arquivo de texto txt em c:\Logs.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="f2bd4-115">Observe que o exemplo faz a falha e não suprime, permitindo que ele ser relatados de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
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
  
 <span data-ttu-id="f2bd4-116">O `ErrorBehaviorAttribute` existe como um mecanismo para registrar um manipulador de erro com um serviço.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="f2bd4-117">Esse atributo tem um parâmetro de tipo único.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="f2bd4-118">Se o tipo deve implementar o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface e deve ter um construtor público vazio.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="f2bd4-119">O atributo, em seguida, cria uma instância desse tipo de manipulador de erro e instala o serviço.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="f2bd4-120">Ele faz isso Implementando a <xref:System.ServiceModel.Description.IServiceBehavior> interface e, em seguida, usando o <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> método para adicionar instâncias do manipulador de erros para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
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
  
 <span data-ttu-id="f2bd4-121">O exemplo implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-121">The sample implements a calculator service.</span></span> <span data-ttu-id="f2bd4-122">O cliente deliberadamente gera dois erros no serviço, fornecendo os parâmetros com valores inválidos.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="f2bd4-123">O `CalculatorErrorHandler` usa o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface para registrar os erros em um arquivo local e, em seguida, permite que eles ser relatados de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="f2bd4-124">O cliente força uma divisão por zero e uma condição de argumento fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
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
  
 <span data-ttu-id="f2bd4-125">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f2bd4-126">Você verá a divisão por zero e as condições de argumento fora do intervalo que está sendo relatadas como falhas.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="f2bd4-127">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-127">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="f2bd4-128">O arquivo c:\logs\errors.txt contém as informações registradas sobre os erros pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="f2bd4-129">Observe que o serviço deve gravar no diretório você deve garantir que o processo sob a qual o serviço está em execução (normalmente ASP.NET ou serviço de rede), tem a permissão para gravar no diretório.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-129">Note that for the service to write to the directory you must make sure that the process under which the service is running, (typically ASP.NET or Network Service), has the permission to write to the directory.</span></span>  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f2bd4-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f2bd4-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f2bd4-131">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2bd4-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f2bd4-132">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2bd4-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f2bd4-133">Certifique-se de que você criou o diretório c:\Logs. para o arquivo txt.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="f2bd4-134">Ou modificar o nome de arquivo usado no `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4.  <span data-ttu-id="f2bd4-135">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2bd4-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2bd4-136">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2bd4-137">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f2bd4-138">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2bd4-139">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f2bd4-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a><span data-ttu-id="f2bd4-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2bd4-140">See Also</span></span>
