---
title: 'Como: Controle de versão de serviço'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: afc1a690cae020ded3988cfd41f0e926a2e86f1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346282"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="74b52-102">Como: Controle de versão de serviço</span><span class="sxs-lookup"><span data-stu-id="74b52-102">How To: Service Versioning</span></span>
<span data-ttu-id="74b52-103">Este tópico descreve as etapas básicas necessárias para criar uma configuração de roteamento que roteia mensagens para diferentes versões do mesmo serviço.</span><span class="sxs-lookup"><span data-stu-id="74b52-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="74b52-104">Neste exemplo, as mensagens são roteadas para duas versões diferentes de um serviço de calculadora `roundingCalc` (v1) e `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="74b52-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="74b52-105">Ambas as implementações de suportam as mesmas operações; No entanto o serviço mais antigo, `roundingCalc`, Arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="74b52-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="74b52-106">Um aplicativo cliente deve ser capaz de indicar se deseja usar o mais recente `regularCalc` service.</span><span class="sxs-lookup"><span data-stu-id="74b52-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="74b52-107">Para rotear uma mensagem para uma versão de serviço específico, o serviço de roteamento deve ser capaz de determinar o destino da mensagem com base no conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="74b52-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="74b52-108">O método demonstrado a seguir, o cliente especificará a versão ao inserir informações em um cabeçalho de mensagem.</span><span class="sxs-lookup"><span data-stu-id="74b52-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="74b52-109">Há métodos de controle de versão de serviço que não necessitam de clientes passar dados adicionais.</span><span class="sxs-lookup"><span data-stu-id="74b52-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="74b52-110">Por exemplo, uma mensagem poderia ser roteada para a mais recente ou uma versão compatível mais de um serviço ou o roteador poderia usar uma parte do envelope SOAP padrão.</span><span class="sxs-lookup"><span data-stu-id="74b52-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="74b52-111">As operações expostas por ambos os serviços são:</span><span class="sxs-lookup"><span data-stu-id="74b52-111">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="74b52-112">Adicionar</span><span class="sxs-lookup"><span data-stu-id="74b52-112">Add</span></span>  
  
-   <span data-ttu-id="74b52-113">Subtração</span><span class="sxs-lookup"><span data-stu-id="74b52-113">Subtract</span></span>  
  
-   <span data-ttu-id="74b52-114">Multiplicar</span><span class="sxs-lookup"><span data-stu-id="74b52-114">Multiply</span></span>  
  
-   <span data-ttu-id="74b52-115">Divisão</span><span class="sxs-lookup"><span data-stu-id="74b52-115">Divide</span></span>  
  
 <span data-ttu-id="74b52-116">Como ambas as implementações de serviço lidar com as mesmas operações e são essencialmente idênticas diferentes dos dados que eles retornam, os dados base contidos nas mensagens enviadas de aplicativos cliente não são exclusivos o suficiente para que você possa determinar como rotear o solicitação.</span><span class="sxs-lookup"><span data-stu-id="74b52-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="74b52-117">Por exemplo, os filtros de ação não podem ser usados porque as ações padrão para ambos os serviços são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="74b52-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="74b52-118">Isso pode ser resolvido de diversas maneiras, como expor um ponto de extremidade específico no roteador para cada versão do serviço ou adicionando um elemento de cabeçalho personalizado para a mensagem para indicar a versão do serviço.</span><span class="sxs-lookup"><span data-stu-id="74b52-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="74b52-119">Cada uma dessas abordagens permite exclusivamente rotear mensagens de entrada para uma versão específica do serviço, mas utilizar o conteúdo da mensagem exclusivo é o método preferencial de diferenciar entre as solicitações para as versões de serviço diferentes.</span><span class="sxs-lookup"><span data-stu-id="74b52-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="74b52-120">Neste exemplo, o aplicativo cliente adiciona o cabeçalho personalizado 'CalcVer' para a mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="74b52-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="74b52-121">Esse cabeçalho conterá um valor que indica a versão do serviço que a mensagem deve ser roteada.</span><span class="sxs-lookup"><span data-stu-id="74b52-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="74b52-122">Um valor de '1' indica que a mensagem deve ser processada pelo serviço roundingCalc, enquanto o serviço regularCalc indica que um valor de '2'.</span><span class="sxs-lookup"><span data-stu-id="74b52-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="74b52-123">Isso permite que o aplicativo de cliente diretamente controlar qual versão do serviço processará a mensagem.</span><span class="sxs-lookup"><span data-stu-id="74b52-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="74b52-124">Como o cabeçalho personalizado é um valor contido dentro da mensagem, você pode usar um ponto de extremidade para receber as mensagens destinadas para ambas as versões do serviço.</span><span class="sxs-lookup"><span data-stu-id="74b52-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="74b52-125">O código a seguir pode ser usado no aplicativo cliente para adicionar esse cabeçalho personalizado para a mensagem:</span><span class="sxs-lookup"><span data-stu-id="74b52-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="74b52-126">Implementar o controle de versão do serviço</span><span class="sxs-lookup"><span data-stu-id="74b52-126">Implement Service Versioning</span></span>  
  
1. <span data-ttu-id="74b52-127">Crie a configuração básica do serviço de roteamento, especificando o ponto de extremidade de serviço exposto pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="74b52-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="74b52-128">O exemplo a seguir define um ponto de extremidade de serviço único, que será usado para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="74b52-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="74b52-129">Ele também define os pontos de extremidade do cliente que serão usados para enviar mensagens para o `roundingCalc` (v1) e o `regularCalc` serviços (v2).</span><span class="sxs-lookup"><span data-stu-id="74b52-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
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
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2. <span data-ttu-id="74b52-130">Defina os filtros usados para rotear mensagens para os pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="74b52-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="74b52-131">Neste exemplo, o filtro XPath é usado para detectar o valor do cabeçalho personalizado "CalcVer" para determinar qual é a mensagem deve ser roteada para a versão.</span><span class="sxs-lookup"><span data-stu-id="74b52-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="74b52-132">Um filtro XPath também é usado para detectar mensagens que não contêm o cabeçalho "CalcVer".</span><span class="sxs-lookup"><span data-stu-id="74b52-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="74b52-133">O exemplo a seguir define os filtros necessários e a tabela de namespace.</span><span class="sxs-lookup"><span data-stu-id="74b52-133">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="74b52-134">O prefixo de namespace s12 é definido por padrão na tabela de namespace e representa o namespace `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="74b52-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3. <span data-ttu-id="74b52-135">Defina a tabela de filtro, que associa cada filtro com um ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="74b52-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="74b52-136">Se a mensagem contém o cabeçalho de "CalcVer" com um valor de 1, ele será enviado para o serviço regularCalc.</span><span class="sxs-lookup"><span data-stu-id="74b52-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="74b52-137">Se o cabeçalho contém um valor de 2, ele será enviado para o serviço roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="74b52-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="74b52-138">Se nenhum cabeçalho estiver presente, a mensagem será roteada para o regularCalc.</span><span class="sxs-lookup"><span data-stu-id="74b52-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="74b52-139">A seguir define a tabela de filtro e adiciona os filtros definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="74b52-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="74b52-140">Para avaliar as mensagens de entrada com os filtros contidos na tabela de filtros, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="74b52-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="74b52-141">O exemplo a seguir demonstra a associação `filterTable1` com os pontos de extremidade de serviço:</span><span class="sxs-lookup"><span data-stu-id="74b52-141">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="74b52-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74b52-142">Example</span></span>  
 <span data-ttu-id="74b52-143">A seguir está uma listagem completa do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="74b52-143">The following is a complete listing of the configuration file.</span></span>  
  
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
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="74b52-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74b52-144">Example</span></span>  
 <span data-ttu-id="74b52-145">A seguir está uma listagem completa do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="74b52-145">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to   
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
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
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="74b52-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74b52-146">See also</span></span>

- [<span data-ttu-id="74b52-147">Serviços de roteamento</span><span class="sxs-lookup"><span data-stu-id="74b52-147">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
