---
title: Evitando problemas com a instrução Using
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd3065a21c1714b0643bfb87b731193d3367352f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="0ea03-102">Evitando problemas com a instrução Using</span><span class="sxs-lookup"><span data-stu-id="0ea03-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="0ea03-103">Este exemplo demonstra como você não deve usar o c# "using" instrução para limpar automaticamente os recursos ao usar um cliente tipado.</span><span class="sxs-lookup"><span data-stu-id="0ea03-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="0ea03-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="0ea03-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0ea03-105">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="0ea03-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ea03-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0ea03-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0ea03-107">Este exemplo mostra dois problemas comuns que ocorrem ao usar o c# "using" instrução com clientes com tipo, bem como código que limpa corretamente depois de exceções.</span><span class="sxs-lookup"><span data-stu-id="0ea03-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="0ea03-108">A instrução "using" c# resulta em uma chamada para `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="0ea03-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="0ea03-109">Isso é o mesmo que `Close`(), que pode gerar exceções quando ocorre um erro de rede.</span><span class="sxs-lookup"><span data-stu-id="0ea03-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="0ea03-110">Porque a chamada para `Dispose`() é inerente na chave de fechamento do bloco "using", essa fonte de exceções é provavelmente ir despercebidos por pessoas escrever o código e o código de leitura.</span><span class="sxs-lookup"><span data-stu-id="0ea03-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="0ea03-111">Isso representa uma fonte em potencial de erros de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0ea03-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="0ea03-112">O primeiro problema ilustrado no `DemonstrateProblemUsingCanThrow` método, é que a chave de fechamento lança uma exceção e o código depois que a chave de fechamento não são executadas:</span><span class="sxs-lookup"><span data-stu-id="0ea03-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="0ea03-113">Mesmo se nada dentro de usando bloquear lançará uma exceção ou todas as exceções dentro de usando bloco são detectados, o `Console.Writeline` pode não acontecer porque o implícita `Dispose`chamada () em que a chave de fechamento pode lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0ea03-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="0ea03-114">O segundo problema ilustrado no `DemonstrateProblemUsingCanThrowAndMask` , é outra implicação a chave de fechamento lançar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="0ea03-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="0ea03-115">Porque o `Dispose`() ocorre dentro de um bloco "finally", o `ApplicationException` nunca é visto fora do usando bloquear se o `Dispose`falhar ().</span><span class="sxs-lookup"><span data-stu-id="0ea03-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="0ea03-116">Se o código fora deve saber sobre quando o `ApplicationException` ocorre, a construção "using" pode causar problemas mascarando essa exceção.</span><span class="sxs-lookup"><span data-stu-id="0ea03-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="0ea03-117">Por fim, o exemplo demonstra como limpar corretamente quando as exceções ocorrem em `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="0ea03-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="0ea03-118">Isso usa um bloco try/catch para relatar erros e chamada `Abort`.</span><span class="sxs-lookup"><span data-stu-id="0ea03-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="0ea03-119">Consulte o [esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemplo para obter mais detalhes sobre como capturar exceções de chamadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="0ea03-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="0ea03-120">O usando a instrução e o ServiceHost: muitos aplicativos de hospedagem interna pouco mais de um serviço de host e ServiceHost.Close raramente lança uma exceção, para que esses aplicativos podem usar com segurança o usando a instrução com ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="0ea03-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="0ea03-121">No entanto, lembre-se de que ServiceHost.Close pode lançar um `CommunicationException`, portanto, se seu aplicativo continua depois de fechar o ServiceHost, você deve evitar o uso de instrução e seguem o padrão fornecido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0ea03-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="0ea03-122">Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="0ea03-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="0ea03-123">O processo de cliente é executado três cenários, cada um dos quais tentativas de chamar `Divide`.</span><span class="sxs-lookup"><span data-stu-id="0ea03-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="0ea03-124">O primeiro cenário demonstra o código que está sendo ignorado devido a uma exceção de `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="0ea03-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="0ea03-125">O segundo cenário demonstra uma exceção importante que está sendo mascarada devido a uma exceção de `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="0ea03-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="0ea03-126">O terceiro cenário demonstra correto de limpeza.</span><span class="sxs-lookup"><span data-stu-id="0ea03-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="0ea03-127">A saída esperada do processo de cliente é:</span><span class="sxs-lookup"><span data-stu-id="0ea03-127">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0ea03-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0ea03-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0ea03-129">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ea03-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0ea03-130">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ea03-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0ea03-131">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ea03-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ea03-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0ea03-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0ea03-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0ea03-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0ea03-134">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0ea03-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ea03-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0ea03-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="0ea03-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ea03-136">See Also</span></span>
