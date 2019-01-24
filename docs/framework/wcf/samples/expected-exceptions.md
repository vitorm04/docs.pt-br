---
title: Exceções esperadas
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: ff4241d6843158d859efbb010f165b27f5477286
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539617"
---
# <a name="expected-exceptions"></a><span data-ttu-id="cbcb6-102">Exceções esperadas</span><span class="sxs-lookup"><span data-stu-id="cbcb6-102">Expected Exceptions</span></span>
<span data-ttu-id="cbcb6-103">Este exemplo demonstra como capturar exceções esperadas, ao usar um cliente com tipo.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="cbcb6-104">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="cbcb6-105">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cbcb6-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbcb6-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cbcb6-107">Este exemplo demonstra a captura e tratando os dois tipos de exceção esperada que corrija programas deve tratar: `TimeoutException` e `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="cbcb6-108">As exceções que são geradas de métodos de comunicação em um cliente do Windows Communication Foundation (WCF) são esperados ou inesperados.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="cbcb6-109">Exceções inesperadas incluem falhas catastróficas semelhante `OutOfMemoryException` e, como erros de programação `ArgumentNullException` ou `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="cbcb6-110">Normalmente não há nenhuma maneira útil para lidar com erros inesperados, normalmente que você não deverá capturá-las ao chamar um método de comunicação de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="cbcb6-111">Esperado incluem exceções a partir de métodos de comunicação em um cliente WCF `TimeoutException`, `CommunicationException`, e qualquer classe derivada de `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="cbcb6-112">Elas indicam um problema durante a comunicação que pode ser manipulada com segurança, anulando o cliente WCF e relatando uma falha de comunicação.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="cbcb6-113">Como fatores externos podem causar esses erros em qualquer aplicativo, aplicativos corretos devem capturar essas exceções e recuperar quando eles ocorrerem.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="cbcb6-114">Há várias classes derivadas de `CommunicationException` que um cliente pode lançar.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="cbcb6-115">Em alguns casos, aplicativos também capturar alguns deles execute manipulação especial, mas permitir que os outros ser tratado como um `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="cbcb6-116">Isso pode ser feito capturando o tipo de exceção mais específico primeiro e, em seguida, capturando `CommunicationException` em uma cláusula catch posterior.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="cbcb6-117">Código que chama um método de comunicação do cliente deve capturar as `TimeoutException` e `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="cbcb6-118">É uma maneira de tratar esses erros anular o cliente e relatar a falha de comunicação.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="cbcb6-119">Se ocorrer uma exceção esperada, o cliente pode ou não pode ser usado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="cbcb6-120">Para determinar se o cliente ainda é utilizável, verifique se o `State` é de propriedade `CommunicationState`. Aberto.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="cbcb6-121">Se ainda estiver aberto, é ainda podem ser usado.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="cbcb6-122">Caso contrário, você deve anular o cliente e liberar todas as referências a ele.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cbcb6-123">Você pode observar que os clientes que possuem uma sessão geralmente não serão úteis após uma exceção, e os clientes que não têm uma sessão geralmente ainda serão úteis após uma exceção.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="cbcb6-124">No entanto, nenhuma delas é garantida, isso se você quiser tentar continuar usando o cliente após uma exceção de seu aplicativo deve verificar o `State` propriedade para verificar se o cliente ainda está aberta.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="cbcb6-125">Quando você executar o exemplo, as exceções e respostas de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="cbcb6-126">O processo de cliente é executado em dois cenários, cada um dos quais tentativas de chamar `Add` seguido por `Divide`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="cbcb6-127">O primeiro cenário simula um problema de rede, anulando o cliente antes de fazer a chamada para `Divide`.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="cbcb6-128">O segundo cenário faz com que uma condição de tempo limite, definindo o tempo limite muito curto para o método ser concluído.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="cbcb6-129">A saída esperada do processo de cliente é:</span><span class="sxs-lookup"><span data-stu-id="cbcb6-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cbcb6-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cbcb6-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cbcb6-131">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbcb6-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cbcb6-132">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbcb6-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cbcb6-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbcb6-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbcb6-134">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cbcb6-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cbcb6-136">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cbcb6-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cbcb6-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="cbcb6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbcb6-138">See also</span></span>
