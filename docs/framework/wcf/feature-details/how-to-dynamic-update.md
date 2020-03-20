---
title: Como atualizar dinamicamente
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: aaeb4d9d42c289cf34a6aee9212fc2d74b8f8c01
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184959"
---
# <a name="how-to-dynamic-update"></a>Como atualizar dinamicamente
Este tópico descreve as etapas básicas necessárias para criar e atualizar dinamicamente a configuração de roteamento. Neste exemplo, a configuração inicial de roteamento é obtida a partir do arquivo de configuração e encaminha todas as mensagens para o serviço de calculadora Calc regular; no entanto, é posteriormente atualizado programáticamente a fim de alterar o ponto final de destino do serviço arredondamentoCalc.  
  
> [!NOTE]
> Em muitas implementações, a configuração será totalmente dinâmica e não dependerá de uma configuração padrão; no entanto, existem alguns cenários, como o deste tópico, onde é desejável ter um estado de configuração padrão quando o serviço é iniciado.  
  
> [!NOTE]
> Atualizações dinâmicas ocorrem apenas na memória, e não resultam na modificação de arquivos de configuração.  
  
 Tanto o Calc regular quanto o arredondamentoCalc suportam as mesmas operações de adicionar, subtrair, multiplicar e dividir; no entanto, arredondarCalc arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar. Um arquivo de configuração é usado para configurar o serviço para encaminhar todas as mensagens para o serviço regularCalc. Depois que o Serviço de <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> Roteamento for iniciado, é usado para reconfigurar o serviço para encaminhar mensagens para o serviço de arredondamentoCalc.  
  
### <a name="implement-initial-configuration"></a>Implementar configuração inicial  
  
1. Crie a configuração básica do serviço de roteamento especificando os pontos finais de serviço expostos pelo serviço. O exemplo a seguir define um único ponto final de serviço, que será usado para receber mensagens. Ele também define um ponto final do cliente que será usado para enviar mensagens para o Calc regular.  
  
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
  
2. Defina o filtro usado para direcionar mensagens para os pontos finais de destino. Para este exemplo, o filtro MatchAll é usado para encaminhar todas as mensagens para o CalcEndpoint regular definido anteriormente. O exemplo a seguir define a tabela do filtro e do filtro.  
  
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
  
3. Para avaliar as mensagens recebidas contra os filtros contidos na tabela de filtros, você deve associar a tabela do filtro com os pontos finais de serviço usando o comportamento de roteamento. O exemplo a seguir demonstra associar "filterTable1" com o ponto final do serviço.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Implementar configuração dinâmica  
 A configuração dinâmica do Serviço de Roteamento <xref:System.ServiceModel.Routing.RoutingConfiguration> só <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> pode ser executada em código, criando uma nova configuração e usando para substituir a configuração atual.  Para este exemplo, o Serviço de Roteamento é auto-hospedado dentro de um aplicativo de console. Depois que o aplicativo for iniciado, você pode modificar a configuração de roteamento inserindo 'regular' ou 'arredondando' na janela do console para configurar o ponto final de destino para o qual as mensagens são roteadas; regularCalc quando 'regular' é inserido, caso contrário arredondandoCalc quando 'arredondamento' é inserido.  
  
1. As seguintes instruções de uso devem ser adicionadas para dar suporte ao Serviço de Roteamento.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. O código a seguir é usado para auto-hospedar o Serviço de Roteamento como um aplicativo de console. Isso inicializa o Serviço de Roteamento usando a configuração descrita na etapa anterior, que está contida no arquivo de configuração do aplicativo. O loop while contém o código usado para alterar a configuração de roteamento.  
  
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
  
3. Para atualizar dinamicamente a configuração de roteamento, uma nova configuração de roteamento deve ser criada. Isso deve conter todos os pontos finais, filtros e tabelas de filtro suscitados para a nova configuração de roteamento, pois substituirá completamente a configuração de roteamento existente. Para usar a nova configuração de <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> roteamento, você deve invocar e passar a nova configuração.  
  
     Adicione o seguinte código ao loop while definido anteriormente para permitir que o serviço seja reconfigurado com base na entrada do usuário.  
  
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
    > Uma vez que o método para fornecer uma nova configuração de roteamento está contido na extensão de serviço RoutingExtension, novos objetos de configuração de roteamento podem ser fornecidos em qualquer lugar do modelo de extensibilidade WCF que tenha ou possa obter uma referência ao ServiceHost ou Extensões de serviço (como em outra Extensão de Serviço).
  
## <a name="example"></a>Exemplo  

A seguir está uma listagem completa do aplicativo de console usado neste exemplo:
  
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
  
## <a name="example"></a>Exemplo  

A seguir está uma listagem completa do arquivo de configuração usado neste exemplo:
  
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
  
## <a name="see-also"></a>Confira também

- [Serviços de roteamento](../samples/routing-services.md)
