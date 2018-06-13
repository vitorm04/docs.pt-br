---
title: Como lidar com erros
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 7b173997eb53f8cf156ccb14083885a199dc8921
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493590"
---
# <a name="how-to-error-handling"></a>Como lidar com erros
Este tópico descreve as etapas básicas necessárias para criar uma configuração de roteamento que usa o tratamento de erros. Neste exemplo, as mensagens são roteadas para um ponto de extremidade de destino. Se uma mensagem não pode ser entregue devido a uma falha de comunicação ou de rede (<xref:System.ServiceModel.CommunicationException>), a mensagem é enviada novamente para um ponto de extremidade alternativo.  
  
> [!NOTE]
>  Para simular uma falha de rede, o ponto de extremidade de destino usado neste exemplo contém um endereço incorreto. As mensagens roteadas para essa falha de ponto de extremidade como nenhum serviço está escutando no endereço especificado.  
  
> [!NOTE]
>  Embora o exemplo contido neste tópico não aborda explicitamente as configurações de tempo limite, você deve levar em consideração ao usar o tratamento de erros. Quando são encontrados erros, haverá um atraso adicional encontrado antes do cliente recebe uma resposta. Isso ocorre porque o erro é recebido no serviço de roteamento, que, em seguida, tenta enviar a mensagem para um ponto de extremidade de backup. Se os valores de tempo limite associado com os pontos de extremidade primário e de backup de destino forem grandes, o cliente pode ter um longo atraso como a mensagem de falha em vários pontos de extremidade na lista de backup antes de ser enviada com êxito.  
>   
>  Como o serviço de roteamento foi possível encontrar um atraso máximo igual à soma do valor de tempo limite para todos os pontos de extremidade associados com um filtro, é recomendável que você aumentar o tempo limite esperado no cliente adequadamente.  
  
### <a name="implement-error-handling"></a>Implementar o tratamento de erros  
  
1.  Crie a configuração básica do serviço de roteamento, especificando o ponto de extremidade do serviço exposto pelo serviço. O exemplo a seguir define um ponto de extremidade de serviço único, que é usado para receber mensagens. Ele também define os pontos de extremidade do cliente que são usados para enviar mensagens. deadDestination e realDestination. O ponto de extremidade deadDestination contém um endereço que não faz referência a um serviço em execução e é usado para simular uma falha de rede ao enviar mensagens para esse ponto de extremidade.  
  
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
  
2.  Defina os filtros usados para rotear mensagens para os pontos de extremidade de destino.  Neste exemplo, um filtro de MatchAll é usado para corresponder a todas as mensagens recebidas pelo serviço de roteamento.  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  Defina a lista de ponto de extremidade de backup, que contém os pontos de extremidade que uma mensagem é enviada para em caso de falha de rede ou de comunicação ao enviar para o ponto de extremidade de destino principal. O exemplo a seguir define uma lista de backup que contém um ponto de extremidade; No entanto, vários pontos de extremidade podem ser especificados em uma lista de backup.  
  
     Se a lista de backup contiver vários pontos de extremidade, quando uma rede ou falha de comunicação ocorre, que o serviço de roteamento tenta enviar a mensagem para o primeiro ponto de extremidade na lista. Se ocorrer uma falha de rede ou de comunicação ao enviar para este ponto de extremidade, o serviço de roteamento tenta enviar a mensagem para o próximo ponto de extremidade contido na lista. O serviço continuará a enviar a mensagem para cada ponto de extremidade na lista de ponto de extremidade de backup até que a mensagem é enviada com êxito, todos os pontos de extremidade de backup retornam um erro de rede ou relacionados de comunicação, ou a mensagem é enviada e o ponto de extremidade retorna um fora da rede, Erro não relacionadas a comunicações.  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  Defina a tabela de filtro, que associa o filtro com o ponto de extremidade deadDestination e a lista de ponto de extremidade de backup.  O serviço de roteamento primeiro tenta enviar a mensagem para o ponto de extremidade de destino associado ao filtro. Como o deadDestination contém um endereço que não faz referência a um serviço em execução, isso resulta em um erro de rede. O serviço de roteamento, em seguida, tenta enviar a mensagem para o ponto de extremidade especificado no backupEndpointlist.  
  
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
  
5.  Para avaliar as mensagens de entrada com base no filtro contidas na tabela de filtro, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento.  O exemplo a seguir demonstra a associação "filterTable1" com os pontos de extremidade de serviço.  
  
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
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem completa do arquivo de configuração.  
  
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
