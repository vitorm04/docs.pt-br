---
title: 'Como: Atualização dinâmica'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 0a103e980d0d1be08f3ae6850c6af64405582c7b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972086"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="d40b4-102">Como: Atualização dinâmica</span><span class="sxs-lookup"><span data-stu-id="d40b4-102">How To: Dynamic Update</span></span>
<span data-ttu-id="d40b4-103">Este tópico descreve as etapas básicas necessárias para criar e atualizar dinamicamente a configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d40b4-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="d40b4-104">Neste exemplo, a configuração de roteamento inicial é obtida do arquivo de configuração e roteia todas as mensagens para o serviço de calculadora regularCalc; no entanto, ele é posteriormente atualizado programaticamente para alterar o ponto de extremidade de destino do serviço roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="d40b4-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d40b4-105">Em muitas implementações, a configuração será totalmente dinâmica e não dependerá de uma configuração padrão; no entanto, há alguns cenários, como aquele neste tópico, em que é desejável ter um estado de configuração padrão quando o serviço é iniciado.</span><span class="sxs-lookup"><span data-stu-id="d40b4-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d40b4-106">As atualizações dinâmicas ocorrem apenas na memória e não resultam na modificação dos arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="d40b4-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="d40b4-107">RegularCalc e roundingCalc dão suporte às mesmas operações de adicionar, subtrair, multiplicar e dividir; no entanto, roundingCalc arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="d40b4-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="d40b4-108">Um arquivo de configuração é usado para configurar o serviço para rotear todas as mensagens para o serviço regularCalc.</span><span class="sxs-lookup"><span data-stu-id="d40b4-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="d40b4-109">Depois que o serviço de roteamento foi iniciado <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> , é usado para reconfigurar o serviço para rotear mensagens para o serviço roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="d40b4-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="d40b4-110">Implementar configuração inicial</span><span class="sxs-lookup"><span data-stu-id="d40b4-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="d40b4-111">Crie a configuração básica do serviço de roteamento especificando os pontos de extremidade de serviço expostos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d40b4-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="d40b4-112">O exemplo a seguir define um único ponto de extremidade de serviço, que será usado para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="d40b4-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="d40b4-113">Ele também define um ponto de extremidade de cliente que será usado para enviar mensagens para o regularCalc.</span><span class="sxs-lookup"><span data-stu-id="d40b4-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="d40b4-114">Defina o filtro usado para rotear mensagens para os pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="d40b4-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="d40b4-115">Para este exemplo, o filtro filtro matchall é usado para rotear todas as mensagens para o regularCalcEndpoint definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d40b4-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="d40b4-116">O exemplo a seguir define o filtro e a tabela de filtro.</span><span class="sxs-lookup"><span data-stu-id="d40b4-116">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="d40b4-117">Para avaliar as mensagens de entrada em relação aos filtros contidos na tabela de filtros, você deve associar a tabela de filtros aos pontos de extremidade de serviço usando o comportamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d40b4-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="d40b4-118">O exemplo a seguir demonstra como associar "filterTable1" ao ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="d40b4-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="d40b4-119">Implementar configuração dinâmica</span><span class="sxs-lookup"><span data-stu-id="d40b4-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="d40b4-120">A configuração dinâmica do serviço de roteamento só pode ser executada no código criando um novo <xref:System.ServiceModel.Routing.RoutingConfiguration> e usando <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> para substituir a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="d40b4-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="d40b4-121">Para este exemplo, o serviço de roteamento é hospedado internamente em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d40b4-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="d40b4-122">Depois que o aplicativo for iniciado, você poderá modificar a configuração de roteamento inserindo ' regular ' ou ' arredondando ' na janela do console para configurar o ponto de extremidade de destino para o qual as mensagens são roteadas; regularCalc quando ' regular ' for inserido, caso contrário, roundingCalc quando ' arredondando ' for inserido.</span><span class="sxs-lookup"><span data-stu-id="d40b4-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="d40b4-123">As instruções using a seguir devem ser adicionadas para dar suporte ao serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d40b4-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="d40b4-124">O código a seguir é usado para hospedar por conta própria o serviço de roteamento como um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d40b4-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="d40b4-125">Isso inicializa o serviço de roteamento usando a configuração descrita na etapa anterior, que está contida no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d40b4-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="d40b4-126">O loop while contém o código usado para alterar a configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d40b4-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners           
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="d40b4-127">Para atualizar dinamicamente a configuração de roteamento, é necessário criar uma nova configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d40b4-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="d40b4-128">Isso deve conter todos os pontos de extremidade, filtros e tabelas de filtro necessários para a nova configuração de roteamento, pois ele substituirá completamente a configuração de roteamento existente.</span><span class="sxs-lookup"><span data-stu-id="d40b4-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="d40b4-129">Para usar a nova configuração de roteamento, você deve invocar <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> e passar a nova configuração.</span><span class="sxs-lookup"><span data-stu-id="d40b4-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="d40b4-130">Adicione o seguinte código ao loop while definido anteriormente para permitir que o serviço seja reconfigurado com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="d40b4-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="d40b4-131">Como o método para fornecer um novo RoutingConfiguration está contido na extensão de serviço RoutingExtension, novos objetos RoutingConfiguration podem ser fornecidos em qualquer lugar no modelo de extensibilidade do WCF que tem ou pode obter uma referência para o ServiceHost ou Extensões (como em outra imextension).</span><span class="sxs-lookup"><span data-stu-id="d40b4-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="d40b4-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d40b4-132">Example</span></span>  
 <span data-ttu-id="d40b4-133">A seguir está uma lista completa do aplicativo de console usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d40b4-133">Following is a complete listing of the console application used in this example.</span></span>  
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {             
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners           
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="d40b4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d40b4-134">Example</span></span>  
 <span data-ttu-id="d40b4-135">A seguir está uma lista completa do arquivo de configuração usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d40b4-135">Following is a complete listing of the configuration file used in this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d40b4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d40b4-136">See also</span></span>

- [<span data-ttu-id="d40b4-137">Serviços de roteamento</span><span class="sxs-lookup"><span data-stu-id="d40b4-137">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
