---
title: Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: e32128a20a765762249e6892232447c56036c2d8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524134"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF
Este tópico explica como criar um serviço do Windows Communication Foundation (WCF) podem ser descobertos. Ele se baseia a [auto-hospedar](https://go.microsoft.com/fwlink/?LinkId=145523) exemplo.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Para configurar a amostra existente do serviço de hospedagem interna para descoberta  
  
1.  Abra a solução de hospedagem interna em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. O exemplo está localizado no diretório TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2.  Adicione uma referência ao `System.ServiceModel.Discovery.dll` ao projeto de serviço. Você poderá ver uma mensagem de erro dizendo "System. ServiceModel.Discovery.dll ou uma de suas dependências requer uma versão posterior do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] daquele especificado no projeto... " Se você vir essa mensagem, clique com botão direito no projeto no Gerenciador de soluções e escolha **propriedades**. No **propriedades do projeto** janela, certifique-se de que o **estrutura de destino** é [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3.  Abra o arquivo Service.cs e adicione o seguinte `using` instrução.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  No `Main()` método, dentro de `using` instrução, adicionar um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância ao host de serviço.  
  
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
  
     O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Especifica que o serviço for aplicado a é detectável.  
  
5.  Adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> para o host de serviço logo após o código que adiciona o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Esse código especifica que as mensagens de descoberta devem ser enviadas para o ponto de extremidade de descoberta UDP padrão.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Para criar um aplicativo cliente que usa a descoberta para chamar o serviço  
  
1.  Adicionar um novo aplicativo de console à solução chamado `DiscoveryClientApp`.  
  
2.  Adicione uma referência ao `System.ServiceModel.dll` e `System.ServiceModel.Discovery.dll`  
  
3.  Copie os arquivos GeneratedClient.cs e App. config do projeto de cliente existentes para o novo projeto DiscoveryClientApp. Para fazer isso, clique com botão direito os arquivos a **Gerenciador de soluções**, selecione **cópia**e, em seguida, selecione o **DiscoveryClientApp** do projeto, clique com botão direito e selecione **Colar**.  
  
4.  Abra Module.vb.  
  
5.  Adicione o seguinte `using` instruções.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  Adicione um método estático chamado `FindCalculatorServiceAddress()` para o `Program` classe.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Esse método usa a descoberta para pesquisar o `CalculatorService` service.  
  
7.  Dentro de `FindCalculatorServiceAddress` método, crie um novo <xref:System.ServiceModel.Discovery.DiscoveryClient> instância, passando um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> para o construtor.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Isso informa ao WCF que o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe deve usar o ponto de extremidade de descoberta UDP padrão para enviar e receber mensagens de descoberta.  
  
8.  Na próxima linha, chame o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método e especifique um <xref:System.ServiceModel.Discovery.FindCriteria> instância que contém o contrato de serviço que você deseja pesquisar. Nesse caso, especifique `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Após a chamada para <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, verifique se há pelo menos um serviço correspondente e retornar o <xref:System.ServiceModel.EndpointAddress> do primeiro serviço correspondente. Caso contrário, retornará `null`.  
  
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
  
10. Adicionar um método estático denominado `InvokeCalculatorService` para o `Program` classe.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Esse método usa o endereço do ponto de extremidade que retornado de `FindCalculatorServiceAddress` para chamar o serviço da Calculadora.  
  
11. Dentro de `InvokeCalculatorService` método, crie uma instância da `CalculatorServiceClient` classe. Essa classe é definida pelo [auto-hospedar](https://go.microsoft.com/fwlink/?LinkId=145523) exemplo. Ele foi gerado usando Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na próxima linha, defina o endereço do ponto de extremidade do cliente para o endereço do ponto de extremidade retornado de `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Imediatamente após o código para a etapa anterior, chame os métodos expostos pelo serviço de calculadora.  
  
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
  
14. Adicione código para o `Main()` método na `Program` classe chamar `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na próxima linha, chame o `InvokeCalculatorService()` e passar o endereço do ponto de extremidade que retornado de `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Abra um prompt de comando com privilégios elevados e execute Service.exe.  
  
2.  Abra um prompt de comando e execute Discoveryclientapp.exe.  
  
3.  A saída do service.exe deve parecer com a saída a seguir.  
  
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
  
4.  A saída do Discoveryclientapp.exe deve parecer com a saída a seguir.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem do código para este exemplo. Como esse código é baseado na [auto-hospedar](https://go.microsoft.com/fwlink/?LinkId=145523) exemplo, somente os arquivos que são alterados são listados. Para obter mais informações sobre o exemplo de hospedagem interna, consulte [instruções de instalação](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

## <a name="see-also"></a>Consulte também  
 [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Modelo de objeto de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
