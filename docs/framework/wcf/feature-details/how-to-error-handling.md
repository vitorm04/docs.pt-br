---
title: Como lidar com erros
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5b0fe57bb6a4604c86e63a154e3af5542672912
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-error-handling"></a><span data-ttu-id="9e2f8-102">Como lidar com erros</span><span class="sxs-lookup"><span data-stu-id="9e2f8-102">How To: Error Handling</span></span>
<span data-ttu-id="9e2f8-103">Este tópico descreve as etapas básicas necessárias para criar uma configuração de roteamento que usa o tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="9e2f8-104">Neste exemplo, as mensagens são roteadas para um ponto de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="9e2f8-105">Se uma mensagem não pode ser entregue devido a uma falha de comunicação ou de rede (<xref:System.ServiceModel.CommunicationException>), a mensagem é enviada novamente para um ponto de extremidade alternativo.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e2f8-106">Para simular uma falha de rede, o ponto de extremidade de destino usado neste exemplo contém um endereço incorreto.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="9e2f8-107">As mensagens roteadas para essa falha de ponto de extremidade como nenhum serviço está escutando no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e2f8-108">Embora o exemplo contido neste tópico não aborda explicitamente as configurações de tempo limite, você deve levar em consideração ao usar o tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="9e2f8-109">Quando são encontrados erros, haverá um atraso adicional encontrado antes do cliente recebe uma resposta.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="9e2f8-110">Isso ocorre porque o erro é recebido no serviço de roteamento, que, em seguida, tenta enviar a mensagem para um ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="9e2f8-111">Se os valores de tempo limite associado com os pontos de extremidade primário e de backup de destino forem grandes, o cliente pode ter um longo atraso como a mensagem de falha em vários pontos de extremidade na lista de backup antes de ser enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="9e2f8-112">Como o serviço de roteamento foi possível encontrar um atraso máximo igual à soma do valor de tempo limite para todos os pontos de extremidade associados com um filtro, é recomendável que você aumentar o tempo limite esperado no cliente adequadamente.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="9e2f8-113">Implementar o tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="9e2f8-113">Implement Error Handling</span></span>  
  
1.  <span data-ttu-id="9e2f8-114">Crie a configuração básica do serviço de roteamento, especificando o ponto de extremidade do serviço exposto pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="9e2f8-115">O exemplo a seguir define um ponto de extremidade de serviço único, que é usado para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="9e2f8-116">Ele também define os pontos de extremidade do cliente que são usados para enviar mensagens. deadDestination e realDestination.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="9e2f8-117">O ponto de extremidade deadDestination contém um endereço que não faz referência a um serviço em execução e é usado para simular uma falha de rede ao enviar mensagens para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/" />  
          </baseAddresses>  
        </host>  
        <!-- Create the Routing Service endpoint -->  
        <endpoint address="router"  
                  binding="basicHttpBinding"  
                  name="RoutingServiceEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
  
    <!-- Create the destination endpoints that we want to send to -->  
    <client>  
      <!-- Create a dummy endpoint that we know will be down -->  
      <endpoint name="deadDestination"   
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <!-- Now create the real service endpoint -->  
      <endpoint name="realDestination"   
                address="net.tcp://localhost:8080/servicemodelsamples/service"  
                binding="netTcpBinding"   
                contract="*" />  
    </client>  
    ```  
  
2.  <span data-ttu-id="9e2f8-118">Defina os filtros usados para rotear mensagens para os pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="9e2f8-119">Neste exemplo, um filtro de MatchAll é usado para corresponder a todas as mensagens recebidas pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  <span data-ttu-id="9e2f8-120">Defina a lista de ponto de extremidade de backup, que contém os pontos de extremidade que uma mensagem é enviada para em caso de falha de rede ou de comunicação ao enviar para o ponto de extremidade de destino principal.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="9e2f8-121">O exemplo a seguir define uma lista de backup que contém um ponto de extremidade; No entanto, vários pontos de extremidade podem ser especificados em uma lista de backup.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="9e2f8-122">Se a lista de backup contiver vários pontos de extremidade, quando uma rede ou falha de comunicação ocorre, que o serviço de roteamento tenta enviar a mensagem para o primeiro ponto de extremidade na lista.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="9e2f8-123">Se ocorrer uma falha de rede ou de comunicação ao enviar para este ponto de extremidade, o serviço de roteamento tenta enviar a mensagem para o próximo ponto de extremidade contido na lista.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="9e2f8-124">O serviço continuará a enviar a mensagem para cada ponto de extremidade na lista de ponto de extremidade de backup até que a mensagem é enviada com êxito, todos os pontos de extremidade de backup retornam um erro de rede ou relacionados de comunicação, ou a mensagem é enviada e o ponto de extremidade retorna um fora da rede, Erro não relacionadas a comunicações.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  <span data-ttu-id="9e2f8-125">Defina a tabela de filtro, que associa o filtro com o ponto de extremidade deadDestination e a lista de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="9e2f8-126">O serviço de roteamento primeiro tenta enviar a mensagem para o ponto de extremidade de destino associado ao filtro.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="9e2f8-127">Como o deadDestination contém um endereço que não faz referência a um serviço em execução, isso resulta em um erro de rede.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="9e2f8-128">O serviço de roteamento, em seguida, tenta enviar a mensagem para o ponto de extremidade especificado no backupEndpointlist.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
    ```xml  
    <filterTables>  
            <!-- Set up the Routing Service's Message Filter Table -->  
            <filterTable name="filterTable1">  
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->  
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
                <!-- Listed in the backupEndpointList -->  
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
            </filterTable>  
          </filterTables>  
    ```  
  
5.  <span data-ttu-id="9e2f8-129">Para avaliar as mensagens de entrada com base no filtro contidas na tabela de filtro, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="9e2f8-130">O exemplo a seguir demonstra a associação "filterTable1" com os pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <!-- Set up the Routing Behavior -->  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="9e2f8-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e2f8-131">Example</span></span>  
 <span data-ttu-id="9e2f8-132">A seguir está uma listagem completa do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9e2f8-132">Following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/" />  
          </baseAddresses>  
        </host>  
        <!-- Create the Routing Service endpoint -->  
        <endpoint address="router"  
                  binding="basicHttpBinding"  
                  name="RoutingServiceEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <!-- Set up the Routing Behavior -->  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <!-- Create the destination endpoints that we want to send to -->  
    <client>  
      <!-- Create a dummy endpoint that we know will be down -->  
      <endpoint name="deadDestination"   
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <!-- Now create the real service endpoint -->  
      <endpoint name="realDestination"   
                address="net.tcp://localhost:8080/servicemodelsamples/service"  
                binding="netTcpBinding"   
                contract="*" />  
    </client>  
    <routing>  
      <filters>  
        <!-- Create a MatchAll filter which will catch all messages -->  
        <filter name="MatchAllFilter1" filterType="MatchAll" />  
      </filters>  
      <filterTables>  
        <!-- Set up the Routing Service's Message Filter Table -->  
        <filterTable name="filterTable1">  
            <!-- Add an entrty that maps the MatchAllMessageFilter to the dead destination -->  
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
            <!-- Listed in the backupEndpointList -->  
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
        </filterTable>  
      </filterTables>  
      <!-- Create the backup endpoint list -->  
      <backupLists>          
        <backupList name="backupEndpointList">  
            <add endpointName="realDestination" />  
        </backupList>  
      </backupLists>  
      </routing>  
  </system.serviceModel>  
</configuration>  
```
