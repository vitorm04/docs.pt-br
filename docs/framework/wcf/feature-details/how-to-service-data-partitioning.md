---
title: "Como particionar dados de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6a3f95f2ecea342072de010a6cee51069f755fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="3c6a1-102">Como particionar dados de serviço</span><span class="sxs-lookup"><span data-stu-id="3c6a1-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="3c6a1-103">Este tópico descreve as etapas básicas necessárias para mensagens de partição em várias instâncias do mesmo serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="3c6a1-104">Particionamento de dados de serviço geralmente são usados quando você precisar dimensionar um serviço para fornecer a melhor qualidade de serviço, ou quando você precisa lidar com solicitações de diferentes clientes de uma maneira específica.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="3c6a1-105">Por exemplo, mensagens de alto valor ou clientes "Ouro" podem precisar ser processado em uma prioridade mais alta que as mensagens de um cliente padrão.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="3c6a1-106">Neste exemplo, as mensagens são roteadas para uma das duas instâncias do serviço regularCalc.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="3c6a1-107">Ambas as instâncias do serviço são idênticas; No entanto o serviço representado pelas mensagens de processos de ponto de extremidade calculator1 recebeu de clientes de alto valor, o ponto de extremidade de calculadora 2 processa mensagens de outros clientes</span><span class="sxs-lookup"><span data-stu-id="3c6a1-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="3c6a1-108">A mensagem enviada do cliente não tem nenhum dado exclusivo que pode ser usado para identificar qual instância de serviço a mensagem deve ser roteada.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="3c6a1-109">Para permitir que cada cliente aos dados de rota para um serviço de destino específico, implementaremos dois pontos de extremidade de serviço que serão usados para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c6a1-110">Embora este exemplo usa pontos de extremidade específicos para particionar dados, isso pode também ser feito usando as informações contidas na mensagem como dados de cabeçalho ou no corpo.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="3c6a1-111">Implementação de particionamento de dados de serviço</span><span class="sxs-lookup"><span data-stu-id="3c6a1-111">Implement Service Data Partitioning</span></span>  
  
1.  <span data-ttu-id="3c6a1-112">Crie a configuração básica do serviço de roteamento, especificando os pontos de extremidade do serviço expostos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="3c6a1-113">O exemplo a seguir define dois pontos de extremidade, que serão usados para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="3c6a1-114">Ele também define os pontos de extremidade do cliente, que são usados para enviar mensagens para as instâncias de serviço regularCalc.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2.  <span data-ttu-id="3c6a1-115">Defina os filtros usados para rotear mensagens para os pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="3c6a1-116">Neste exemplo, o filtro de EndpointName é usado para determinar qual ponto de extremidade do serviço recebeu a mensagem.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="3c6a1-117">O exemplo a seguir define a seção de roteamento necessária e filtros.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-117">The following example defines the necessary routing section and filters.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3.  <span data-ttu-id="3c6a1-118">Defina a tabela de filtro, que associa cada filtro um ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="3c6a1-119">Neste exemplo, a mensagem será roteada com base no ponto de extremidade específico que foi recebido pela.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="3c6a1-120">Desde que a mensagem só pode corresponder a um dos dois filtros possíveis, não é necessário para usar o filtro de prioridade para controlar a ordem na qual os filtros são avaliados.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="3c6a1-121">O exemplo a seguir define a tabela de filtro e adiciona os filtros definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="3c6a1-122">Para avaliar as mensagens de entrada com os filtros contidos na tabela, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="3c6a1-123">O exemplo a seguir demonstra a associação "filterTable1" com os pontos de extremidade de serviço:</span><span class="sxs-lookup"><span data-stu-id="3c6a1-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3c6a1-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c6a1-124">Example</span></span>  
 <span data-ttu-id="3c6a1-125">A seguir está uma listagem completa do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3c6a1-125">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c6a1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c6a1-126">See Also</span></span>  
 [<span data-ttu-id="3c6a1-127">Serviços de roteamento</span><span class="sxs-lookup"><span data-stu-id="3c6a1-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
