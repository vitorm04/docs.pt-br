---
title: Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 0685694db8f67ed690cf2a8002bf70a05695a192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="77d9c-102">Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="77d9c-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="77d9c-103">Este tópico explica como criar um serviço do Windows Communication Foundation (WCF) podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="77d9c-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="77d9c-104">Ele se baseia o [auto-host](http://go.microsoft.com/fwlink/?LinkId=145523) exemplo.</span><span class="sxs-lookup"><span data-stu-id="77d9c-104">It is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="77d9c-105">Para configurar a amostra existente do serviço de hospedagem interna para descoberta</span><span class="sxs-lookup"><span data-stu-id="77d9c-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="77d9c-106">Abra a solução de hospedagem interna em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d9c-106">Open the Self-Host solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="77d9c-107">O exemplo está localizado no diretório TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="77d9c-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="77d9c-108">Adicione uma referência a `System.ServiceModel.Discovery.dll` para o projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="77d9c-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="77d9c-109">Você verá uma mensagem de erro dizendo "System.</span><span class="sxs-lookup"><span data-stu-id="77d9c-109">You may see an error message saying "System.</span></span> <span data-ttu-id="77d9c-110">ServiceModel.Discovery.dll ou uma de suas dependências exige uma versão posterior do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] àquela especificada no projeto... "</span><span class="sxs-lookup"><span data-stu-id="77d9c-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …"</span></span> <span data-ttu-id="77d9c-111">Se você vir essa mensagem, clique com botão direito no projeto no Gerenciador de soluções e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="77d9c-111">If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="77d9c-112">No **propriedades do projeto** janela, verifique se o **Framework de destino** é [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d9c-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="77d9c-113">Abra o arquivo Service.cs e adicione o seguinte `using` instrução.</span><span class="sxs-lookup"><span data-stu-id="77d9c-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="77d9c-114">No `Main()` método, dentro de `using` instrução, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="77d9c-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="77d9c-115">O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Especifica que o serviço será aplicada a é detectável.</span><span class="sxs-lookup"><span data-stu-id="77d9c-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="77d9c-116">Adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> para o host de serviço logo após o código que adiciona o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="77d9c-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="77d9c-117">Esse código especifica que as mensagens de descoberta devem ser enviadas ao ponto de extremidade de descoberta UDP padrão.</span><span class="sxs-lookup"><span data-stu-id="77d9c-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="77d9c-118">Para criar um aplicativo cliente que usa a descoberta para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="77d9c-118">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="77d9c-119">Adicionar um novo aplicativo de console para a solução chamado `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="77d9c-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="77d9c-120">Adicione uma referência ao `System.ServiceModel.dll` e `System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="77d9c-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="77d9c-121">Copie os arquivos GeneratedClient.cs e App. config do projeto de cliente existente para o novo projeto DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="77d9c-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="77d9c-122">Para fazer isso, clique com botão direito os arquivos a **Solution Explorer**, selecione **cópia**e, em seguida, selecione o **DiscoveryClientApp** do projeto, clique com botão direito e selecione **Colar**.</span><span class="sxs-lookup"><span data-stu-id="77d9c-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="77d9c-123">Abra Module.vb.</span><span class="sxs-lookup"><span data-stu-id="77d9c-123">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="77d9c-124">Adicione o seguinte `using` instruções.</span><span class="sxs-lookup"><span data-stu-id="77d9c-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="77d9c-125">Adicionar um método estático chamado `FindCalculatorServiceAddress()` para o `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="77d9c-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="77d9c-126">Esse método usa a descoberta para pesquisar o `CalculatorService` service.</span><span class="sxs-lookup"><span data-stu-id="77d9c-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="77d9c-127">Dentro de `FindCalculatorServiceAddress` método, crie um novo <xref:System.ServiceModel.Discovery.DiscoveryClient> instância, passando um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> para o construtor.</span><span class="sxs-lookup"><span data-stu-id="77d9c-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="77d9c-128">Isso informa ao WCF que o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe deve usar o ponto de extremidade de descoberta padrão UDP para enviar e receber mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="77d9c-128">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="77d9c-129">Na próxima linha, chame o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método e especifique um <xref:System.ServiceModel.Discovery.FindCriteria> instância que contém o contrato de serviço que você deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="77d9c-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="77d9c-130">Nesse caso, especifique `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="77d9c-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="77d9c-131">Após a chamada a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, verifique se há pelo menos um serviço correspondente e retornar o <xref:System.ServiceModel.EndpointAddress> do primeiro serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="77d9c-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="77d9c-132">Caso contrário, retornará `null`.</span><span class="sxs-lookup"><span data-stu-id="77d9c-132">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="77d9c-133">Adicionar um método estático denominado `InvokeCalculatorService` para o `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="77d9c-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="77d9c-134">Esse método usa o endereço de ponto de extremidade retornado de `FindCalculatorServiceAddress` para chamar o serviço da Calculadora.</span><span class="sxs-lookup"><span data-stu-id="77d9c-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="77d9c-135">Dentro de `InvokeCalculatorService` método, crie uma instância do `CalculatorServiceClient` classe.</span><span class="sxs-lookup"><span data-stu-id="77d9c-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="77d9c-136">Essa classe é definida pelo [auto-host](http://go.microsoft.com/fwlink/?LinkId=145523) exemplo.</span><span class="sxs-lookup"><span data-stu-id="77d9c-136">This class is defined by the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="77d9c-137">Ele foi gerado usando Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="77d9c-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="77d9c-138">Na próxima linha, defina o endereço do ponto de extremidade do cliente para o endereço de ponto de extremidade retornado de `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="77d9c-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="77d9c-139">Imediatamente após o código para a etapa anterior, chame os métodos expostos pelo serviço do cálculo.</span><span class="sxs-lookup"><span data-stu-id="77d9c-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="77d9c-140">Adicione código para o `Main()` método o `Program` classe chamar `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="77d9c-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="77d9c-141">Na próxima linha, chame o `InvokeCalculatorService()` e passar o endereço de ponto de extremidade retornado de `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="77d9c-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="77d9c-142">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="77d9c-142">To test the application</span></span>  
  
1.  <span data-ttu-id="77d9c-143">Abra um prompt de comando com privilégios elevados e execute Service.exe.</span><span class="sxs-lookup"><span data-stu-id="77d9c-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="77d9c-144">Abra um prompt de comando e execute Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="77d9c-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="77d9c-145">A saída de service.exe deve parecer com a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="77d9c-145">The output from service.exe should look like the following output.</span></span>  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  <span data-ttu-id="77d9c-146">A saída de Discoveryclientapp.exe deve parecer com a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="77d9c-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="77d9c-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77d9c-147">Example</span></span>  
 <span data-ttu-id="77d9c-148">A seguir está uma listagem de código para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="77d9c-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="77d9c-149">Como esse código é baseado no [auto-host](http://go.microsoft.com/fwlink/?LinkId=145523) exemplo, são listados somente os arquivos que são alterados.</span><span class="sxs-lookup"><span data-stu-id="77d9c-149">Because this code is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="77d9c-150">Para obter mais informações sobre o próprio Host de exemplo, consulte [instruções de instalação](http://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="77d9c-150">For more information about the Self-Host sample, see [Setup Instructions](http://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="77d9c-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77d9c-151">See Also</span></span>  
 [<span data-ttu-id="77d9c-152">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="77d9c-152">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="77d9c-153">Modelo de objeto de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="77d9c-153">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
