---
title: Filtros de mensagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd5019668e865d2fea835b450d992d45b5273ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="message-filters"></a>Filtros de mensagem
Para implementar roteamento baseado em conteúdo, o serviço de roteamento usa <xref:System.ServiceModel.Dispatcher.MessageFilter> implementações que inspecionam seções específicas de uma mensagem, como o endereço, nome do ponto de extremidade ou uma instrução XPath específica. Se nenhum dos filtros de mensagem fornecido com [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] atender às suas necessidades, você pode criar um filtro personalizado, criando uma nova implementação de base de <xref:System.ServiceModel.Dispatcher.MessageFilter> classe.  
  
 Ao configurar o serviço de roteamento, você deve definir os elementos de filtro (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objetos) que descrevem o tipo de **MessageFilter** e quaisquer dados de suporte necessários para criar o filtro, como valores de cadeia de caracteres específica para pesquisa para dentro da mensagem. Observe que apenas criar os elementos de filtro define os filtros de mensagens individuais; Para usar os filtros para avaliar e rotear mensagens, você também deve definir uma tabela de filtro (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Cada entrada na tabela de filtro faz referência a um elemento de filtro e especifica o ponto de extremidade do cliente que uma mensagem será roteada para se a mensagem corresponde ao filtro. As entradas da tabela de filtro também permitem que você especifique uma coleção de pontos de extremidade de backup (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), que define uma lista de pontos de extremidade que a mensagem será transmitida para em caso de falha de transmissão ao enviar para o ponto de extremidade primário. Esses pontos de extremidade serão tentados na ordem especificada até obter êxito.  
  
## <a name="message-filters"></a>Filtros de mensagem  
 Os filtros de mensagem usados pelo serviço de roteamento fornecem a funcionalidade comum de seleção de mensagem, como avaliar o nome de uma mensagem foi enviada para a ação de SOAP, ou o endereço ou prefixo de endereço que a mensagem foi enviada para o ponto de extremidade. Filtros também podem ser Unidos com um `AND` condição, para que as mensagens só serão roteadas para um ponto de extremidade se a mensagem corresponde a ambos os filtros. Você também pode criar filtros personalizados ao criar sua própria implementação de <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 A seguinte tabela lista o <xref:System.ServiceModel.Routing.Configuration.FilterType> usada pelo serviço de roteamento, a classe que implementa o filtro de mensagem específica e obrigatório <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parâmetros.  
  
|Tipo de filtro|Descrição|Filtrar dados|Filtro de exemplo|  
|------------------|-----------------|-------------------------|--------------------|  
|Ação|Usa o <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> classe para corresponder as mensagens que contém uma ação específica.|A ação de filtro após.|\<nome do filtro = filterType "action1" = "Ação" filterData = "http://namespace/contract/operation" / >|  
|EndpointAddress|Usa o <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> classe com <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` para corresponder as mensagens que contém um endereço específico.|O endereço para filtrar após (no cabeçalho para).|\<nome do filtro = filterType "endereço1" = "EndpointAddress" filterData = "http://host/vdir/s.svc/b" / >|  
|EndpointAddressPrefix|Usa o <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> classe com <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` para corresponder as mensagens que contêm um prefixo de endereço específico.|O endereço para filtrar usando a correspondência de prefixo mais longo.|\<nome do filtro = filterType "prefix1" = "EndpointAddressPrefix" filterData = "http://host/" / >|  
|And|Usa o <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> classe que sempre é avaliada duas condições antes de retornar.|filterData não é usado; em vez disso, filter1 e filter2 têm os nomes dos filtros de mensagem correspondente (também na tabela), que deve ser **AND**ed juntos.|\<nome do filtro = filterType "and1" = "E" filter1 = filter2 "endereço1" = "action1" / >|  
|Personalizado|Um tipo definido pelo usuário que estende o <xref:System.ServiceModel.Dispatcher.MessageFilter> classe e tem um construtor que recebe uma cadeia de caracteres.|O atributo customType é o nome de tipo totalmente qualificado da classe para criar; filterData é a cadeia de caracteres passados para o construtor ao criar o filtro.|\<nome do filtro = filterType "custom1" = "Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData = "Dados personalizados" / >|  
|EndpointName|Usa o <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> classe para corresponder as mensagens com base no nome do ponto de extremidade de serviço que eles chegaram no.|O nome do ponto de extremidade de serviço, por exemplo: "serviceEndpoint1".  Isso deve ser um dos pontos de extremidade expostos no serviço de roteamento.|\<nome do filtro = filterType "stock1" = "Ponto de extremidade" filterData = "SvcEndpoint" / >|  
|MatchAll|Usa o <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> classe. Esse filtro corresponde a todas as mensagens que chegam.|filterData não é usado. Esse filtro sempre coincidirão com todas as mensagens.|\<nome do filtro = filterType "matchAll1" = "MatchAll" / >|  
|XPath|Usa o <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> classe para corresponder consultas XPath específicas dentro da mensagem.|A consulta XPath a ser usado durante a correspondência de mensagens.|\<nome do filtro = filterType "XPath1" = "XPath" filterData = "//ns:element" / >|  
  
 O exemplo a seguir define as entradas de filtro que usam os filtros de mensagem do XPath, EndpointName e PrefixEndpointAddress. Este exemplo também demonstra como usar um filtro personalizado para as entradas RoundRobinFilter1 e RoundRobinFilter2.  
  
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
>  Basta definir um filtro não faz com que as mensagens a ser avaliada com base no filtro. O filtro deve ser adicionado a uma tabela de filtro, que é associado com o ponto de extremidade do serviço exposto pelo serviço de roteamento.  
  
### <a name="namespace-table"></a>Tabela de Namespace  
 Ao usar um filtro XPath, os dados de filtro que contém a consulta XPath podem se tornar muito grandes devido ao uso de namespaces. Para aliviar esse problema, o serviço de roteamento fornece a capacidade de definir seus próprio prefixos de namespace usando a tabela de namespace.  
  
 A tabela de namespace é uma coleção de <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objetos que define os prefixos de namespace para namespaces comuns que podem ser usados em um XPath. A seguir estão os prefixos de espaços para nome e namespace do padrão que estão contidos na tabela de namespace.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|S11|http://schemas.xmlsoap.org/SOAP/envelope|  
|/s12|http://www.w3.org/2003/05/SOAP-envelope|  
|wsaAugust2004|http://schemas.xmlsoap.org/ws/2004/08/Addressing|  
|wsa10|http://www.w3.org/2005/08/Addressing|  
|SM|http://schemas.microsoft.com/ServiceModel/2004/05/xpathfunctions|  
|tempuri|http://tempuri.org|  
|ser|http://schemas.microsoft.com/2003/10/Serialization|  
  
 Quando você souber que você usar um namespace específico em suas consultas XPath, você pode adicioná-lo para a tabela de namespace junto com um prefixo de namespace exclusivo e use o prefixo em qualquer consulta XPath em vez do namespace completo. O exemplo a seguir define um prefixo de "custom" para o namespace "http://my.custom.namespace", que é usado na consulta XPath contida em filterData.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtrar tabelas  
 Embora cada elemento de filtro define uma comparação lógica que pode ser aplicada a uma mensagem, a tabela de filtro fornece a associação entre o elemento de filtro e o ponto de extremidade do cliente de destino. Uma tabela de filtro é uma coleção nomeada de <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objetos que definem a associação entre um filtro, um ponto de extremidade de destino principal e uma lista de pontos de extremidade alternativa de backup. As entradas da tabela de filtro também permitem que você especifique uma prioridade opcional para cada condição de filtro. O exemplo a seguir define dois filtros e, em seguida, define uma tabela de filtro que associa cada filtro um ponto de extremidade de destino.  
  
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
 Por padrão, todas as entradas na tabela de filtro são avaliadas simultaneamente, e a mensagem que está sendo avaliada é roteada para a extremidade associadas a cada entrada de filtro correspondente. Se vários filtros forem avaliados como `true`e a mensagem é unidirecionais ou bidirecionais, a mensagem é difundida via multicast para os pontos de extremidade para todos os filtros de correspondência. Mensagens de solicitação-resposta não podem ser multicast porque somente uma resposta pode ser retornada ao cliente.  
  
 Lógica mais complexa de roteamento pode ser implementada, especificando níveis de prioridade para cada filtro; o serviço de roteamento avalia todos os filtros no nível de prioridade mais alto primeiro. Se uma mensagem corresponde a um filtro desse nível, nenhum filtro de menor prioridade será processado. Por exemplo, uma mensagem de entrada unidirecional primeiro é avaliada em relação a todos os filtros com prioridade 2. A mensagem não corresponde qualquer filtro nesse nível de prioridade, próximo que a mensagem é comparada com filtros com uma prioridade de 1. Dois filtros de prioridade 1 correspondem à mensagem e porque é uma mensagem unidirecional que ela é roteada para os pontos de extremidade de destino.  Porque foi encontrada uma correspondência entre os filtros de prioridade 1, nenhum filtro de prioridade 0 é avaliado.  
  
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
  
 No exemplo anterior, se uma mensagem corresponde XPathFilter, ela será roteada para o roundingCalcEndpoint e sem filtros adicionais na tabela serão avaliados porque todos os outros filtros de uma prioridade mais baixa. No entanto, se a mensagem não corresponder XPathFilter ele, em seguida, será avaliado em relação a todos os filtros de menor prioridade, EndpointNameFilter e PrefixAddressFilter.  
  
> [!NOTE]
>  Quando possível, use filtros exclusivos em vez de especificar uma prioridade, como avaliação de prioridade pode resultar em degradação do desempenho.  
  
### <a name="backup-lists"></a>Listas de backup  
 Cada filtro na tabela de filtros pode opcionalmente especificar uma lista de backup, que é uma coleção nomeada de pontos de extremidade (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Esta coleção contém uma lista ordenada de pontos de extremidade que a mensagem será transmitida no caso de um <xref:System.ServiceModel.CommunicationException> ao enviar para o ponto de extremidade primário especificado em <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. O exemplo a seguir define uma lista de backup denominada "backupServiceEndpoints" que contém dois pontos de extremidade.  
  
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
  
 No exemplo anterior, se um envio para o ponto de extremidade "Destino" primário falhar, o serviço de roteamento tentará enviar para cada ponto de extremidade na sequência estão listados, enviar primeiro para backupServiceQueue e enviar posteriormente para alternateServiceQueue se a Enviar para backupServiceQueue falhará. Se todos os pontos de extremidade de backup falharem, uma falha será retornada.
