---
title: Use fechar e anular para liberar recursos de cliente do WCF
description: Dispose pode falhar e lançar exceções quando ocorre falha na rede. Isso pode causar um comportamento indesejado. Em vez disso, use fechar e anular para liberar recursos de cliente quando a falha da rede.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: d37ad9d2277fea2656311a5a1f57d51343d10d89
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147209"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="53936-105">Fechar e anular liberar recursos com segurança quando as conexões de rede tem sido descartado</span><span class="sxs-lookup"><span data-stu-id="53936-105">Close and Abort release resources safely when network connections have dropped</span></span>
<span data-ttu-id="53936-106">Este exemplo demonstra como usar o `Close` e `Abort` métodos para limpar os recursos ao usar um cliente com tipo.</span><span class="sxs-lookup"><span data-stu-id="53936-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="53936-107">O `using` instrução faz com que exceções quando a conexão de rede não é robusto.</span><span class="sxs-lookup"><span data-stu-id="53936-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="53936-108">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="53936-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="53936-109">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="53936-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53936-110">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="53936-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="53936-111">Este exemplo mostra dois dos problemas comuns que ocorrem ao usar o c# "using" de instrução com clientes com tipo, bem como código que limpa corretamente depois de exceções.</span><span class="sxs-lookup"><span data-stu-id="53936-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="53936-112">A instrução "using" c# resulta em uma chamada para `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="53936-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="53936-113">Isso é o mesmo que `Close`(), que pode gerar exceções quando ocorre um erro de rede.</span><span class="sxs-lookup"><span data-stu-id="53936-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="53936-114">Porque a chamada para `Dispose`() é inerente em que a chave de fechamento do bloco "using", essa fonte de exceções é provavelmente passar despercebidos por pessoas escrevendo o código e a leitura do código.</span><span class="sxs-lookup"><span data-stu-id="53936-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="53936-115">Isso representa uma possível fonte de erros de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53936-115">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="53936-116">O primeiro problema ilustrado no `DemonstrateProblemUsingCanThrow` método, é que a chave de fechamento lança uma exceção e o código, depois que a chave de fechamento não são executadas:</span><span class="sxs-lookup"><span data-stu-id="53936-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="53936-117">Mesmo se nada dentro do usando bloquear gera uma exceção ou todas as exceções dentro do usando o bloco são capturadas, o `Console.Writeline` não pode acontecer porque o implícita `Dispose`chamada () em que a chave de fechamento pode gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="53936-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="53936-118">O segundo problema ilustrado no `DemonstrateProblemUsingCanThrowAndMask` método, é outra implicação a lançar uma exceção de fechamento:</span><span class="sxs-lookup"><span data-stu-id="53936-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="53936-119">Porque o `Dispose`() ocorre dentro de um bloco "finally", o `ApplicationException` nunca é visto fora de usando bloqueie se o `Dispose`falhar ().</span><span class="sxs-lookup"><span data-stu-id="53936-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="53936-120">Se o código fora deve saber sobre quando o `ApplicationException` ocorre, a construção "using" pode causar problemas através do mascaramento essa exceção.</span><span class="sxs-lookup"><span data-stu-id="53936-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="53936-121">Por fim, o exemplo demonstra como limpar corretamente quando exceções ocorrem em `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="53936-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="53936-122">Isso usa um bloco try/catch para relatar erros e chamada `Abort`.</span><span class="sxs-lookup"><span data-stu-id="53936-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="53936-123">Consulte a [esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemplo para obter mais detalhes sobre como capturar exceções de chamadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="53936-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
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
>  <span data-ttu-id="53936-124">O usando a instrução e o ServiceHost: Muitos aplicativos de hospedagem interna pouco mais de um serviço de host e ServiceHost.Close raramente lança uma exceção, portanto, esses aplicativos podem usar com segurança o usando a instrução com o ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="53936-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="53936-125">No entanto, lembre-se de que ServiceHost.Close pode lançar um `CommunicationException`, portanto, se seu aplicativo continua depois de fechar o ServiceHost, você deve evitar o uso de instrução e siga o padrão fornecido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="53936-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="53936-126">Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="53936-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="53936-127">O processo de cliente é executado em três cenários, cada um dos quais tentativas de chamar `Divide`.</span><span class="sxs-lookup"><span data-stu-id="53936-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="53936-128">O primeiro cenário demonstra o código que está sendo ignorado devido a uma exceção de `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="53936-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="53936-129">O segundo cenário demonstra uma exceção importante que está sendo mascarada por causa de uma exceção de `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="53936-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="53936-130">O terceiro cenário demonstra correto de limpeza.</span><span class="sxs-lookup"><span data-stu-id="53936-130">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="53936-131">A saída esperada do processo de cliente é:</span><span class="sxs-lookup"><span data-stu-id="53936-131">The expected output from the client process is:</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="53936-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="53936-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="53936-133">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53936-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="53936-134">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53936-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="53936-135">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53936-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53936-136">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="53936-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53936-137">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="53936-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="53936-138">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="53936-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53936-139">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="53936-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="53936-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53936-140">See Also</span></span>
