---
title: Como usar filtros
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 34ea961b0ef5db51efcae0b86f2c06171d6d756c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464108"
---
# <a name="how-to-use-filters"></a>Como usar filtros
Este tópico descreve as etapas básicas necessárias para criar uma configuração de roteamento que usa vários filtros. Neste exemplo, as mensagens são encaminhadas para duas implementações de um serviço de calculadora, regularCalc e roundingCalc. Ambas as implementações suportam as mesmas operações; no entanto, um serviço arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar. Um aplicativo cliente deve ser capaz de indicar se deve usar a versão de arredondamento do serviço; se nenhuma preferência de serviço for expressa, então a mensagem é equilibrada entre os dois serviços. As operações expostas por ambos os serviços são:  
  
- Adicionar  
  
- Subtrair  
  
- Multiplicar  
  
- Dividir  
  
 Como ambos os serviços implementam as mesmas operações, você não pode usar o filtro Ação, porque a ação especificada na mensagem não será única. Em vez disso, você deve fazer um trabalho adicional para garantir que as mensagens sejam encaminhadas para os pontos finais apropriados.  
  
### <a name="determine-unique-data"></a>Determinar dados únicos  
  
1. Como ambas as implementações de serviço lidam com as mesmas operações e são essencialmente idênticas aos dados que retornam, os dados base contidos nas mensagens enviadas dos aplicativos do cliente não são únicos o suficiente para permitir que você determine como direcionar a solicitação. Mas se o aplicativo cliente adicionar um valor de cabeçalho único à mensagem, então você pode usar esse valor para determinar como a mensagem deve ser roteada.  
  
     Para este exemplo, se o aplicativo cliente precisar que a mensagem seja processada pela calculadora de arredondamento, ele adiciona um cabeçalho personalizado usando o seguinte código:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Agora você pode usar o filtro XPath para inspecionar mensagens para este cabeçalho e encaminhar mensagens contendo o cabeçalho para o serviço roundCalc.  
  
2. Além disso, o Serviço de Roteamento expõe dois pontos finais de serviço virtuais que podem ser usados com os filtros EndpointName, EndpointAddress ou PrefixEndpointAddress para direcionar exclusivamente mensagens recebidas para uma implementação de calculadora específica com base no ponto final ao qual o aplicativo cliente envia a solicitação.  
  
### <a name="define-endpoints"></a>Definir pontos finais  
  
1. Ao definir os pontos finais usados pelo Serviço de Roteamento, você deve primeiro determinar a forma do canal usado por seus clientes e serviços. Neste cenário, ambos os serviços de destino utilizam <xref:System.ServiceModel.Routing.IRequestReplyRouter> um padrão de solicitação-resposta, de modo que o é usado. O exemplo a seguir define os pontos finais de serviço expostos pelo Serviço de Roteamento.  
  
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
  
     Com essa configuração, o Serviço de Roteamento expõe três pontos finais separados. Dependendo das escolhas de tempo de execução, o aplicativo cliente envia mensagens para um desses endereços. As mensagens que chegam a um dos pontos finais de serviço "virtuais" ("arredondamento/calculadora" ou "regular/calculadora") são encaminhadas para a implementação da calculadora correspondente. Se o aplicativo cliente não enviar a solicitação para um ponto final específico, a mensagem será endereçada ao ponto final geral. Independentemente do ponto final escolhido, o aplicativo cliente também pode optar por incluir o cabeçalho personalizado para indicar que a mensagem deve ser encaminhada para a implementação da calculadora de arredondamento.  
  
2. O exemplo a seguir define os pontos finais do cliente (destino) para os quais o Serviço de Roteamento encaminha mensagens.  
  
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
  
     Esses pontos finais são usados na tabela de filtros para indicar o ponto final de destino para o qual a mensagem é enviada quando corresponde a um filtro específico.  
  
### <a name="define-filters"></a>Definir Filtros  
  
1. Para direcionar mensagens com base no cabeçalho personalizado "RoundingCalculator" que o aplicativo cliente adiciona à mensagem, defina um filtro que usa uma consulta XPath para verificar a presença deste cabeçalho. Como este cabeçalho é definido usando um namespace personalizado, adicione também uma entrada de namespace que define um prefixo de namespace personalizado de "personalizado" que é usado na consulta XPath. O exemplo a seguir define a seção de roteamento necessária, a tabela namespace e o filtro XPath.  
  
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
  
     Este **MessageFilter** procura um cabeçalho de RoundingCalculator na mensagem que contém um valor de "arredondamento". Este cabeçalho é definido pelo cliente para indicar que a mensagem deve ser encaminhada para o serviço de arredondamentoCalc.  
  
    > [!NOTE]
    > O prefixo s12 namespace é definido por padrão na tabela `http://www.w3.org/2003/05/soap-envelope`namespace e representa o namespace .
  
2. Você também deve definir filtros que procurem mensagens recebidas nos dois pontos finais virtuais. O primeiro ponto final virtual é o ponto final "regular/calculadora". O cliente pode enviar solicitações para este ponto final para indicar que a mensagem deve ser encaminhada para o serviço regularCalc. A configuração a seguir define <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> um filtro que usa o para determinar se a mensagem chegou através de um ponto final com o nome especificado no filterData.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Se uma mensagem for recebida pelo ponto final do serviço chamado `true`"calculatorEndpoint", este filtro será avaliado para .  
  
3. Em seguida, defina um filtro que procure mensagens enviadas para o endereço do roundingEndpoint. O cliente pode enviar solicitações para este ponto final para indicar que a mensagem deve ser encaminhada para o serviço de arredondamentoCalc. A configuração a seguir define <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> um filtro que usa o para determinar se a mensagem chegou ao ponto final "arredondamento/calculadora".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Se uma mensagem for recebida `http://localhost/routingservice/router/rounding/` em um endereço que começa com então este filtro avaliará como **verdadeiro**. Como o endereço base usado `http://localhost/routingservice/router` por essa configuração é e o endereço especificado para o arredondamentoEndpoint é `http://localhost/routingservice/router/rounding/calculator`"arredondamento/calculadora", o endereço completo usado para se comunicar com este ponto final é , o que corresponde a este filtro.  
  
    > [!NOTE]
    > O filtro PrefixEndpointAddress não avalia o nome do host ao executar uma partida, porque um único host pode ser referido usando uma variedade de nomes de host que podem ser formas válidas de se referir ao host a partir do aplicativo cliente. Por exemplo, todos os seguintes podem se referir ao mesmo host:  
    >
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. O filtro final deve suportar o roteamento de mensagens que chegam ao ponto final geral sem o cabeçalho personalizado. Para este cenário, as mensagens devem alternar entre os serviços regulares Calc e RoundingCalc. Para suportar o roteamento "round robin" dessas mensagens, use um filtro personalizado que permite que uma instância de filtro corresponda a cada mensagem processada.  O seguinte define duas instâncias de um RoundRobinMessageFilter, que são agrupadas para indicar que devem alternar entre si.  
  
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
  
     Durante o tempo de execução, este tipo de filtro alterna entre todas as instâncias de filtro definidas deste tipo que são configuradas como o mesmo grupo em uma coleção. Isso faz com que as mensagens processadas `true` `RoundRobinFilter1` por `RoundRobinFilter2`este filtro personalizado se alternam entre o retorno para e .  
  
### <a name="define-filter-tables"></a>Definir tabelas de filtro  
  
1. Para associar os filtros a pontos finais específicos do cliente, você deve colocá-los dentro de uma tabela de filtros. Este cenário de exemplo também usa configurações de prioridade de filtro, que é uma configuração opcional que permite indicar a ordem em que os filtros são processados. Se nenhuma prioridade de filtro for especificada, todos os filtros serão avaliados simultaneamente.  
  
    > [!NOTE]
    > Embora a especificação de uma prioridade de filtro permita controlar a ordem na qual os filtros são processados, isso pode afetar negativamente o desempenho do Serviço de Roteamento. Quando possível, construa a lógica do filtro para que o uso de prioridades de filtro não seja necessário.  
  
     O seguinte define a tabela do filtro e adiciona o "XPathFilter" definido anteriormente à tabela com uma prioridade de 2. Esta entrada também especifica `XPathFilter` que se a mensagem corresponder, `roundingCalcEndpoint`a mensagem será encaminhada para o .  
  
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
          </filterTables>  
    </routing>  
    ```  
  
     Ao especificar uma prioridade de filtro, os filtros de maior prioridade são avaliados primeiro. Se um ou mais filtros em um nível de prioridade específico corresponderem, nenhum filtro em níveis de prioridade mais baixos será avaliado. Para este cenário, 2 é a maior prioridade especificada e esta é a única entrada de filtro neste nível.  
  
2. As entradas do filtro foram definidas para verificar se uma mensagem é recebida em um ponto final específico inspecionando o nome do ponto final ou o prefixo de endereço. As seguintes entradas adicionam ambas as entradas do filtro à tabela de filtros e as associam aos pontos finais de destino para os os qual a mensagem será roteada. Esses filtros são definidos como uma prioridade de 1 para indicar que eles só devem ser executados se o filtro XPath anterior não corresponder à mensagem.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Como esses filtros têm uma prioridade de filtro de 1, eles só serão avaliados se o filtro no nível de prioridade 2 não corresponder à mensagem. Além disso, como ambos os filtros têm o mesmo nível de prioridade, eles serão avaliados simultaneamente. Como ambos os filtros são mutuamente exclusivos, é possível que apenas um ou outro corresponda a uma mensagem.  
  
3. Se uma mensagem não corresponder a nenhum dos filtros anteriores, a mensagem foi recebida através do ponto final do serviço genérico e não continha informações de cabeçalho que indicassem para onde encaminhá-la. Essas mensagens devem ser manuseadas pelo filtro personalizado, que as equilibra entre os dois serviços de calculadora. O exemplo a seguir demonstra como adicionar as entradas do filtro à tabela do filtro; cada filtro está associado a um dos dois pontos finais de destino.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Como essas entradas especificam uma prioridade de 0, elas só serão avaliadas se nenhum filtro de uma prioridade maior corresponder à mensagem. Além disso, como ambos são da mesma prioridade, são avaliados simultaneamente.  
  
     Como mencionado anteriormente, o filtro personalizado usado por essas definições `true` de filtro apenas avalia uma ou outra como para cada mensagem recebida. Como apenas dois filtros são definidos usando este filtro, com a mesma configuração de grupo especificada, o efeito é que o Serviço de Roteamento alterna entre o envio para o CalcEndpoint regular e o RoundingCalcEndpoint.  
  
4. Para avaliar as mensagens contra os filtros, a tabela de filtros deve primeiro ser associada aos pontos finais de serviço que serão usados para receber mensagens.  O exemplo a seguir demonstra como associar a tabela de roteamento com os pontos finais do serviço usando o comportamento de roteamento:  
  
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
  
## <a name="see-also"></a>Confira também

- [Serviços de roteamento](../../../../docs/framework/wcf/samples/routing-services.md)
