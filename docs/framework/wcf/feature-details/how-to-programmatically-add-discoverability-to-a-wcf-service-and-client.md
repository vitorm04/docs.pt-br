---
title: Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: bf89c793cbd72a0a3980e6ec8e42c688dcedec26
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344972"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="f407b-102">Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="f407b-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="f407b-103">Este tópico explica como tornar um serviço da Windows Communication Foundation (WCF) descoberto.</span><span class="sxs-lookup"><span data-stu-id="f407b-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="f407b-104">É baseado na amostra [self-host.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host)</span><span class="sxs-lookup"><span data-stu-id="f407b-104">It is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="f407b-105">Para configurar a amostra de serviço self-host existente para o Discovery</span><span class="sxs-lookup"><span data-stu-id="f407b-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="f407b-106">Abra a solução Self-Host no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f407b-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="f407b-107">A amostra está localizada no diretório TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="f407b-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="f407b-108">Adicione uma `System.ServiceModel.Discovery.dll` referência ao projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="f407b-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="f407b-109">Você pode ver uma mensagem de erro dizendo "Sistema.</span><span class="sxs-lookup"><span data-stu-id="f407b-109">You may see an error message saying "System.</span></span> <span data-ttu-id="f407b-110">ServiceModel.Discovery.dll ou uma de suas dependências requer uma versão posterior do .NET Framework do que a especificada no projeto ..." Se você vir esta mensagem, clique com o botão direito do mouse no projeto no Solution Explorer e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f407b-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="f407b-111">Na janela Propriedades do **projeto,** certifique-se de que a **estrutura de destino** é [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f407b-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="f407b-112">Abra o arquivo Service.cs `using` e adicione a seguinte declaração.</span><span class="sxs-lookup"><span data-stu-id="f407b-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="f407b-113">No `Main()` método, dentro `using` da declaração, adicione uma <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância ao host de serviço.</span><span class="sxs-lookup"><span data-stu-id="f407b-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
  
            // ...  
        }  
    }  
    ```  
  
     <span data-ttu-id="f407b-114">O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> especificaque que o serviço a que é aplicado é descoberto.</span><span class="sxs-lookup"><span data-stu-id="f407b-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="f407b-115">Adicione <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a ao host de serviço logo <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>após o código que adiciona o .</span><span class="sxs-lookup"><span data-stu-id="f407b-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="f407b-116">Este código especifica que as mensagens de detecção devem ser enviadas para o ponto final de detecção udp padrão.</span><span class="sxs-lookup"><span data-stu-id="f407b-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="f407b-117">Para criar um aplicativo cliente que usa a descoberta para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="f407b-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="f407b-118">Adicione um novo aplicativo de `DiscoveryClientApp`console à solução chamada .</span><span class="sxs-lookup"><span data-stu-id="f407b-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="f407b-119">Adicione uma `System.ServiceModel.dll` referência e`System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="f407b-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="f407b-120">Copie os arquivos GeneratedClient.cs e App.config do projeto cliente existente para o novo projeto DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="f407b-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="f407b-121">Para isso, clique com o botão direito do mouse nos arquivos do **Solution Explorer**, selecione **Copiar**e selecione o projeto **DiscoveryClientApp,** clique com o botão direito do mouse e **selecione Colar**.</span><span class="sxs-lookup"><span data-stu-id="f407b-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="f407b-122">Abra Program.cs.</span><span class="sxs-lookup"><span data-stu-id="f407b-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="f407b-123">Adicione as seguintes declarações de `using`.</span><span class="sxs-lookup"><span data-stu-id="f407b-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="f407b-124">Adicione um método `FindCalculatorServiceAddress()` estático chamado à `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="f407b-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="f407b-125">Este método usa a `CalculatorService` descoberta para procurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f407b-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="f407b-126">Dentro `FindCalculatorServiceAddress` do método, <xref:System.ServiceModel.Discovery.DiscoveryClient> crie uma nova <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> instância, passando em um para o construtor.</span><span class="sxs-lookup"><span data-stu-id="f407b-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="f407b-127">Isso diz ao <xref:System.ServiceModel.Discovery.DiscoveryClient> WCF que a classe deve usar o ponto final de descoberta udp padrão para enviar e receber mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f407b-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="f407b-128">Na próxima linha, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ligue para <xref:System.ServiceModel.Discovery.FindCriteria> o método e especifique uma instância que contenha o contrato de serviço que você deseja procurar.</span><span class="sxs-lookup"><span data-stu-id="f407b-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="f407b-129">Neste caso, `ICalculator`especifique .</span><span class="sxs-lookup"><span data-stu-id="f407b-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="f407b-130">Após a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>chamada para , verifique se há pelo menos <xref:System.ServiceModel.EndpointAddress> um serviço correspondente e devolva o primeiro serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="f407b-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="f407b-131">Caso contrário, retorne `null`.</span><span class="sxs-lookup"><span data-stu-id="f407b-131">Otherwise return `null`.</span></span>  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. <span data-ttu-id="f407b-132">Adicione um método `InvokeCalculatorService` estático nomeado à `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="f407b-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="f407b-133">Este método usa o endereço `FindCalculatorServiceAddress` de ponto final retornado para chamar o serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="f407b-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="f407b-134">Dentro `InvokeCalculatorService` do método, crie `CalculatorServiceClient` uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="f407b-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="f407b-135">Esta classe é definida pela amostra [Self-Host.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host)</span><span class="sxs-lookup"><span data-stu-id="f407b-135">This class is defined by the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span> <span data-ttu-id="f407b-136">Foi gerado usando Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="f407b-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="f407b-137">Na próxima linha, defina o endereço de ponto final do `FindCalculatorServiceAddress()`cliente para o endereço de ponto final retornado de .</span><span class="sxs-lookup"><span data-stu-id="f407b-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="f407b-138">Imediatamente após o código da etapa anterior, chame os métodos expostos pelo serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="f407b-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. <span data-ttu-id="f407b-139">Adicione código `Main()` ao método `Program` na `FindCalculatorServiceAddress`classe para chamar .</span><span class="sxs-lookup"><span data-stu-id="f407b-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="f407b-140">Na próxima linha, `InvokeCalculatorService()` ligue para o e passe `FindCalculatorServiceAddress()`no endereço final retornado de .</span><span class="sxs-lookup"><span data-stu-id="f407b-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="f407b-141">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f407b-141">To test the application</span></span>  
  
1. <span data-ttu-id="f407b-142">Abra um prompt de comando elevado e execute Service.exe.</span><span class="sxs-lookup"><span data-stu-id="f407b-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="f407b-143">Abra um prompt de comando e execute Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="f407b-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="f407b-144">A saída do service.exe deve parecer com a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="f407b-144">The output from service.exe should look like the following output.</span></span>  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. <span data-ttu-id="f407b-145">A saída do Discoveryclientapp.exe deve parecer com a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="f407b-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="f407b-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f407b-146">Example</span></span>  
 <span data-ttu-id="f407b-147">A seguir está uma lista do código para esta amostra.</span><span class="sxs-lookup"><span data-stu-id="f407b-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="f407b-148">Como este código é baseado na amostra [self-host,](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) apenas os arquivos que são alterados são listados.</span><span class="sxs-lookup"><span data-stu-id="f407b-148">Because this code is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="f407b-149">Para obter mais informações sobre a amostra auto-host, consulte [Instruções de configuração](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span><span class="sxs-lookup"><span data-stu-id="f407b-149">For more information about the Self-Host sample, see [Setup Instructions](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="f407b-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="f407b-150">See also</span></span>

- [<span data-ttu-id="f407b-151">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="f407b-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="f407b-152">Modelo de objeto de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="f407b-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
