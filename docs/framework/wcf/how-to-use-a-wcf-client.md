---
title: Como utilizar o cliente do Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d9d2fb363aa753edc6d2d4002a948fbb35b75ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="36491-102">Como utilizar o cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="36491-102">How to: Use a Windows Communication Foundation Client</span></span>
<span data-ttu-id="36491-103">Este é o último dos seis tarefas necessárias para criar um basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="36491-103">This is the last of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="36491-104">Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="36491-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="36491-105">Uma vez um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy foi criado e configurado, pode ser criada uma instância do cliente e o aplicativo cliente pode ser compilado e usado para se comunicar com o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="36491-105">Once a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy has been created and configured, a client instance can be created and the client application can be compiled and used to communicate with the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="36491-106">Este tópico descreve procedimentos para criar uma instância e usar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="36491-106">This topic describes procedures for instantiating and using a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="36491-107">Este procedimento faz três coisas:</span><span class="sxs-lookup"><span data-stu-id="36491-107">This procedure does three things:</span></span>  
  
1.  <span data-ttu-id="36491-108">Cria um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="36491-108">Instantiates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
2.  <span data-ttu-id="36491-109">Chama as operações de serviço do proxy gerado.</span><span class="sxs-lookup"><span data-stu-id="36491-109">Calls the service operations from the generated proxy.</span></span>  
  
3.  <span data-ttu-id="36491-110">Fecha o cliente após a conclusão da chamada da operação.</span><span class="sxs-lookup"><span data-stu-id="36491-110">Closes the client once the operation call is completed.</span></span>  
  
### <a name="to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="36491-111">Para usar um cliente Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="36491-111">To use a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="36491-112">Abra o arquivo Program.cs. vb ou do projeto GettingStartedClient e substitua o código existente pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="36491-112">Open the Program.cs or Program.vb file from the GettingStartedClient project and replace the existing code with the following code:</span></span>  
  
    ```  
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
  
    ```  
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
  
     <span data-ttu-id="36491-113">Observe a instrução usando ou importações que importa o GettingStartedClient.ServiceReference1.</span><span class="sxs-lookup"><span data-stu-id="36491-113">Notice the using or imports statement that imports the GettingStartedClient.ServiceReference1.</span></span> <span data-ttu-id="36491-114">Isso importa o código gerado pelo Adicionar referência de serviço no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36491-114">This imports the code generated by Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="36491-115">O código instancia o proxy do WCF e, em seguida, chama cada uma das operações de serviço expostas pelo serviço de cálculo, fecha o proxy e termina.</span><span class="sxs-lookup"><span data-stu-id="36491-115">The code instantiates the WCF proxy and then calls each of the service operations exposed by the calculator service, closes the proxy and terminates.</span></span>  
  
 <span data-ttu-id="36491-116">Agora você concluiu o tutorial.</span><span class="sxs-lookup"><span data-stu-id="36491-116">You have now completed the tutorial.</span></span> <span data-ttu-id="36491-117">É definido um contrato de serviço, implementado o contrato de serviço, gerado um proxy WCF, configurado um aplicativo cliente WCF e usado, em seguida, o proxy para chamar operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="36491-117">You defined a service contract, implemented the service contract, generated a WCF proxy, configured a WCF client application, and then used the proxy to call service operations.</span></span> <span data-ttu-id="36491-118">Para testar o aplicativo, primeiro execute GettingStartedHost para iniciar o serviço e, em seguida, executar GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="36491-118">To test out the application first run GettingStartedHost to start the service and then run GettingStartedClient.</span></span> <span data-ttu-id="36491-119">A saída de GettingStartedHost deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="36491-119">The output from GettingStartedHost should look like this:</span></span>  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 <span data-ttu-id="36491-120">A saída de GettingStartedClient deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="36491-120">The output from GettingStartedClient should look like this:</span></span>  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a><span data-ttu-id="36491-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36491-121">See Also</span></span>  
 <span data-ttu-id="36491-122">[Building Clients](../../../docs/framework/wcf/building-clients.md) (Compilando clientes)</span><span class="sxs-lookup"><span data-stu-id="36491-122">[Building Clients](../../../docs/framework/wcf/building-clients.md)</span></span>  
 <span data-ttu-id="36491-123">[How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md) (Como criar um cliente)</span><span class="sxs-lookup"><span data-stu-id="36491-123">[How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)</span></span>  
 [<span data-ttu-id="36491-124">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="36491-124">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
 <span data-ttu-id="36491-125">[Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md) (Programação básica do WCF)</span><span class="sxs-lookup"><span data-stu-id="36491-125">[Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md)</span></span>  
 [<span data-ttu-id="36491-126">Como: criar um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="36491-126">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="36491-127">Como: acessar serviços com um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="36491-127">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="36491-128">Introdução</span><span class="sxs-lookup"><span data-stu-id="36491-128">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="36491-129">Hospedagem interna</span><span class="sxs-lookup"><span data-stu-id="36491-129">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
