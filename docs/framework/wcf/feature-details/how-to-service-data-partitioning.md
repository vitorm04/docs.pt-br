---
title: 'Como: fornecer particionamento de dados'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300379"
---
# <a name="how-to-service-data-partitioning"></a>Como: fornecer particionamento de dados
Este tópico descreve as etapas básicas necessárias para mensagens de partição em várias instâncias do mesmo serviço de destino. Particionamento de dados de serviço é normalmente usados quando você precisar dimensionar um serviço a fim de fornecer a melhor qualidade de serviço, ou quando você precisa lidar com solicitações de clientes diferentes de uma maneira específica. Por exemplo, mensagens de alto valor ou clientes de "Ouro" talvez precise ser processadas em uma prioridade mais alta do que as mensagens de um cliente padrão.  
  
 Neste exemplo, as mensagens são roteadas para uma das duas instâncias do serviço regularCalc. Ambas as instâncias do serviço são idênticas; No entanto do serviço representado por mensagens de processos de ponto de extremidade de calculator1 recebidos de clientes de alto valor, o ponto de extremidade de calculadora 2 processa mensagens de outros clientes  
  
 Não tem todos os dados exclusivos que podem ser usados para identificar qual instância de serviço, a mensagem deve ser roteada para a mensagem enviada do cliente. Para permitir que cada cliente para encaminhar dados para um serviço de destino específico, implementaremos dois pontos de extremidade de serviço que serão usados para receber mensagens.  
  
> [!NOTE]
>  Embora este exemplo usa pontos de extremidade específicos para particionar dados, isso também pode ser feito usando as informações contidas dentro da mensagem como dados de cabeçalho ou no corpo.  
  
### <a name="implement-service-data-partitioning"></a>Particionamento de dados de serviço implementar  
  
1. Crie a configuração básica do serviço de roteamento, especificando os pontos de extremidade de serviço expostos pelo serviço. O exemplo a seguir define dois pontos de extremidade, que serão usados para receber mensagens. Ele também define os pontos de extremidade do cliente, que são usados para enviar mensagens para as instâncias de serviço regularCalc.  
  
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
  
2. Defina os filtros usados para rotear mensagens para os pontos de extremidade de destino.  Neste exemplo, o filtro de EndpointName é usado para determinar qual ponto de extremidade de serviço recebeu a mensagem. O exemplo a seguir define os filtros e a seção de roteamento necessário.  
  
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
  
3. Defina a tabela de filtro, que associa cada filtro com um ponto de extremidade do cliente. Neste exemplo, a mensagem será roteada com base no ponto de extremidade específico que foi recebido pela. Uma vez que a mensagem só pode corresponder a um dos dois filtros possíveis, não é necessário para usar a prioridade do filtro para controlar a ordem na qual os filtros são avaliados.  
  
     A seguir define a tabela de filtro e adiciona os filtros definidos anteriormente.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Para avaliar as mensagens de entrada com os filtros contidos na tabela, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento. O exemplo a seguir demonstra a associação "filterTable1" com os pontos de extremidade de serviço:  
  
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
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem completa do arquivo de configuração.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Serviços de roteamento](../../../../docs/framework/wcf/samples/routing-services.md)
