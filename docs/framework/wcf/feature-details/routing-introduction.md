---
title: Introdução ao roteamento
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 41545d0340ae222e427d1e6d428ed1e3f7b4fa76
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912487"
---
# <a name="routing-introduction"></a>Introdução ao roteamento
O serviço Routing fornece um SOAP conectável genérico que é capaz de roteamento de mensagens com base no conteúdo da mensagem intermediário. Com o serviço de roteamento, você pode criar lógica de roteamento complexa que permite implementar cenários como a agregação de serviço, controle de versão do serviço, roteamento de prioridades e roteamento de multicast. O serviço de roteamento também fornece a manipulação de erros permite que você configurar as listas de pontos de extremidade de backup, ao qual as mensagens são enviadas se ocorrer uma falha ao enviar para o ponto de extremidade de destino principal.  
  
 Este tópico é destinado para os novos para o serviço de roteamento e aborda a configuração básica e que hospeda o serviço de roteamento.  
  
## <a name="configuration"></a>Configuração  
 O serviço de roteamento é implementado como um serviço WCF que expõe um ou mais pontos de extremidade que recebem mensagens de aplicativos cliente e rotear as mensagens para um ou mais pontos de extremidade de destino. O serviço fornece um <xref:System.ServiceModel.Routing.RoutingBehavior>, que é aplicado a pontos de extremidade de serviço expostos pelo serviço. Esse comportamento é usado para configurar vários aspectos de como funciona o serviço. Para facilitar a configuração ao usar um arquivo de configuração, os parâmetros são especificados na **RoutingBehavior**. Em cenários com base no código, esses parâmetros seriam ser especificados como parte de um <xref:System.ServiceModel.Routing.RoutingConfiguration> objeto, que pode ser passado para um **RoutingBehavior**.  
  
 Ao iniciar, esse comportamento adiciona o <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, que é usado para executar o processamento SOAP das mensagens, para os pontos de extremidade do cliente. Isso permite que o serviço de roteamento transmitir mensagens para pontos de extremidade que requerem um diferentes **MessageVersion** que a mensagem foi recebida sobre o ponto de extremidade. O **RoutingBehavior** também registra uma extensão de serviço, o <xref:System.ServiceModel.Routing.RoutingExtension>, que fornece um ponto de acessibilidade para modificar a configuração do serviço de roteamento em tempo de execução.  
  
 O **RoutingConfiguration** classe fornece um meio consistente de configurar e atualizar a configuração do serviço de roteamento.  Ele contém parâmetros que atuam como as configurações para o serviço de roteamento e são usados para configurar o **RoutingBehavior** quando o serviço é iniciado, ou é passado para o **RoutingExtension** para modificar o roteamento configuração de tempo de execução.  
  
 A lógica de roteamento usada para executar o roteamento baseado em conteúdo de mensagens é definida pelo agrupamento de vários <xref:System.ServiceModel.Dispatcher.MessageFilter> objetos juntos para filtram tabelas (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objetos). Mensagens de entrada são avaliadas em relação os filtros de mensagem contidos na tabela de filtros e para cada **MessageFilter** que coincide com a mensagem encaminhada para um ponto de extremidade de destino. A tabela de filtro que deve ser usado para rotear mensagens é especificada usando o **RoutingBehavior** na configuração ou por meio de código usando o **RoutingConfiguration** objeto.  
  
### <a name="defining-endpoints"></a>Definir pontos de extremidade  
 Embora possa parecer que você deve iniciar a configuração definindo a lógica de roteamento que você usará, sua primeira etapa, na verdade, deve ser determinar a forma de você será o roteamento de mensagens para os pontos de extremidade. O serviço de roteamento usa contratos que definem a forma dos canais usados para receber e enviar mensagens e, portanto, a forma do canal de entrada deve corresponder do canal de saída.  Por exemplo, se você está roteando para pontos de extremidade que usam a forma de canal de solicitação-resposta, em seguida, você deve usar um contrato compatível com os pontos de extremidade de entrada, como o <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 Isso significa que, se seus pontos de extremidade de destino usam contratos com vários padrões de comunicação (por exemplo, a combinação de operações unidirecionais e bidirecionais), não é possível criar um ponto de extremidade de serviço único que pode receber e rotear mensagens para todos eles. Você deve determinar quais pontos de extremidade têm formas compatíveis e definem um ou mais pontos de extremidade que serão usados para receber mensagens a serem roteadas para os pontos de extremidade de destino.  
  
> [!NOTE]
> Ao trabalhar com contratos que especificam os vários padrões de comunicação (por exemplo, uma combinação de operações unidirecionais e bidirecionais), uma solução alternativa é usar um contrato duplex no serviço de roteamento, como <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. No entanto, isso significa que a associação deve ser capaz de comunicação duplex, o que pode não ser possível para todos os cenários. Em cenários em que isso não for possível, fatorar a comunicação em vários pontos de extremidade ou modificar o aplicativo pode ser necessário.  
  
 Para obter mais informações sobre contratos de roteamento, consulte [roteando contratos](routing-contracts.md).  
  
 Depois que o ponto de extremidade de serviço é definido, você pode usar o **RoutingBehavior** para associar a um determinado **RoutingConfiguration** com o ponto de extremidade. Ao configurar o serviço de roteamento usando um arquivo de configuração, o **RoutingBehavior** é usado para especificar a tabela de filtro que contém a lógica de roteamento usada para processar as mensagens recebidas neste ponto de extremidade. Se você estiver configurando o serviço de roteamento por meio de programação pode especificar a tabela de filtro usando o **RoutingConfiguration**.  
  
 O exemplo a seguir define pontos de extremidade do serviço e cliente que são usados pelo serviço de roteamento de forma programática e usando um arquivo de configuração.  
  
```xml  
    <services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 Este exemplo configura o serviço de roteamento para expor um ponto de extremidade com um endereço de `http://localhost:8000/routingservice/router`, que é usado para receber mensagens a serem roteadas. Porque as mensagens são roteadas para os pontos de extremidade de solicitação-resposta, o ponto de extremidade de serviço usa o <xref:System.ServiceModel.Routing.IRequestReplyRouter> contrato. Essa configuração também define um ponto de extremidade de cliente único `http://localhost:8000/servicemodelsample/service` que mensagens são roteadas. A tabela de filtro (não mostrada) chamada "routingTable1" contém a lógica de roteamento usada para rotear mensagens e é associada com o ponto de extremidade de serviço usando o **RoutingBehavior** (para um arquivo de configuração) ou  **RoutingConfiguration** (para a configuração programática).  
  
### <a name="routing-logic"></a>Lógica de roteamento  
 Para definir a lógica de roteamento usada para rotear mensagens, você deve determinar quais dados contidos em mensagens de entrada podem ser exclusivamente devidas ações sejam após. Por exemplo, se todos os pontos de destino você está roteando para compartilhar as mesmas ações de SOAP, o valor da ação contido dentro da mensagem não é um bom indicador de qual ponto de extremidade específico a mensagem deve ser roteada para. Se você exclusivamente deve rotear mensagens para um ponto de extremidade específico, você deve filtrar nos dados que identifica exclusivamente o ponto de extremidade de destino que a mensagem é roteada para.  
  
 O serviço Routing fornece várias **MessageFilter** implementações que inspecionam valores específicos dentro da mensagem, como o endereço, ação, nome do ponto de extremidade ou até mesmo uma consulta XPath. Se nenhuma dessas implementações atender às suas necessidades, você pode criar um personalizado **MessageFilter** implementação. Para obter mais informações sobre filtros de mensagem e uma comparação das implementações usada pelo serviço de roteamento, consulte [filtros de mensagem](message-filters.md) e [escolhendo um filtro](choosing-a-filter.md).  
  
 Vários filtros de mensagem são organizados em tabelas de filtro, que associar cada **MessageFilter** com um ponto de extremidade de destino. Opcionalmente, a tabela de filtro também pode ser usada para especificar uma lista de pontos de extremidade de backup que o serviço de roteamento tentará enviar a mensagem em caso de falha de transmissão.  
  
 Por padrão todos os filtros de mensagem dentro de uma tabela de filtro são avaliados simultaneamente; No entanto, você pode especificar um <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> que faz com que os filtros de mensagem a ser avaliada em uma ordem específica. Todas as entradas com a prioridade mais alta são avaliadas primeiro e filtros de mensagem de prioridades inferiores não são avaliados, se uma correspondência for encontrada em um nível de prioridade mais alta. Para obter mais informações sobre tabelas de filtro, consulte [filtros de mensagem](message-filters.md).  
  
 Os exemplos a seguir usam o <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, que é avaliado como `true` para todas as mensagens. Isso **MessageFilter** é adicionado à tabela de filtros "routingTable1", que associa a **MessageFilter** com o ponto de extremidade de cliente chamado "CalculatorService". O **RoutingBehavior** , em seguida, especifica que essa tabela deve ser usado para rotear mensagens processadas pelo ponto de extremidade de serviço.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  Por padrão, o serviço de roteamento de somente avalia os cabeçalhos da mensagem. Para permitir que os filtros acessar o corpo da mensagem, você deve definir <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> para `false`.  
  
 **Multicast**  
  
 Embora muitas configurações de serviço de roteamento usam lógica de filtro exclusivo que encaminha mensagens para apenas um ponto de extremidade específico, você precisa rotear uma mensagem específica para vários pontos de extremidade de destino. Como uma mensagem para vários destinos de difusão seletiva, as condições a seguir devem ser verdadeiras:  
  
- A forma de canal não deve ser de solicitação-resposta (embora podem ser unidirecionais ou bidirecionais,) porque apenas uma resposta pode ser recebida pelo aplicativo cliente em resposta à solicitação.  
  
- Vários filtros devem retornar `true` ao avaliar a mensagem.  
  
 Se essas condições forem atendidas, a mensagem é roteada para todos os pontos de extremidade de todos os filtros que são avaliadas como `true`. O exemplo a seguir define uma configuração de roteamento que resulta em mensagens sendo roteadas para os pontos de extremidade, se o endereço do ponto de extremidade na mensagem for `http://localhost:8000/routingservice/router/rounding`.  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### <a name="soap-processing"></a>Processamento SOAP  
 Para dar suporte a roteamento de mensagens entre os protocolos diferentes, o **RoutingBehavior** por padrão, adiciona o <xref:System.ServiceModel.Routing.SoapProcessingBehavior> para todos os pontos de extremidade do cliente que as mensagens são roteadas. Esse comportamento cria automaticamente uma nova **MessageVersion** antes de encaminhar a mensagem ao ponto de extremidade, bem como criar um monitor compatível com **MessageVersion** para qualquer documento de resposta antes de retorná-lo para o aplicativo cliente solicitante.  
  
 As etapas executadas para criar um novo **MessageVersion** para a mensagem de saída são da seguinte maneira:  
  
 **Processamento de solicitação**  
  
- Obter o **MessageVersion** da associação/canal de saída.  
  
- Obter o leitor de corpo da mensagem original.  
  
- Crie uma nova mensagem com a mesma ação, o leitor de corpo e um novo **MessageVersion**.  
  
- Se <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, copie o para, de FaultTo e os cabeçalhos RelatesTo para a nova mensagem.  
  
- Copie todas as propriedades de mensagem para a nova mensagem.  
  
- Store a mensagem de solicitação original a ser usado ao processar a resposta.  
  
- Retorna a nova mensagem de solicitação.  
  
 **Processamento da resposta**  
  
- Obter o **MessageVersion** da mensagem de solicitação original.  
  
- Obter o leitor de corpo da mensagem de resposta recebida.  
  
- Crie uma nova mensagem de resposta com a mesma ação, o leitor de corpo e o **MessageVersion** da mensagem de solicitação original.  
  
- Se <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, copie o para, de FaultTo e os cabeçalhos RelatesTo para a nova mensagem.  
  
- Copie as propriedades de mensagem para a nova mensagem.  
  
- Retorna a nova mensagem de resposta.  
  
 Por padrão, o **SoapProcessingBehavior** é adicionado automaticamente para os pontos de extremidade do cliente pelo <xref:System.ServiceModel.Routing.RoutingBehavior> quando o serviço é iniciado; no entanto, você pode controlar se o processamento SOAP é adicionado a todos os pontos de extremidade do cliente usando o <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> propriedade. Você também pode adicionar o comportamento diretamente para um ponto de extremidade específico e habilitar ou desabilitar esse comportamento no nível do ponto de extremidade, se um controle mais granular do processamento SOAP é necessário.  
  
> [!NOTE]
>  Se o processamento SOAP está desabilitado para um ponto de extremidade requer uma MessageVersion diferente da mensagem de solicitação original, você deve fornecer um mecanismo personalizado para executar modificações de SOAP que são necessárias antes de enviar a mensagem para o ponto de extremidade de destino.  
  
 Nos exemplos a seguir, o **soapProcessingEnabled** propriedade é usada para impedir que o **SoapProcessingBehavior** sejam adicionados automaticamente a todos os pontos de extremidade do cliente.  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### <a name="dynamic-configuration"></a>Configuração dinâmica  
 Quando você adicionar pontos de extremidade de cliente adicionais ou precisa modificar os filtros que são usadas para rotear mensagens, você deve ter uma maneira de atualizar a configuração dinamicamente em tempo de execução para evitar interromper o serviço para os pontos de extremidade recebendo mensagens por meio de o serviço de roteamento. Modificar um arquivo de configuração ou o código do aplicativo host nem sempre é suficiente, pois qualquer um dos métodos exige que o aplicativo, o que poderia levar a perda potencial de todas as mensagens atualmente em trânsito e o potencial para tempo de inatividade durante a reciclagem Aguardando o serviço seja reiniciado.  
  
 Você pode modificar apenas o **RoutingConfiguration** programaticamente. Embora inicialmente, você pode configurar o serviço usando um arquivo de configuração, você só pode modificar a configuração de tempo de execução, criando um novo **RoutingConfigution** e passá-lo como um parâmetro para o <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> método exposto pelo <xref:System.ServiceModel.Routing.RoutingExtension> extensão de serviço. Todas as mensagens em trânsito no momento continuam a ser roteado usando a configuração anterior, enquanto as mensagens recebidas após a chamada para **ApplyConfiguration** usar a nova configuração. O exemplo a seguir demonstra como criar uma instância do serviço Roteamento e, em seguida, posteriormente, modificando a configuração.  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  Ao atualizar o serviço de roteamento dessa maneira só é possível passar uma nova configuração. Não é possível modificar apenas selecionar elementos da configuração atual ou acrescentar novas entradas para a configuração atual. Você deve criar e passar uma nova configuração que substituirá o existente.  
  
> [!NOTE]
>  Todas as sessões abertas usando a configuração anterior continuam usando a configuração anterior. A nova configuração só é usada por novas sessões.  
  
## <a name="error-handling"></a>Tratamento de erros  
 Se houver <xref:System.ServiceModel.CommunicationException> é encontrado ao tentar enviar uma mensagem, é feita de tratamento de erros. Normalmente, essas exceções indicam que um problema foi encontrado ao tentar se comunicar com o ponto de extremidade do cliente definido como um <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, ou <xref:System.ServiceModel.CommunicationObjectFaultedException>. O código de tratamento de erro também irá capturar e tentar novamente enviar quando uma <xref:System.TimeoutException> ocorrer, que é outra exceção comuns que não é derivada de **CommunicationException**.  
  
 Quando uma das exceções anteriores ocorre, o serviço de roteamento de failover para uma lista de pontos de extremidade de backup. Se todos os pontos de extremidade de backup falharem com uma falha de comunicação, ou se um ponto de extremidade retornará uma exceção que indica uma falha no serviço de destino, o serviço de roteamento retornará uma falha para o aplicativo cliente.  
  
> [!NOTE]
>  A funcionalidade de tratamento de erros captura e manipula as exceções que ocorrem ao tentar enviar uma mensagem e ao tentar fechar um canal. O código de tratamento de erros não se destina a detectar ou lidar com exceções criadas pelos pontos de extremidade de aplicativo está se comunicando com; uma <xref:System.ServiceModel.FaultException> gerada por um serviço é exibido no serviço de roteamento como um **FaultMessage** e flui para o cliente.  
>   
>  Se ocorrer um erro quando o serviço de roteamento tenta retransmitir uma mensagem, você poderá receber um <xref:System.ServiceModel.FaultException> no lado do cliente, em vez de um <xref:System.ServiceModel.EndpointNotFoundException> normalmente obtidas na ausência do serviço de roteamento. Um serviço de roteamento pode mascarar, portanto, exceções e não fornecer transparência total, a menos que você examinar as exceções aninhadas.  
  
### <a name="tracing-exceptions"></a>Exceções de rastreamento  
 Ao enviar uma mensagem para um ponto de extremidade em uma lista falhar, o serviço de roteamento rastreia os dados de exceção resultante e anexa os detalhes da exceção como uma propriedade de mensagem chamada **exceções**. Isso preserva os dados de exceção e permite acesso programático a um usuário por meio de um Inspetor de mensagens.  Os dados de exceção são armazenados por mensagem em um dicionário que mapeia o nome do ponto de extremidade para os detalhes da exceção encontrados ao tentar enviar uma mensagem a ele.  
  
### <a name="backup-endpoints"></a>Pontos de extremidade de backup  
 Cada entrada de filtro dentro da tabela de filtro pode opcionalmente especificar uma lista de pontos de extremidade de backup, que são usados em caso de falha de transmissão ao enviar para o ponto de extremidade primário. Se essa falha ocorrer, o serviço de roteamento tenta transmitir a mensagem para a primeira entrada na lista de ponto de extremidade de backup. Se essa tentativa de envio também encontra uma falha de transmissão, o próximo ponto de extremidade da lista de backups é tentado. O serviço de roteamento continua enviando a mensagem para cada ponto de extremidade na lista até que a mensagem é recebida com êxito, todos os pontos de extremidade de retornam uma falha de transmissão ou uma falha de transmissão não é retornada por um ponto de extremidade.  
  
 Os exemplos a seguir configuram o serviço de roteamento de mensagens para usar uma lista de backup.  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### <a name="supported-error-patterns"></a>Padrões de erro com suporte  
 A tabela a seguir descreve os padrões que são compatíveis com o uso de listas de ponto de extremidade de backup, junto com anotações que descrevem os detalhes de tratamento de erros para padrões específicos.  
  
|Padrão|Session|Transação|Contexto de recebimento|Lista de backup com suporte|Observações|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Unidirecional||||Sim|Tenta enviar a mensagem em um ponto de extremidade de backup novamente. Se esta mensagem está sendo multicast, somente a mensagem no canal com falha é movida para o seu destino de backup.|  
|Unidirecional||✓||Não|Uma exceção é lançada e a transação será revertida.|  
|Unidirecional|||✓|Sim|Tenta enviar a mensagem em um ponto de extremidade de backup novamente. Depois que a mensagem é recebida com êxito e completa todos recebem contextos. Se a mensagem não for recebida com êxito por qualquer ponto de extremidade, não conclua o contexto de recebimento.<br /><br /> Quando essa mensagem está sendo multicast, o contexto de recebimento é preenchido somente se a mensagem é recebida com êxito pelo menos um ponto de extremidade (primário ou backup). Se nenhum dos pontos de extremidade em qualquer um dos caminhos de multicast com êxito a mensagem, não conclua o contexto de recebimento.|  
|Unidirecional||✓|✓|Sim|Anular a transação anterior, crie uma nova transação e reenviar todas as mensagens. Mensagens de erro são transmitidas para um destino de backup.<br /><br /> Após uma transação ter sido criada no qual todas as transmissões de êxito, conclua os contextos de recebimento em confirmar a transação.|  
|Unidirecional|✓|||Sim|Tenta enviar a mensagem em um ponto de extremidade de backup novamente. Em um cenário de multicast somente as mensagens em uma sessão que encontrou um erro ou em uma sessão fechar cuja sessão falhado são reenviadas para destinos de backup.|  
|Unidirecional|✓|✓||Não|Uma exceção é lançada e a transação será revertida.|  
|Unidirecional|✓||✓|Sim|Tenta enviar a mensagem em um ponto de extremidade de backup novamente. Depois que todos os envios concluída sem erros de mensagem, a sessão não indica mais nenhuma mensagem e o serviço de roteamento é fechada com êxito todos os canais de sessão de saída, receberiam por todos os contextos são concluídos, e o canal de sessão de entrada é fechado.|  
|Unidirecional|✓|✓|✓|Sim|Anular a transação atual e crie um novo. Reenvie todas as mensagens anteriores na sessão. Depois de uma transação foi criada no qual todas as mensagens têm foi enviadas com êxito e a sessão indica que não há mais mensagens, todos os canais de sessão de saída são fechados, recebem contextos são concluídos com a transação, é o canal de sessão de entrada fechado, e a transação é confirmada.<br /><br /> Quando as sessões estão sendo multicast as mensagens que não tiveram nenhum erro são reenviadas para o mesmo destino como antes e as mensagens que encontrou um erro é enviada para destinos de backup.|  
|Bidirecional||||Sim|Envie para um destino de backup.  Depois que um canal de retorna uma mensagem de resposta, retorne a resposta ao cliente original.|  
|Bidirecional|✓|||Sim|Envie todas as mensagens no canal para um destino de backup.  Depois que um canal de retorna uma mensagem de resposta, retorne a resposta ao cliente original.|  
|Bidirecional||✓||Não|Uma exceção é lançada e a transação será revertida.|  
|Bidirecional|✓|✓||Não|Uma exceção é lançada e a transação será revertida.|  
|Duplex||||Não|No momento, não há suporte para a comunicação dúplex de sessão não.|  
|Duplex|✓|||Sim|Envie para um destino de backup.|  
  
## <a name="hosting"></a>Hospedagem  
 Como o serviço de roteamento é implementado como um serviço WCF, ele deve ser auto-hospedado dentro de um aplicativo ou hospedado pelo IIS ou WAS. É recomendável que o serviço de roteamento ser hospedado em IIS, WAS ou um aplicativo de serviço do Windows para aproveitar a inicialização automática e disponível nestes ambientes de hospedagem de recursos de gerenciamento de ciclo de vida.  
  
 O exemplo a seguir demonstra que hospeda o serviço de roteamento em um aplicativo.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Para hospedar o serviço de roteamento de mensagens dentro do IIS ou WAS, você deve criar um arquivo de serviço (. svc) ou usar a ativação baseada em configuração do serviço. Ao usar um arquivo de serviço, você deve especificar o <xref:System.ServiceModel.Routing.RoutingService> usando o parâmetro de serviço. O exemplo a seguir contém um arquivo de serviço de exemplo que pode ser usado para hospedar o serviço de roteamento com o IIS ou WAS.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Representação e serviço de roteamento  
 O serviço de roteamento de WCF pode ser usado com a representação para envio e recebimento de mensagens. Todas as restrições de Windows usual de representação se aplicam. Se seria necessário configurar as permissões de serviço ou a conta para usar a representação ao escrever seu próprio serviço, você terá de fazer essas mesmas etapas para usar a representação com o serviço de roteamento. Para obter mais informações, consulte [delegação e representação](delegation-and-impersonation-with-wcf.md).  
  
 A representação com o serviço de roteamento requer o uso de personificação do ASP.NET no modo de compatibilidade do ASP.NET ou o uso de credenciais do Windows que foram configurados para permitir a representação. Para obter mais informações sobre o modo de compatibilidade do ASP.NET, consulte [serviços WCF e ASP.NET](wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  O serviço de roteamento do WCF não dá suporte à representação com a autenticação básica.  
  
 Para usar a representação do ASP.NET com o serviço de roteamento, habilite o modo de compatibilidade do ASP.NET no serviço do ambiente de hospedagem. O serviço de roteamento já foi marcado como permitir a representação e modo de compatibilidade do ASP.NET serão habilitados automaticamente. A representação é o único uso com suporte de integração do ASP.NET com o serviço de roteamento.  
  
 Usar a representação de credencial do Windows com o serviço de roteamento que você precisa configurar as credenciais e o serviço. O objeto de credenciais do cliente (<xref:System.ServiceModel.Security.WindowsClientCredential>, está acessível do <xref:System.ServiceModel.ChannelFactory>) define um <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade que deve ser definida para permitir a representação. Por fim, no serviço que você precisa configurar o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> comportamento para definir `ImpersonateCallerForAllOperations` para `true`. O serviço de roteamento usa esse sinalizador para decidir se deseja criar os clientes para encaminhamento de mensagens com a representação habilitada.  
  
## <a name="see-also"></a>Consulte também

- [Filtros de mensagem](message-filters.md)
- [Roteando contratos](routing-contracts.md)
- [Escolhendo um filtro](choosing-a-filter.md)
