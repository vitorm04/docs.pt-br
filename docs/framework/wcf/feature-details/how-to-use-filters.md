---
title: Como usar filtros
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94d45537ca3edd5f31f1ed31898857f002312a0b
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-filters"></a>Como usar filtros
Este tópico descreve as etapas básicas necessárias para criar uma configuração de roteamento que usa vários filtros. Neste exemplo, as mensagens são roteadas para duas implementações de um serviço de cálculo, regularCalc e roundingCalc. Suportam a ambas as implementações as mesmas operações; No entanto, um serviço Arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar. Um aplicativo cliente deve ser capaz de indicar se deseja usar a versão de arredondamento do serviço; Se nenhuma preferência de serviço é expresso em seguida, a mensagem é carga balanceada entre os dois serviços. As operações expostas por ambos os serviços são:  
  
-   Adicionar  
  
-   Subtração  
  
-   Multiplicar  
  
-   Divisão  
  
 Como os dois serviços implementam as mesmas operações, você não pode usar o filtro de ação, porque a ação especificada na mensagem não será exclusiva. Em vez disso, você deve fazer o trabalho adicional para garantir que as mensagens são roteadas para os pontos de extremidade apropriados.  
  
### <a name="determine-unique-data"></a>Determinar dados exclusivos  
  
1.  Como ambas as implementações do serviço lidar com as mesmas operações e são essencialmente idênticas diferente de dados que elas retornam, base dados contidos nas mensagens enviadas pelos aplicativos cliente não são exclusivos para que você possa determinar como rotear o solicitação. Mas, se o aplicativo cliente adiciona um valor de cabeçalho exclusivo para a mensagem, em seguida, você pode usar esse valor para determinar como a mensagem deve ser roteada.  
  
     Neste exemplo, se o aplicativo cliente precisa a mensagem a ser processado pelo cálculo de arredondamento, ele adiciona um cabeçalho personalizado usando o código a seguir:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Agora você pode usar o filtro XPath para inspecionar mensagens para esse cabeçalho e rotear mensagens que contém o cabeçalho para o serviço roundCalc.  
  
2.  Além disso, o serviço de roteamento expõe dois pontos de extremidade do serviço virtual que podem ser usados com EndpointName, EndpointAddress, ou PrefixEndpointAddress filtros para exclusivamente rotear mensagens de entrada para uma implementação de cálculo específica com base no ponto de extremidade para que o aplicativo cliente envia a solicitação.  
  
### <a name="define-endpoints"></a>Definir pontos de extremidade  
  
1.  Ao definir os pontos de extremidade usados pelo serviço de roteamento, você deve primeiro determinar a forma de canal usado por seus clientes e serviços. Nesse cenário de ambos os serviços de destino usam um padrão de solicitação-resposta, portanto, o <xref:System.ServiceModel.Routing.IRequestReplyRouter> é usado. O exemplo a seguir define os pontos de extremidade do serviço expostos pelo serviço de roteamento.  
  
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
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     Com essa configuração, o serviço de roteamento expõe três pontos de extremidade separados. Dependendo das opções de tempo de execução, o aplicativo cliente envia mensagens para um desses endereços. As mensagens que chegam a um dos pontos de extremidade de serviço "virtual" ("arredondamento/cálculo" ou "regular/cálculo") são encaminhadas para a implementação de calculadora correspondente. Se o aplicativo cliente não envia a solicitação para um ponto de extremidade específico, a mensagem é endereçada ao ponto de extremidade geral. Independentemente do ponto de extremidade escolhido, o aplicativo cliente também pode optar incluir o cabeçalho personalizado para indicar que a mensagem deve ser encaminhada para a implementação de cálculo de arredondamento.  
  
2.  O exemplo a seguir define os pontos de extremidade do cliente (destino) que o serviço de roteamento encaminha mensagens.  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     Esses pontos de extremidade são usados na tabela de filtro para indicar o ponto de extremidade de destino que a mensagem é enviada para quando ele corresponde a um filtro específico.  
  
### <a name="define-filters"></a>Definir filtros  
  
1.  Para rotear mensagens com base no cabeçalho personalizado "RoundingCalculator" o aplicativo cliente adiciona à mensagem, defina um filtro que usa uma consulta XPath para verificar a presença desse cabeçalho. Como esse cabeçalho é definido usando um namespace personalizado, também adicione uma entrada de namespace que define um prefixo de namespace personalizada de "custom", o que é usado na consulta XPath. O exemplo a seguir define a seção de roteamento necessária, a tabela de namespace e o filtro XPath.  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     Isso **MessageFilter** procura um cabeçalho RoundingCalculator na mensagem que contém um valor de "arredondamento". Esse cabeçalho é definido pelo cliente para indicar que a mensagem deve ser roteada para o serviço roundingCalc.  
  
    > [!NOTE]
    >  O prefixo de namespace /s12 é definido por padrão na tabela de namespace e representa o namespace "http://www.w3.org/2003/05/soap-envelope".  
  
2.  Você também deve definir filtros que procure as mensagens recebidas nos dois pontos de extremidade virtuais. O primeiro ponto de extremidade virtual é o ponto de extremidade "regular/cálculo". O cliente pode enviar solicitações para esse ponto de extremidade para indicar que a mensagem deve ser roteada para o serviço regularCalc. A configuração a seguir define um filtro que usa o <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> para determinar se a mensagem foi recebida por meio de um ponto de extremidade com o nome especificado em filterData.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Se uma mensagem é recebida pelo ponto de extremidade de serviço denominado "calculatorEndpoint", esse filtro é avaliada como `true`.  
  
3.  Em seguida, defina um filtro que procura por mensagens enviadas para o endereço do roundingEndpoint. O cliente pode enviar solicitações para esse ponto de extremidade para indicar que a mensagem deve ser roteada para o serviço roundingCalc. A configuração a seguir define um filtro que usa o <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> para determinar se a mensagem foi recebida no ponto de extremidade "arredondamento/cálculo".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Se uma mensagem é recebida em um endereço que começa com "http://localhost/routingservice/router/rounding/", esse filtro é avaliada como **true**. Como o endereço base usado por esta configuração é "http://localhost/routingservice/router" e o endereço especificado para o roundingEndpoint é "arredondamento/cálculo", o endereço completo usado para se comunicar com este ponto de extremidade é "http://localhost/ routingservice/roteador/arredondamento/cálculo", que corresponde a este filtro.  
  
    > [!NOTE]
    >  O filtro de PrefixEndpointAddress não avalia o nome de host ao executar uma correspondência, porque um único host pode ser chamado por meio de uma variedade de nomes de host que podem todos ser válidas maneiras de fazer referência ao host do aplicativo cliente. Por exemplo, todos os itens a seguir podem se referir ao mesmo host:  
    >   
    >  -   localhost  
    > -   127.0.0.1  
    > -   www.contoso.com  
    > -   ContosoWeb01  
  
4.  O filtro final deve oferecer suporte a roteamento de mensagens que chegam no ponto de extremidade geral sem o cabeçalho personalizado. Para este cenário, as mensagens devem alternar entre os serviços regularCalc e roundingCalc. Para dar suporte a "round robin" roteamento dessas mensagens, use um filtro personalizado que permite que uma instância de filtro para correspondência para cada mensagem processada.  O exemplo a seguir define duas instâncias de um RoundRobinMessageFilter, que são agrupados juntos para indicar que eles devem alternam entre si.  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     Durante o tempo de execução, esse tipo de filtro alterna entre todas as instâncias de filtro definido desse tipo que são configuradas como o mesmo grupo em uma coleção. Isso faz com que as mensagens processadas por esse filtro personalizado para alternar entre retornando `true` para RoundRobinFilter1 e RoundRobinFilter2.  
  
### <a name="define-filter-tables"></a>Definir filtro de tabelas  
  
1.  Para associar os filtros de pontos de extremidade de cliente específico, você deve colocá-los em uma tabela de filtro. Neste cenário de exemplo também usa as configurações de prioridade do filtro, que é uma configuração opcional que permite que você indique a ordem na qual os filtros são processados. Se nenhuma prioridade do filtro for especificada, todos os filtros serão avaliados simultaneamente.  
  
    > [!NOTE]
    >  Ao especificar uma prioridade de filtro permite que você controle a ordem na qual os filtros é processados, ele pode afetar negativamente o desempenho do serviço de roteamento. Quando possível, construa lógica do filtro de forma que o uso das prioridades de filtro não é necessário.  
  
     O exemplo a seguir define a tabela de filtro e adiciona "XPathFilter" definido anteriormente para a tabela com uma prioridade de 2. Essa entrada também especifica que, se "XPathFilter" corresponde a mensagem, a mensagem será roteada para "roundingCalcEndpoint"  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     Ao especificar uma prioridade de filtro, os filtros de prioridade mais altos são avaliados primeiro. Se corresponderem a um ou mais filtros em um nível de prioridade específica, não há filtros nos níveis de prioridade inferiores serão avaliados. Para este cenário, 2 é a prioridade mais alta especificada e esta é a entrada de filtro apenas neste nível.  
  
2.  Filtrar entradas foram definidas para verificar se uma mensagem é recebida em um ponto de extremidade específico ao inspecionar o nome do ponto de extremidade ou o prefixo de endereço. As seguintes entradas adicionar ambas essas entradas de filtro à tabela de filtro e associá-los com os pontos de extremidade de destino será roteada para a mensagem. Esses filtros são definidos para uma prioridade de 1 para indicar que eles seja executado somente se o filtro anterior do XPath não correspondeu a mensagem.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Como esses filtros têm uma prioridade de filtro de 1, eles só serão avaliados se o filtro no nível de prioridade 2 não coincide com a mensagem. Além disso, porque ambos os filtros tiverem o mesmo nível de prioridade que eles serão avaliados simultaneamente. Como ambos os filtros são mutuamente exclusivos, é possível para apenas um ou outro para corresponder a uma mensagem.  
  
3.  Se uma mensagem não corresponde a nenhum dos filtros anteriores, a mensagem foi recebida com o ponto de extremidade de serviço genérico e não contidos nenhuma informação de cabeçalho que indica onde roteá-la. Essas mensagens devem ser manipulados pelo filtro personalizado, que o balanceamento de carga-los entre os serviços de cálculo de dois. O exemplo a seguir demonstra como adicionar as entradas de filtro à tabela de filtro; cada filtro é associado a um dos pontos de extremidade de destino de dois.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Como essas entradas de especificar uma prioridade de 0, eles só serão avaliados se a mensagem não corresponde a nenhum filtro de uma prioridade mais alta. Além disso, já que ambos são da mesma prioridade, eles serão avaliados simultaneamente.  
  
     Conforme mencionado anteriormente, o filtro personalizado usado por essas definições de filtro é avaliada apenas uma ou outra como `true` para cada mensagem recebida. Como apenas dois filtros são definidos usando esse filtro, com a mesma configuração de grupo especificado, o efeito é que o serviço de roteamento alterna entre o envio para o regularCalcEndpoint e o RoundingCalcEndpoint.  
  
4.  Para avaliar mensagens com os filtros, a tabela de filtro deve primeiro ser associada com os pontos de extremidade de serviço que serão usados para receber mensagens.  O exemplo a seguir demonstra como associar a tabela de roteamento com os pontos de extremidade de serviço usando o comportamento de roteamento:  
  
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
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
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
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de roteamento](../../../../docs/framework/wcf/samples/routing-services.md)
