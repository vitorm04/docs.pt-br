---
title: Como utilizar o cliente do Windows Communication Foundation
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 12e911fb899cb85121c129b762828cdda01e64f1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580207"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="4d73b-102">Como utilizar o cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4d73b-102">How to: Use a Windows Communication Foundation Client</span></span>

<span data-ttu-id="4d73b-103">Esta é a última das seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4d73b-103">This is the last of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4d73b-104">Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4d73b-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="4d73b-105">Depois que um proxy do Windows Communication Foundation (WCF) foi criado e configurado, uma instância do cliente pode ser criada e o aplicativo cliente pode ser compilado e usado para se comunicar com o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="4d73b-105">Once a Windows Communication Foundation (WCF) proxy has been created and configured, a client instance can be created and the client application can be compiled and used to communicate with the WCF service.</span></span> <span data-ttu-id="4d73b-106">Este tópico descreve procedimentos para instanciar e usar um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="4d73b-106">This topic describes procedures for instantiating and using a WCF client.</span></span> <span data-ttu-id="4d73b-107">Este procedimento faz três coisas:</span><span class="sxs-lookup"><span data-stu-id="4d73b-107">This procedure does three things:</span></span>

1.  <span data-ttu-id="4d73b-108">Cria uma instância de um cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="4d73b-108">Instantiates a WCF client.</span></span>

2.  <span data-ttu-id="4d73b-109">Chama as operações de serviço do proxy gerado.</span><span class="sxs-lookup"><span data-stu-id="4d73b-109">Calls the service operations from the generated proxy.</span></span>

3.  <span data-ttu-id="4d73b-110">Fecha o cliente depois que a chamada da operação é concluída.</span><span class="sxs-lookup"><span data-stu-id="4d73b-110">Closes the client once the operation call is completed.</span></span>

## <a name="use-a-windows-communication-foundation-client"></a><span data-ttu-id="4d73b-111">Usar um cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4d73b-111">Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="4d73b-112">Abra o arquivo Program.cs ou Program. vb do projeto GettingStartedClient e substitua o código existente pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="4d73b-112">Open the Program.cs or Program.vb file from the GettingStartedClient project and replace the existing code with the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            //Step 3: Closing the client gracefully closes the connection and cleans up resources.
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClientVB2.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy
        Dim Client As New CalculatorClient()

        'Step 2: Call the service operations.
        'Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        'Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        'Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        'Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Closing the client gracefully closes the connection and cleans up resources.
        Client.Close()

        Console.WriteLine()
        Console.WriteLine("Press <ENTER> to terminate client.")
        Console.ReadLine()

    End Sub

End Module
```

<span data-ttu-id="4d73b-113">Observe que o `using` ou `Imports` instrução que importa o `GettingStartedClient.ServiceReference1`.</span><span class="sxs-lookup"><span data-stu-id="4d73b-113">Notice the `using` or `Imports` statement that imports the `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="4d73b-114">Este importa o código gerado pelo **adicionar referência de serviço** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4d73b-114">This imports the code generated by **Add Service Reference** in Visual Studio.</span></span> <span data-ttu-id="4d73b-115">O código instancia o proxy do WCF e, em seguida, chama cada uma das operações de serviço expostas pelo serviço de Calculadora, fecha o proxy e será encerrado.</span><span class="sxs-lookup"><span data-stu-id="4d73b-115">The code instantiates the WCF proxy and then calls each of the service operations exposed by the calculator service, closes the proxy, and terminates.</span></span>

<span data-ttu-id="4d73b-116">Agora você concluiu o tutorial.</span><span class="sxs-lookup"><span data-stu-id="4d73b-116">You have now completed the tutorial.</span></span> <span data-ttu-id="4d73b-117">É definido um contrato de serviço, implementado o contrato de serviço, gerado de um proxy do WCF, configurado um aplicativo de cliente do WCF e usado, em seguida, o proxy para chamar operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="4d73b-117">You defined a service contract, implemented the service contract, generated a WCF proxy, configured a WCF client application, and then used the proxy to call service operations.</span></span> <span data-ttu-id="4d73b-118">Para testar o aplicativo, primeiro execute GettingStartedHost para iniciar o serviço e, em seguida, executar GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="4d73b-118">To test out the application, first run GettingStartedHost to start the service and then run GettingStartedClient.</span></span>

<span data-ttu-id="4d73b-119">A saída de um GettingStartedHost deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="4d73b-119">The output from GettingStartedHost should look like this:</span></span>

```text
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714
```

<span data-ttu-id="4d73b-120">A saída de GettingStartedClient deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="4d73b-120">The output from GettingStartedClient should look like this:</span></span>

```text
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.
```

## <a name="see-also"></a><span data-ttu-id="4d73b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d73b-121">See also</span></span>

- [<span data-ttu-id="4d73b-122">Compilando clientes</span><span class="sxs-lookup"><span data-stu-id="4d73b-122">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="4d73b-123">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="4d73b-123">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="4d73b-124">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="4d73b-124">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="4d73b-125">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="4d73b-125">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="4d73b-126">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="4d73b-126">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="4d73b-127">Como acessar serviços com um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="4d73b-127">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="4d73b-128">Introdução</span><span class="sxs-lookup"><span data-stu-id="4d73b-128">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="4d73b-129">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="4d73b-129">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)