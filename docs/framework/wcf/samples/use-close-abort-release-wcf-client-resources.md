---
title: Usar Close e Abort para liberar recursos de cliente do WCF
description: Dispose pode falhar e gerar exceções quando a rede falhar. Isso pode causar comportamento indesejado. Em vez disso, use fechar e anular para liberar recursos do cliente quando a rede tiver falhado.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599913"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="15852-105">Fechar e anular a liberação de recursos com segurança quando as conexões de rede forem descartadas</span><span class="sxs-lookup"><span data-stu-id="15852-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="15852-106">Este exemplo demonstra como usar `Close` os `Abort` métodos e para limpar os recursos ao usar um cliente digitado.</span><span class="sxs-lookup"><span data-stu-id="15852-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="15852-107">A `using` instrução causa exceções quando a conexão de rede não é robusta.</span><span class="sxs-lookup"><span data-stu-id="15852-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="15852-108">Este exemplo é baseado no [introdução](getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="15852-108">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="15852-109">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="15852-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="15852-110">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="15852-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="15852-111">Este exemplo mostra dois dos problemas comuns que ocorrem ao usar a instrução C# "using" com clientes digitados, bem como o código que limpa corretamente após exceções.</span><span class="sxs-lookup"><span data-stu-id="15852-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="15852-112">A instrução C# "using" resulta em uma chamada para `Dispose` ().</span><span class="sxs-lookup"><span data-stu-id="15852-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="15852-113">Isso é o mesmo que `Close` (), que pode gerar exceções quando ocorre um erro de rede.</span><span class="sxs-lookup"><span data-stu-id="15852-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="15852-114">Como a chamada para `Dispose` () ocorre implicitamente na chave de fechamento do bloco "using", essa fonte de exceções provavelmente passará despercebida por pessoas que escrevem o código e lendo o código.</span><span class="sxs-lookup"><span data-stu-id="15852-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="15852-115">Isso representa uma possível fonte de erros de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="15852-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="15852-116">O primeiro problema, ilustrado no `DemonstrateProblemUsingCanThrow` método, é que a chave de fechamento gera uma exceção e o código após a chave de fechamento não é executado:</span><span class="sxs-lookup"><span data-stu-id="15852-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="15852-117">Mesmo que nada dentro do bloco Using gere uma exceção ou todas as exceções dentro do bloco Using sejam detectadas, o `Console.WriteLine` pode não acontecer porque a `Dispose` chamada implícita () na chave de fechamento pode gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="15852-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="15852-118">O segundo problema, ilustrado no `DemonstrateProblemUsingCanThrowAndMask` método, é outra implicação da chave de fechamento lançar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="15852-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="15852-119">Como o `Dispose` () ocorre dentro de um bloco "finally", o `ApplicationException` nunca é visto fora do bloco Using se o `Dispose` () falhar.</span><span class="sxs-lookup"><span data-stu-id="15852-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="15852-120">Se o código fora precisar saber sobre quando `ApplicationException` ocorre, a construção "using" poderá causar problemas mascarando essa exceção.</span><span class="sxs-lookup"><span data-stu-id="15852-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="15852-121">Por fim, o exemplo demonstra como limpar corretamente quando ocorrem exceções no `DemonstrateCleanupWithExceptions` .</span><span class="sxs-lookup"><span data-stu-id="15852-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="15852-122">Isso usa um bloco try/catch para relatar erros e chamar `Abort` .</span><span class="sxs-lookup"><span data-stu-id="15852-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="15852-123">Consulte o exemplo de [exceções esperadas](expected-exceptions.md) para obter mais detalhes sobre a captura de exceções de chamadas de cliente.</span><span class="sxs-lookup"><span data-stu-id="15852-123">See the [Expected Exceptions](expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

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
> <span data-ttu-id="15852-124">A instrução using e ServiceHost: muitos aplicativos de hospedagem interna fazem pouco mais do que hospedar um serviço, e ServiceHost. Close raramente gera uma exceção, de modo que esses aplicativos podem usar com segurança a instrução using com ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="15852-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="15852-125">No entanto, lembre-se de que ServiceHost. Close pode lançar um `CommunicationException` , portanto, se o seu aplicativo continuar depois de fechar o ServiceHost, você deverá evitar a instrução using e seguir o padrão fornecido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="15852-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="15852-126">Quando você executa o exemplo, as respostas e as exceções da operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="15852-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="15852-127">O processo do cliente executa três cenários, cada um dos quais tenta chamar `Divide` .</span><span class="sxs-lookup"><span data-stu-id="15852-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="15852-128">O primeiro cenário demonstra que o código está sendo ignorado devido a uma exceção de `Dispose` ().</span><span class="sxs-lookup"><span data-stu-id="15852-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="15852-129">O segundo cenário demonstra uma exceção importante sendo mascarada devido a uma exceção de `Dispose` ().</span><span class="sxs-lookup"><span data-stu-id="15852-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="15852-130">O terceiro cenário demonstra a limpeza correta.</span><span class="sxs-lookup"><span data-stu-id="15852-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="15852-131">A saída esperada do processo do cliente é:</span><span class="sxs-lookup"><span data-stu-id="15852-131">The expected output from the client process is:</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="15852-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="15852-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="15852-133">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15852-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="15852-134">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15852-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="15852-135">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15852-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15852-136">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="15852-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15852-137">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="15852-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="15852-138">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="15852-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15852-139">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="15852-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
