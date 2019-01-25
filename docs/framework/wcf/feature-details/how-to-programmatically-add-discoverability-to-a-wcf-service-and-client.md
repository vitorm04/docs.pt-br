---
title: 'Como: Adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: a0240d09c07a23c2c578008885e5bca00169acdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643124"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="1bba6-102">Como: Adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="1bba6-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="1bba6-103">Este tópico explica como criar um serviço do Windows Communication Foundation (WCF) podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="1bba6-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="1bba6-104">Ele se baseia a [auto-hospedar](https://go.microsoft.com/fwlink/?LinkId=145523) exemplo.</span><span class="sxs-lookup"><span data-stu-id="1bba6-104">It is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="1bba6-105">Para configurar a amostra existente do serviço de hospedagem interna para descoberta</span><span class="sxs-lookup"><span data-stu-id="1bba6-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="1bba6-106">Abra a solução de hospedagem interna no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1bba6-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="1bba6-107">O exemplo está localizado no diretório TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="1bba6-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="1bba6-108">Adicione uma referência ao `System.ServiceModel.Discovery.dll` ao projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="1bba6-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="1bba6-109">Você poderá ver uma mensagem de erro dizendo "System.</span><span class="sxs-lookup"><span data-stu-id="1bba6-109">You may see an error message saying "System.</span></span> <span data-ttu-id="1bba6-110">ServiceModel.Discovery.dll ou uma de suas dependências requer uma versão posterior do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] daquele especificado no projeto... " Se você vir essa mensagem, clique com botão direito no projeto no Gerenciador de soluções e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1bba6-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="1bba6-111">No **propriedades do projeto** janela, certifique-se de que o **estrutura de destino** é [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1bba6-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="1bba6-112">Abra o arquivo Service.cs e adicione o seguinte `using` instrução.</span><span class="sxs-lookup"><span data-stu-id="1bba6-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="1bba6-113">No `Main()` método, dentro de `using` instrução, adicionar um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância ao host de serviço.</span><span class="sxs-lookup"><span data-stu-id="1bba6-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="1bba6-114">O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Especifica que o serviço for aplicado a é detectável.</span><span class="sxs-lookup"><span data-stu-id="1bba6-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="1bba6-115">Adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> para o host de serviço logo após o código que adiciona o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1bba6-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="1bba6-116">Esse código especifica que as mensagens de descoberta devem ser enviadas para o ponto de extremidade de descoberta UDP padrão.</span><span class="sxs-lookup"><span data-stu-id="1bba6-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="1bba6-117">Para criar um aplicativo cliente que usa a descoberta para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="1bba6-117">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="1bba6-118">Adicionar um novo aplicativo de console à solução chamado `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="1bba6-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="1bba6-119">Adicione uma referência ao `System.ServiceModel.dll` e `System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="1bba6-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="1bba6-120">Copie os arquivos GeneratedClient.cs e App. config do projeto de cliente existentes para o novo projeto DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="1bba6-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="1bba6-121">Para fazer isso, clique com botão direito os arquivos a **Gerenciador de soluções**, selecione **cópia**e, em seguida, selecione o **DiscoveryClientApp** do projeto, clique com botão direito e selecione **Colar**.</span><span class="sxs-lookup"><span data-stu-id="1bba6-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="1bba6-122">Abra Module.vb.</span><span class="sxs-lookup"><span data-stu-id="1bba6-122">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="1bba6-123">Adicione o seguinte `using` instruções.</span><span class="sxs-lookup"><span data-stu-id="1bba6-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="1bba6-124">Adicione um método estático chamado `FindCalculatorServiceAddress()` para o `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="1bba6-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="1bba6-125">Esse método usa a descoberta para pesquisar o `CalculatorService` service.</span><span class="sxs-lookup"><span data-stu-id="1bba6-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="1bba6-126">Dentro de `FindCalculatorServiceAddress` método, crie um novo <xref:System.ServiceModel.Discovery.DiscoveryClient> instância, passando um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> para o construtor.</span><span class="sxs-lookup"><span data-stu-id="1bba6-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="1bba6-127">Isso informa ao WCF que o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe deve usar o ponto de extremidade de descoberta UDP padrão para enviar e receber mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="1bba6-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="1bba6-128">Na próxima linha, chame o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método e especifique um <xref:System.ServiceModel.Discovery.FindCriteria> instância que contém o contrato de serviço que você deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="1bba6-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="1bba6-129">Nesse caso, especifique `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="1bba6-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="1bba6-130">Após a chamada para <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, verifique se há pelo menos um serviço correspondente e retornar o <xref:System.ServiceModel.EndpointAddress> do primeiro serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="1bba6-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="1bba6-131">Caso contrário, retornará `null`.</span><span class="sxs-lookup"><span data-stu-id="1bba6-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="1bba6-132">Adicionar um método estático denominado `InvokeCalculatorService` para o `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="1bba6-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="1bba6-133">Esse método usa o endereço do ponto de extremidade que retornado de `FindCalculatorServiceAddress` para chamar o serviço da Calculadora.</span><span class="sxs-lookup"><span data-stu-id="1bba6-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="1bba6-134">Dentro de `InvokeCalculatorService` método, crie uma instância da `CalculatorServiceClient` classe.</span><span class="sxs-lookup"><span data-stu-id="1bba6-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="1bba6-135">Essa classe é definida pelo [auto-hospedar](https://go.microsoft.com/fwlink/?LinkId=145523) exemplo.</span><span class="sxs-lookup"><span data-stu-id="1bba6-135">This class is defined by the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="1bba6-136">Ele foi gerado usando Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="1bba6-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="1bba6-137">Na próxima linha, defina o endereço do ponto de extremidade do cliente para o endereço do ponto de extremidade retornado de `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="1bba6-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="1bba6-138">Imediatamente após o código para a etapa anterior, chame os métodos expostos pelo serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="1bba6-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="1bba6-139">Adicione código para o `Main()` método na `Program` classe chamar `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="1bba6-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="1bba6-140">Na próxima linha, chame o `InvokeCalculatorService()` e passar o endereço do ponto de extremidade que retornado de `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="1bba6-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="1bba6-141">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="1bba6-141">To test the application</span></span>  
  
1.  <span data-ttu-id="1bba6-142">Abra um prompt de comando com privilégios elevados e execute Service.exe.</span><span class="sxs-lookup"><span data-stu-id="1bba6-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="1bba6-143">Abra um prompt de comando e execute Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="1bba6-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="1bba6-144">A saída do service.exe deve parecer com a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="1bba6-144">The output from service.exe should look like the following output.</span></span>  
  
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
  
4.  <span data-ttu-id="1bba6-145">A saída do Discoveryclientapp.exe deve parecer com a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="1bba6-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="1bba6-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bba6-146">Example</span></span>  
 <span data-ttu-id="1bba6-147">A seguir está uma listagem do código para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="1bba6-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="1bba6-148">Como esse código é baseado na [auto-hospedar](https://go.microsoft.com/fwlink/?LinkId=145523) exemplo, somente os arquivos que são alterados são listados.</span><span class="sxs-lookup"><span data-stu-id="1bba6-148">Because this code is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="1bba6-149">Para obter mais informações sobre o exemplo de hospedagem interna, consulte [instruções de instalação](https://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="1bba6-149">For more information about the Self-Host sample, see [Setup Instructions](https://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="1bba6-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bba6-150">See also</span></span>
- [<span data-ttu-id="1bba6-151">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="1bba6-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="1bba6-152">Modelo de objeto de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="1bba6-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
