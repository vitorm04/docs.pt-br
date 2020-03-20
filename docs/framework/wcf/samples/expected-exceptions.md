---
title: Exceções esperadas
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144703"
---
# <a name="expected-exceptions"></a><span data-ttu-id="b8592-102">Exceções esperadas</span><span class="sxs-lookup"><span data-stu-id="b8592-102">Expected Exceptions</span></span>
<span data-ttu-id="b8592-103">Esta amostra demonstra como capturar exceções esperadas ao usar um cliente digitado.</span><span class="sxs-lookup"><span data-stu-id="b8592-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="b8592-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="b8592-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="b8592-105">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="b8592-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8592-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b8592-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b8592-107">Esta amostra demonstra a captura e o manuseio dos dois `TimeoutException` `CommunicationException`tipos de exceção esperados que os programas corretos devem lidar: e .</span><span class="sxs-lookup"><span data-stu-id="b8592-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="b8592-108">Exceções que são lançadas de métodos de comunicação em um cliente WCF (Windows Communication Foundation) são esperadas ou inesperadas.</span><span class="sxs-lookup"><span data-stu-id="b8592-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="b8592-109">Exceções inesperadas incluem `OutOfMemoryException` falhas catastróficas `ArgumentNullException` `InvalidOperationException`como e erros de programação como ou .</span><span class="sxs-lookup"><span data-stu-id="b8592-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="b8592-110">Normalmente, não há uma maneira útil de lidar com erros inesperados, então normalmente você não deve pegá-los ao chamar um método de comunicação do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="b8592-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="b8592-111">As exceções esperadas dos métodos `TimeoutException`de `CommunicationException`comunicação em um `CommunicationException`cliente WCF incluem , e qualquer classe derivada de .</span><span class="sxs-lookup"><span data-stu-id="b8592-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="b8592-112">Estes indicam um problema durante a comunicação que pode ser tratado com segurança abortando o cliente WCF e relatando uma falha de comunicação.</span><span class="sxs-lookup"><span data-stu-id="b8592-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="b8592-113">Como fatores externos podem causar esses erros em qualquer aplicação, os aplicativos corretos devem capturar essas exceções e recuperar quando ocorrem.</span><span class="sxs-lookup"><span data-stu-id="b8592-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="b8592-114">Existem várias classes `CommunicationException` derivadas que um cliente pode jogar.</span><span class="sxs-lookup"><span data-stu-id="b8592-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="b8592-115">Em alguns casos, os aplicativos também pegam alguns desses para fazer um `CommunicationException`tratamento especial, mas deixam que os outros sejam tratados como um .</span><span class="sxs-lookup"><span data-stu-id="b8592-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="b8592-116">Isso pode ser feito capturando o tipo `CommunicationException` de exceção mais específico primeiro e, em seguida, capturando em uma cláusula de captura posterior.</span><span class="sxs-lookup"><span data-stu-id="b8592-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="b8592-117">O código que chama um `TimeoutException` método `CommunicationException`de comunicação do cliente deve pegar o e .</span><span class="sxs-lookup"><span data-stu-id="b8592-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="b8592-118">Uma maneira de lidar com tais erros é abortar o cliente e relatar a falha de comunicação.</span><span class="sxs-lookup"><span data-stu-id="b8592-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="b8592-119">Se ocorrer uma exceção esperada, o cliente pode ou não ser utilizável depois.</span><span class="sxs-lookup"><span data-stu-id="b8592-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="b8592-120">Para determinar se o cliente ainda está `State` utilizável, verifique se a propriedade é `CommunicationState`. Aberto.</span><span class="sxs-lookup"><span data-stu-id="b8592-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="b8592-121">Se ainda está aberto, então ainda é utilizável.</span><span class="sxs-lookup"><span data-stu-id="b8592-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="b8592-122">Caso contrário, você deve abortar o cliente e liberar todas as referências a ele.</span><span class="sxs-lookup"><span data-stu-id="b8592-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b8592-123">Você pode observar que os clientes que têm uma sessão muitas vezes não são mais utilizáveis após uma exceção, e os clientes que não têm uma sessão muitas vezes ainda são utilizáveis após uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b8592-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="b8592-124">No entanto, nenhum deles é garantido, portanto, se você quiser tentar continuar `State` usando o cliente após uma exceção, seu aplicativo deve verificar o imóvel para verificar se o cliente ainda está aberto.</span><span class="sxs-lookup"><span data-stu-id="b8592-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="b8592-125">Quando você executa a amostra, as respostas e exceções da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="b8592-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="b8592-126">O processo do cliente executa dois `Add` cenários, cada um dos quais tenta chamar seguido de `Divide`.</span><span class="sxs-lookup"><span data-stu-id="b8592-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="b8592-127">O primeiro cenário simula um problema de rede abortando o cliente antes de fazer a chamada para `Divide`.</span><span class="sxs-lookup"><span data-stu-id="b8592-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="b8592-128">O segundo cenário causa uma condição de tempo, definindo o tempo curto demais para o método ser concluído.</span><span class="sxs-lookup"><span data-stu-id="b8592-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="b8592-129">A saída esperada do processo do cliente é:</span><span class="sxs-lookup"><span data-stu-id="b8592-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8592-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b8592-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b8592-131">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8592-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b8592-132">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8592-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b8592-133">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8592-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b8592-134">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b8592-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8592-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b8592-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b8592-136">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b8592-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8592-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b8592-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
