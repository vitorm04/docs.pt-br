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
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF
Este tópico explica como tornar um serviço da Windows Communication Foundation (WCF) descoberto. É baseado na amostra [self-host.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host)  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Para configurar a amostra de serviço self-host existente para o Discovery  
  
1. Abra a solução Self-Host no Visual Studio 2012. A amostra está localizada no diretório TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Adicione uma `System.ServiceModel.Discovery.dll` referência ao projeto de serviço. Você pode ver uma mensagem de erro dizendo "Sistema. ServiceModel.Discovery.dll ou uma de suas dependências requer uma versão posterior do .NET Framework do que a especificada no projeto ..." Se você vir esta mensagem, clique com o botão direito do mouse no projeto no Solution Explorer e escolha **Propriedades**. Na janela Propriedades do **projeto,** certifique-se de que a **estrutura de destino** é [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3. Abra o arquivo Service.cs `using` e adicione a seguinte declaração.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. No `Main()` método, dentro `using` da declaração, adicione uma <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância ao host de serviço.  
  
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
  
     O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> especificaque que o serviço a que é aplicado é descoberto.  
  
5. Adicione <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a ao host de serviço logo <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>após o código que adiciona o .  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Este código especifica que as mensagens de detecção devem ser enviadas para o ponto final de detecção udp padrão.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Para criar um aplicativo cliente que usa a descoberta para chamar o serviço  
  
1. Adicione um novo aplicativo de `DiscoveryClientApp`console à solução chamada .  
  
2. Adicione uma `System.ServiceModel.dll` referência e`System.ServiceModel.Discovery.dll`  
  
3. Copie os arquivos GeneratedClient.cs e App.config do projeto cliente existente para o novo projeto DiscoveryClientApp. Para isso, clique com o botão direito do mouse nos arquivos do **Solution Explorer**, selecione **Copiar**e selecione o projeto **DiscoveryClientApp,** clique com o botão direito do mouse e **selecione Colar**.  
  
4. Abra Program.cs.  
  
5. Adicione as seguintes declarações de `using`.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Adicione um método `FindCalculatorServiceAddress()` estático chamado à `Program` classe.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Este método usa a `CalculatorService` descoberta para procurar o serviço.  
  
7. Dentro `FindCalculatorServiceAddress` do método, <xref:System.ServiceModel.Discovery.DiscoveryClient> crie uma nova <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> instância, passando em um para o construtor.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Isso diz ao <xref:System.ServiceModel.Discovery.DiscoveryClient> WCF que a classe deve usar o ponto final de descoberta udp padrão para enviar e receber mensagens de descoberta.  
  
8. Na próxima linha, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ligue para <xref:System.ServiceModel.Discovery.FindCriteria> o método e especifique uma instância que contenha o contrato de serviço que você deseja procurar. Neste caso, `ICalculator`especifique .  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Após a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>chamada para , verifique se há pelo menos <xref:System.ServiceModel.EndpointAddress> um serviço correspondente e devolva o primeiro serviço correspondente. Caso contrário, retorne `null`.  
  
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
  
10. Adicione um método `InvokeCalculatorService` estático nomeado à `Program` classe.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Este método usa o endereço `FindCalculatorServiceAddress` de ponto final retornado para chamar o serviço de calculadora.  
  
11. Dentro `InvokeCalculatorService` do método, crie `CalculatorServiceClient` uma instância da classe. Esta classe é definida pela amostra [Self-Host.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) Foi gerado usando Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na próxima linha, defina o endereço de ponto final do `FindCalculatorServiceAddress()`cliente para o endereço de ponto final retornado de .  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Imediatamente após o código da etapa anterior, chame os métodos expostos pelo serviço de calculadora.  
  
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
  
14. Adicione código `Main()` ao método `Program` na `FindCalculatorServiceAddress`classe para chamar .  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na próxima linha, `InvokeCalculatorService()` ligue para o e passe `FindCalculatorServiceAddress()`no endereço final retornado de .  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1. Abra um prompt de comando elevado e execute Service.exe.  
  
2. Abra um prompt de comando e execute Discoveryclientapp.exe.  
  
3. A saída do service.exe deve parecer com a seguinte saída.  
  
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
  
4. A saída do Discoveryclientapp.exe deve parecer com a seguinte saída.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Exemplo  
 A seguir está uma lista do código para esta amostra. Como este código é baseado na amostra [self-host,](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) apenas os arquivos que são alterados são listados. Para obter mais informações sobre a amostra auto-host, consulte [Instruções de configuração](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).  
  
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

## <a name="see-also"></a>Confira também

- [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Modelo de objeto de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
