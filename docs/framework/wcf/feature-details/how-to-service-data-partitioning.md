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
ms.openlocfilehash: 7104aa2fee49a21dab7fcc8392a9d4bb291203fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-service-data-partitioning"></a>Como particionar dados de serviço
Este tópico descreve as etapas básicas necessárias para mensagens de partição em várias instâncias do mesmo serviço de destino. Particionamento de dados de serviço geralmente são usados quando você precisar dimensionar um serviço para fornecer a melhor qualidade de serviço, ou quando você precisa lidar com solicitações de diferentes clientes de uma maneira específica. Por exemplo, mensagens de alto valor ou clientes "Ouro" podem precisar ser processado em uma prioridade mais alta que as mensagens de um cliente padrão.  
  
 Neste exemplo, as mensagens são roteadas para uma das duas instâncias do serviço regularCalc. Ambas as instâncias do serviço são idênticas; No entanto o serviço representado pelas mensagens de processos de ponto de extremidade calculator1 recebeu de clientes de alto valor, o ponto de extremidade de calculadora 2 processa mensagens de outros clientes  
  
 A mensagem enviada do cliente não tem nenhum dado exclusivo que pode ser usado para identificar qual instância de serviço a mensagem deve ser roteada. Para permitir que cada cliente aos dados de rota para um serviço de destino específico, implementaremos dois pontos de extremidade de serviço que serão usados para receber mensagens.  
  
> [!NOTE]
>  Embora este exemplo usa pontos de extremidade específicos para particionar dados, isso pode também ser feito usando as informações contidas na mensagem como dados de cabeçalho ou no corpo.  
  
### <a name="implement-service-data-partitioning"></a>Implementação de particionamento de dados de serviço  
  
1.  Crie a configuração básica do serviço de roteamento, especificando os pontos de extremidade do serviço expostos pelo serviço. O exemplo a seguir define dois pontos de extremidade, que serão usados para receber mensagens. Ele também define os pontos de extremidade do cliente, que são usados para enviar mensagens para as instâncias de serviço regularCalc.  
  
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
  
2.  Defina os filtros usados para rotear mensagens para os pontos de extremidade de destino.  Neste exemplo, o filtro de EndpointName é usado para determinar qual ponto de extremidade do serviço recebeu a mensagem. O exemplo a seguir define a seção de roteamento necessária e filtros.  
  
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
  
3.  Defina a tabela de filtro, que associa cada filtro um ponto de extremidade do cliente. Neste exemplo, a mensagem será roteada com base no ponto de extremidade específico que foi recebido pela. Desde que a mensagem só pode corresponder a um dos dois filtros possíveis, não é necessário para usar o filtro de prioridade para controlar a ordem na qual os filtros são avaliados.  
  
     O exemplo a seguir define a tabela de filtro e adiciona os filtros definidos anteriormente.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  Para avaliar as mensagens de entrada com os filtros contidos na tabela, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento. O exemplo a seguir demonstra a associação "filterTable1" com os pontos de extremidade de serviço:  
  
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
 [Serviços de roteamento](../../../../docs/framework/wcf/samples/routing-services.md)
