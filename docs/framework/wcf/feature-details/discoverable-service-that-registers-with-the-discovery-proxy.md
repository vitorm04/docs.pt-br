---
title: Como implementar um serviço de descoberta que registra usando o proxy de descoberta
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: bf878dff59a9a258567ff99098b0b3f8761194e2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599224"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="685a7-102">Como implementar um serviço de descoberta que registra usando o proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="685a7-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>
<span data-ttu-id="685a7-103">Este tópico é o segundo de quatro tópicos que discute como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="685a7-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="685a7-104">No tópico anterior, [como implementar um proxy de descoberta](how-to-implement-a-discovery-proxy.md), você implementou um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="685a7-104">In the previous topic, [How to: Implement a Discovery Proxy](how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="685a7-105">Neste tópico, você cria um serviço WCF que envia mensagens de anúncio ( `Hello` e `Bye` ) para o proxy de descoberta, fazendo com que ele se registre e cancele seu registro com o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="685a7-105">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="685a7-106">Para definir o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="685a7-106">To define the service contract</span></span>

1. <span data-ttu-id="685a7-107">Adicione um novo projeto de aplicativo de console à `DiscoveryProxyExample` solução chamada `Service` .</span><span class="sxs-lookup"><span data-stu-id="685a7-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="685a7-108">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="685a7-108">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="685a7-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="685a7-109">System.ServiceModel</span></span>

    2. <span data-ttu-id="685a7-110">System. ServiceModel. Discovery</span><span class="sxs-lookup"><span data-stu-id="685a7-110">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="685a7-111">Adicione uma nova classe ao projeto chamado `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="685a7-111">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="685a7-112">Adicionar as seguintes instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="685a7-112">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="685a7-113">Em CalculatorService.cs, defina o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="685a7-113">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="685a7-114">Também em CalculatorService.cs, implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="685a7-114">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="685a7-115">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="685a7-115">To host the service</span></span>

1. <span data-ttu-id="685a7-116">Abra o arquivo Program.cs que foi gerado quando você criou o projeto.</span><span class="sxs-lookup"><span data-stu-id="685a7-116">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="685a7-117">Adicionar as seguintes instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="685a7-117">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="685a7-118">Dentro do `Main()` método, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="685a7-118">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="685a7-119">Você concluiu a implementação de um serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="685a7-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="685a7-120">Continue em [como: implementar um aplicativo cliente que usa o proxy de descoberta para encontrar um serviço](client-app-discovery-proxy-to-find-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="685a7-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="685a7-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="685a7-121">Example</span></span>
 <span data-ttu-id="685a7-122">Esta é a lista completa do código usado neste tópico.</span><span class="sxs-lookup"><span data-stu-id="685a7-122">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
// Program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="685a7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="685a7-123">See also</span></span>

- [<span data-ttu-id="685a7-124">Descoberta de WCF</span><span class="sxs-lookup"><span data-stu-id="685a7-124">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="685a7-125">Como implementar um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="685a7-125">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="685a7-126">Como implementar um aplicativo cliente que utiliza o proxy de descoberta para encontrar um serviço</span><span class="sxs-lookup"><span data-stu-id="685a7-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
