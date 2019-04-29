---
title: Filtros de mensagem
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: fc4656a76894eb3a844bc9f2187847fd9eff0ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785990"
---
# <a name="message-filters"></a>Filtros de mensagem
Para implementar o roteamento baseado em conteúdo, o serviço de roteamento usa <xref:System.ServiceModel.Dispatcher.MessageFilter> implementações que inspecionam a seções específicas de uma mensagem, como o endereço, nome do ponto de extremidade ou uma instrução XPath específica. Se nenhum dos filtros de mensagem fornecido com [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] às suas necessidades, você pode criar um filtro personalizado, criando uma nova implementação de base de <xref:System.ServiceModel.Dispatcher.MessageFilter> classe.  
  
 Ao configurar o serviço de roteamento, você deve definir os elementos de filtro (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objetos) que descrevem o tipo de **MessageFilter** e quaisquer dados de suporte necessários para criar o filtro, como valores de cadeia de caracteres específica para pesquisa para dentro da mensagem. Observe que apenas criar os elementos de filtro define os filtros de mensagem individual; Para usar os filtros para avaliar e rotear mensagens, você também deve definir uma tabela de filtro (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Cada entrada na tabela de filtros faz referência a um elemento de filtro e especifica o ponto de extremidade do cliente que uma mensagem será roteada para se a mensagem corresponde ao filtro. As entradas da tabela de filtro também permitem que você especifique uma coleção de pontos de extremidade de backup (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), que define uma lista de pontos de extremidade que a mensagem será transmitida em caso de falha de transmissão ao enviar para o ponto de extremidade primário. Esses pontos de extremidade serão tentados na ordem especificada até obter êxito.  
  
## <a name="message-filters"></a>Filtros de mensagem  
 Os filtros de mensagem usados pelo serviço de roteamento fornecem funcionalidade comum de seleção de mensagem, como avaliar o nome de uma mensagem foi enviada para a ação de SOAP, ou o endereço ou prefixo de endereço que a mensagem foi enviada para o ponto de extremidade. Filtros também podem ser adicionados com um `AND` de condição, para que as mensagens só serão roteadas para um ponto de extremidade se a mensagem corresponde a ambos os filtros. Você também pode criar filtros personalizados, criando sua própria implementação de <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 A seguinte tabela lista os <xref:System.ServiceModel.Routing.Configuration.FilterType> usados pelo serviço de roteamento, a classe que implementa o filtro de mensagem específica e a necessária <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parâmetros.  
  
|Tipo de filtro|Descrição|Filtrar o significado de dados|Filtro de exemplo|  
|------------------|-----------------|-------------------------|--------------------|  
|Ação|Usa o <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> classe para corresponder as mensagens que contém uma ação específica.|A ação a filtrar.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|EndpointAddress|Usa o <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> classe, com <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` para corresponder as mensagens que contém um endereço específico.|O endereço para filtrar após (no cabeçalho To).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|Usa o <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> classe, com <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` para corresponder as mensagens que contém um prefixo de endereço específico.|O endereço para filtrar usando a correspondência de prefixo mais longo.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|e|Usa o <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> classe que sempre avalia as duas condições antes de retornar.|filterData não é usado; em vez disso, Filtro1 e Filtro2 têm os nomes os filtros de mensagem correspondente (também na tabela), que deve ser **AND**ed juntos.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Personalizado|Um tipo definido pelo usuário que estende o <xref:System.ServiceModel.Dispatcher.MessageFilter> de classe e tem um construtor que recebe uma cadeia de caracteres.|O atributo customType é o nome de tipo totalmente qualificado da classe para criar; filterData é a cadeia de caracteres para passar para o construtor, ao criar o filtro.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|Usa o <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> classe para corresponder as mensagens com base no nome do ponto de extremidade de serviço que eles entravam no.|O nome do ponto de extremidade de serviço, por exemplo: "serviceEndpoint1".  Isso deve ser um dos pontos de extremidade expostos no serviço de roteamento.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Usa o <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> classe. Esse filtro corresponde a todas as mensagens que chegam.|filterData não é usado. Esse filtro sempre corresponderá a todas as mensagens.|\<filter name="matchAll1" filterType="MatchAll" />|  
|XPath|Usa o <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> classe para corresponder consultas XPath específicas dentro da mensagem.|A consulta XPath para usar ao fazer a correspondência de mensagens.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 O exemplo a seguir define as entradas de filtro que usam os filtros de mensagem de XPath, EndpointName e PrefixEndpointAddress. Este exemplo também demonstra como usar um filtro personalizado para as entradas RoundRobinFilter1 e RoundRobinFilter2.  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"   
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"   
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"   
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
>  Simplesmente definindo um filtro não faz com que as mensagens a ser avaliado com base no filtro. O filtro deve ser adicionado a uma tabela de filtro, que é então associado com o ponto de extremidade de serviço exposto pelo serviço de roteamento.  
  
### <a name="namespace-table"></a>Tabela de Namespace  
 Ao usar um filtro XPath, os dados de filtro que contém a consulta XPath podem se tornar extremamente grandes devido ao uso de namespaces. Para minimizar esse problema, o serviço de roteamento fornece a capacidade de definir seus próprio prefixos de namespace usando a tabela de namespace.  
  
 A tabela de namespace é uma coleção de <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objetos que define os prefixos de namespace para namespaces comuns que podem ser usados em um XPath. Estes são os prefixos de namespace e namespaces de padrão que estão contidos na tabela de namespace.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|suário|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Quando você souber que você usar um namespace específico em suas consultas XPath, você pode adicioná-lo à tabela de namespace, juntamente com um prefixo de namespace exclusivo e usar o prefixo em qualquer consulta XPath em vez do namespace completo. O exemplo a seguir define um prefixo de "custom" para o namespace `"http://my.custom.namespace"`, que é usado na consulta XPath contida em filterData.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtrar tabelas  
 Embora cada elemento de filtro define uma comparação lógica que pode ser aplicada a uma mensagem, a tabela de filtro fornece a associação entre o elemento de filtro e o ponto de extremidade de cliente de destino. Uma tabela de filtro é uma coleção nomeada de <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objetos que definem a associação entre um filtro, um ponto de extremidade de destino principal e uma lista de pontos de extremidade de backup alternativos. As entradas da tabela de filtro também permitem que você especifique uma prioridade opcional para cada condição de filtro. O exemplo a seguir define dois filtros e, em seguida, define uma tabela de filtro que associa cada filtro com um ponto de extremidade de destino.  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>      
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a>Prioridade de avaliação de filtro  
 Por padrão, todas as entradas na tabela de filtros são avaliadas simultaneamente, e a mensagem que está sendo avaliada é roteada para os pontos de extremidade associados a cada entrada de filtro correspondente. Se vários filtros forem avaliados como `true`e a mensagem é unidirecionais ou bidirecionais, a mensagem é multicast para os pontos de extremidade para todos os filtros correspondentes. Mensagens de solicitação / resposta não podem ser multicast, porque apenas uma resposta pode ser retornada ao cliente.  
  
 Lógica de roteamento mais complexa pode ser implementada com a especificação de níveis de prioridade para cada filtro; o serviço de roteamento avalia todos os filtros no nível de prioridade mais alto primeiro. Se uma mensagem corresponde a um filtro desse nível, nenhum filtro de uma prioridade mais baixa será processado. Por exemplo, uma mensagem de entrada unidirecional é avaliada primeiro em relação a todos os filtros com uma prioridade 2. A mensagem não corresponde qualquer filtro nesse nível de prioridade, então, em seguida que a mensagem é comparada com filtros com uma prioridade de 1. Dois filtros de prioridade 1 correspondem à mensagem e porque ele é uma mensagem unidirecional que ela é roteada para ambos os pontos de extremidade de destino.  Porque foi encontrada uma correspondência entre os filtros de prioridade 1, não há filtros de prioridade 0 são avaliados.  
  
> [!NOTE]
>  Se nenhuma prioridade for especificada, a prioridade padrão de 0 será usada.  
  
 O exemplo a seguir define uma tabela de filtro que especifica as prioridades de 2, 1 e 0 para os filtros referenciados na tabela.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"   
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"   
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"   
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"   
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 No exemplo anterior, se uma mensagem corresponder XPathFilter, ela será roteada para o roundingCalcEndpoint e sem filtros adicionais na tabela serão avaliados porque todos os outros filtros não são de uma prioridade mais baixa. No entanto, se a mensagem não corresponde ao Xpathfiltê-lo, em seguida, será avaliada em relação a todos os filtros de baixa prioridade, EndpointNameFilter e PrefixAddressFilter.  
  
> [!NOTE]
>  Quando possível, use filtros exclusivos em vez de especificar uma prioridade, porque a avaliação de prioridade pode resultar em degradação de desempenho.  
  
### <a name="backup-lists"></a>Listas de backup  
 Cada filtro na tabela de filtros pode opcionalmente especificar uma lista de backup, que é uma coleção nomeada de pontos de extremidade (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Esta coleção contém uma lista ordenada de pontos de extremidade que a mensagem será transmitida no caso de uma <xref:System.ServiceModel.CommunicationException> ao enviar para o ponto de extremidade primário especificado em <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. O exemplo a seguir define uma lista de backup denominada "backupServiceEndpoints" que contém dois pontos de extremidade.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 No exemplo anterior, se um envio para o ponto de extremidade primário "Destino" falhar, o serviço de roteamento tentará enviar para cada ponto de extremidade na sequência em que elas são listadas, o envio primeiro para backupServiceQueue e subsequentemente enviando para alternateServiceQueue se a Enviar para backupServiceQueue falhará. Se todos os pontos de extremidade de backup falharem, uma falha será retornada.
