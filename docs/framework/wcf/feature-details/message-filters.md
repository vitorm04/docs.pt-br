---
title: Filtros de mensagem
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a953dea9224d75907c593d87f06a0b0888f0af2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184670"
---
# <a name="message-filters"></a>Filtros de mensagem
Para implementar o roteamento baseado em <xref:System.ServiceModel.Dispatcher.MessageFilter> conteúdo, o Serviço de Roteamento usa implementações que inspecionam seções específicas de uma mensagem, como endereço, nome de ponto final ou uma instrução XPath específica. Se nenhum dos filtros de [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] mensagem fornecidos atender às suas necessidades, você <xref:System.ServiceModel.Dispatcher.MessageFilter> pode criar um filtro personalizado criando uma nova implementação da classe base.  
  
 Ao configurar o Serviço de Roteamento,<xref:System.ServiceModel.Routing.Configuration.FilterElement> você deve definir elementos de filtro (objetos) que descrevem o tipo de **MessageFilter** e quaisquer dados de suporte necessários para criar o filtro, como valores de seqüência específicos para procurar dentro da mensagem. Observe que a criação dos elementos do filtro define apenas os filtros de mensagem individuais; para usar os filtros para avaliar e encaminhar mensagens, você também deve definir uma tabela de filtros (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Cada entrada na tabela de filtro faz referência a um elemento de filtro e especifica o ponto final do cliente para o qual uma mensagem será encaminhada se a mensagem corresponder ao filtro. As entradas da tabela de filtro também permitem<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>especificar uma coleção de pontos finais de backup ( ), que define uma lista de pontos finais para os quais a mensagem será transmitida no caso de uma falha de transmissão ao enviar para o ponto final principal. Esses pontos finais serão julgados na ordem especificada até que se tenha sucesso.  
  
## <a name="message-filters"></a>Filtros de mensagem  
 Os filtros de mensagem usados pelo Serviço de Roteamento fornecem funcionalidade de seleção de mensagens comuns, como avaliar o nome do ponto final para o que uma mensagem foi enviada, a ação SOAP ou o prefixo de endereço ou endereço para o que a mensagem foi enviada. Os filtros também podem `AND` ser unidos com uma condição, de modo que as mensagens só serão roteadas para um ponto final se a mensagem corresponder a ambos os filtros. Você também pode criar filtros personalizados <xref:System.ServiceModel.Dispatcher.MessageFilter>criando sua própria implementação de .  
  
 A tabela a <xref:System.ServiceModel.Routing.Configuration.FilterType> seguir lista o usado pelo Serviço de Roteamento, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> a classe que implementa o filtro de mensagem específico e os parâmetros necessários.  
  
|Tipo de filtro|Descrição|Significado dos dados do filtro|Filtro de exemplo|  
|------------------|-----------------|-------------------------|--------------------|  
|Ação|Usa <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> a classe para corresponder mensagens que contêm uma ação específica.|A ação para filtrar.|\<nome do filtro="action1" filterType="Action"http://namespace/contract/operationfilterData=" />|  
|EndpointAddress|Usa <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> a classe, com <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` mensagens compatíveis contendo um endereço específico.|O endereço a ser filtrado (no cabeçalho Para)|\<nome do filtro="endereço1" filtroType="EndpointAddress"http://host/vdir/s.svc/bfilterData=" />|  
|Ponto finalEndereçoPrefix|Usa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> a classe, com <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` mensagens compatíveis contendo um prefixo de endereço específico.|O endereço a ser filtrado ao usar a correspondência de prefixo mais longa.|\<nome do filtro="prefix1" filterType="EndpointAddressPrefix"http://host/filterData=" />|  
|And|Usa <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> a classe que sempre avalia ambas as condições antes de retornar.|filterData não é usado; em vez disso, o filtro1 e o filtro2 têm os nomes dos filtros de mensagem correspondentes (também na tabela), que devem ser **e**ed juntos.|\<nome do filtro="e1" filtroType="E" filtro1="endereço1" filtro2="action1" />|  
|Personalizado|Um tipo definido pelo <xref:System.ServiceModel.Dispatcher.MessageFilter> usuário que estende a classe e tem um construtor pegando uma corda.|O atributo customType é o nome de tipo totalmente qualificado da classe a ser criado; filterData é a string para passar para o construtor ao criar o filtro.|\<nome do filtro=filtro "custom1"Type="Personalizado" costumeType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|Usa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> a classe para combinar mensagens com base no nome do ponto final do serviço em que eles chegaram.|O nome do ponto final do serviço, por exemplo: "serviceEndpoint1".  Este deve ser um dos pontos finais expostos no Serviço de Roteamento.|\<nome do filtro=filtro "stock1"Type="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Usa <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> a classe. Este filtro corresponde a todas as mensagens que chegam.|filterData não é usado. Este filtro sempre corresponderá a todas as mensagens.|\<nome do filtro="matchAll1" filterType="MatchAll" />|  
|XPath|Usa <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> a classe para corresponder a consultas específicas do XPath na mensagem.|A consulta XPath para usar ao combinar mensagens.|\<nome do filtro=filtro "XPath1"Type="XPath" filterData="//ns:element" />|  
  
 O exemplo a seguir define entradas de filtro que usam os filtros de mensagem XPath, EndpointName e PrefixEndpointAddress. Este exemplo também demonstra o uso de um filtro personalizado para as entradas RoundRobinFilter1 e RoundRobinFilter2.  
  
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
> A simples definição de um filtro não faz com que as mensagens sejam avaliadas contra o filtro. O filtro deve ser adicionado a uma tabela de filtros, que está então associada ao ponto final de serviço exposto pelo Serviço de Roteamento.  
  
### <a name="namespace-table"></a>Tabela de namespace  
 Ao usar um filtro XPath, os dados do filtro que contém a consulta XPath podem se tornar extremamente grandes devido ao uso de namespaces. Para aliviar esse problema, o Serviço de Roteamento oferece a capacidade de definir seus próprios prefixos de namespace usando a tabela namespace.  
  
 A tabela namespace é <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> uma coleção de objetos que define os prefixos namespace para espaços de nome comuns que podem ser usados em um XPath. A seguir estão os namespaces padrão e os prefixos namespace que estão contidos na tabela namespace.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|Sor|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Quando você sabe que estará usando um namespace específico em suas consultas XPath, você pode adicioná-lo à tabela namespace juntamente com um prefixo de namespace exclusivo e usar o prefixo em qualquer consulta XPath em vez do namespace completo. O exemplo a seguir define um prefixo `"http://my.custom.namespace"`de "personalizado" para o namespace , que é então usado na consulta XPath contida no filterData.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Tabelas de filtro  
 Embora cada elemento do filtro defina uma comparação lógica que pode ser aplicada a uma mensagem, a tabela de filtro fornece a associação entre o elemento filtro e o ponto final do cliente de destino. Uma tabela de filtroé <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> uma coleção nomeada de objetos que definem a associação entre um filtro, um ponto final de destino principal e uma lista de pontos finais de backup alternativos. As entradas da tabela de filtro também permitem especificar uma prioridade opcional para cada condição do filtro. O exemplo a seguir define dois filtros e, em seguida, define uma tabela de filtros que associa cada filtro a um ponto final de destino.  
  
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
  
### <a name="filter-evaluation-priority"></a>Prioridade de avaliação de filtros  
 Por padrão, todas as entradas na tabela de filtro saem avaliadas simultaneamente e a mensagem que está sendo avaliada é encaminhada para os pontos finais associados a cada entrada do filtro correspondente. Se vários filtros `true`avaliarem e a mensagem for unidirecional ou duplex, a mensagem será multicast para os pontos finais para todos os filtros correspondentes. As mensagens de solicitação e resposta não podem ser multicast porque apenas uma resposta pode ser devolvida ao cliente.  
  
 Uma lógica de roteamento mais complexa pode ser implementada especificando níveis de prioridade para cada filtro; o Serviço de Roteamento avalia todos os filtros no nível de prioridade mais alto primeiro. Se uma mensagem corresponder a um filtro deste nível, nenhum filtro de uma prioridade inferior será processado. Por exemplo, uma mensagem unidirecional de entrada é avaliada primeiro contra todos os filtros com prioridade de 2. A mensagem não corresponde a nenhum filtro neste nível de prioridade, então, em seguida, a mensagem é comparada com filtros com uma prioridade de 1. Dois filtros prioritários 1 correspondem à mensagem, e por ser uma mensagem unidirecional, ela é encaminhada para ambos os pontos finais do destino.  Como foi encontrada uma correspondência entre os filtros prioritários 1, não são avaliados filtros de prioridade 0.  
  
> [!NOTE]
> Se nenhuma prioridade for especificada, a prioridade padrão de 0 será usada.  
  
 O exemplo a seguir define uma tabela de filtros que especifica prioridades de 2, 1 e 0 para os filtros referenciados na tabela.  
  
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
  
 No exemplo anterior, se uma mensagem corresponder ao XPathFilter, ela será encaminhada para o arredondamentoCalcEndpoint e nenhum filtro adicional na tabela será avaliado porque todos os outros filtros são de menor prioridade. No entanto, se a mensagem não corresponder ao XPathFilter, ela será avaliada em todos os filtros da próxima prioridade inferior, EndpointNameFilter e PrefixAddressFilter.  
  
> [!NOTE]
> Quando possível, use filtros exclusivos em vez de especificar uma prioridade, pois a avaliação prioritária pode resultar em degradação de desempenho.  
  
### <a name="backup-lists"></a>Listas de backup  
 Cada filtro na tabela do filtro pode especificar opcionalmente uma lista<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>de backup, que é uma coleção nomeada de pontos finais (). Esta coleção contém uma lista ordenada de pontos finais aos quais a <xref:System.ServiceModel.CommunicationException> mensagem será transmitida no <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>caso de um ao enviar para o ponto final principal especificado em . O exemplo a seguir define uma lista de backup chamada "backupServiceEndpoints" que contém dois pontos finais.  
  
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
  
 No exemplo anterior, se um envio para o ponto final principal "Destino" falhar, o Serviço de Roteamento tentará enviar para cada ponto final na seqüência em que eles estão listados, primeiro enviando para backupServiceQueue e, posteriormente, enviando para alternateServiceQueue se o enviar para backupServiceQueue falha. Se todos os pontos finais de backup falharem, uma falha será devolvida.
