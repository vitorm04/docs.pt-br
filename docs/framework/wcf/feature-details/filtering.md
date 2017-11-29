---
title: Filtragem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b97c53225afdc2710db26720ed3f28c12a322d8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="filtering"></a>Filtragem
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] filtragem de sistema pode usar filtros declarativos para corresponder as mensagens e tomar decisões operacionais. Você pode usar filtros para determinar o que fazer com uma mensagem examinando a parte da mensagem. Um processo de enfileiramento de mensagens, por exemplo, pode usar uma consulta XPath 1.0 para verificar se o elemento de prioridade de um cabeçalho conhecido para determinar se deve mover uma mensagem para o início da fila.  
  
 O sistema de filtragem é composto de um conjunto de classes com eficiência pode determinar que um conjunto de filtros são `true` para um determinado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem.  
  
 O sistema de filtragem é um componente principal do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens; ele é projetado para ser extremamente rápido. Cada implementação do filtro foi otimizada para um determinado tipo de correspondência com base em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens.  
  
 O sistema de filtragem não é thread-safe. O aplicativo deve lidar com nenhuma semântica de bloqueio. No entanto, ele suporta um gravador único, vários leitor.  
  
## <a name="where-filtering-fits"></a>Qual a filtragem se encaixa  
 A filtragem é executada depois que uma mensagem é recebida e faz parte do processo de expedir a mensagem para o componente de aplicativo apropriado. O design do sistema filtragem atende aos requisitos de várias [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] subsistemas, incluindo mensagens, roteamento, segurança, manipulação de eventos e o gerenciamento do sistema.  
  
## <a name="filters"></a>Filtros  
 O mecanismo de filtro tem dois componentes principais, filtros e tabelas de filtro. Um filtro de toma decisões Boolianas sobre uma mensagem com base nas condições de lógicas especificada pelo usuário. Filtros implementam a <xref:System.ServiceModel.Dispatcher.MessageFilter> classe.  
  
 O <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> métodos são usados para determinar se uma mensagem satisfaz um filtro. Um dos métodos testa o cabeçalho da mensagem, mas não pode inspecionar o corpo da mensagem. O outro método usa um *buffer de mensagem* como um parâmetro de entrada e pode inspecionar o corpo da mensagem.  
  
 Filtros não são geralmente testados individualmente, mas como parte de uma tabela de filtro, que é um genérico de classe que o <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> método cria.  
  
 Vários tipos de filtros cada especializam em correspondência em um determinado tipo de condição booleana. Quando você construir um filtro, você não pode alterar os critérios que usa um filtro; Para modificar os critérios do filtro, criar um novo e excluir o filtro existente.  
  
### <a name="action-filters"></a>Filtros de ação  
 O <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> contém uma lista de cadeias de caracteres de ação. Se qualquer uma das ações na lista do filtro corresponder o cabeçalho de ação na mensagem ou buffer de mensagem, o `Match` método retornará `true`. Se a lista estiver vazia, o filtro é considerado corresponde a um buffer de filtro e qualquer mensagem ou de correspondência total e `Match` retorna `true`. Se nenhuma das ações na lista do filtro corresponder o cabeçalho de ação na mensagem ou buffer de mensagem, `Match` retorna `false`. Se nenhuma ação na mensagem e a lista de filtros não estiver vazia, em seguida, `Match` retorna `false`.  
  
### <a name="endpoint-address-filters"></a>Filtros de endereço de ponto de extremidade  
 O <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtra as mensagens e buffers de mensagens com base em um endereço de ponto de extremidade, conforme representado em sua coleção de cabeçalho. Para uma mensagem passar um filtro, as seguintes condições devem ser atendidas:  
  
-   Endereço do filtro identificador de recurso uniforme (URI) deve ser o mesmo que na mensagem de cabeçalho.  
  
-   Cada parâmetro de ponto de extremidade no endereço do filtro (`address.Headers` coleção) deve localizar um cabeçalho de mensagem para mapear no. Cabeçalhos adicionais na mensagem ou buffer de mensagem são aceitáveis para a correspondência permaneça `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Filtros de endereço de ponto de extremidade do prefixo  
  
1.  O <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> funciona como o <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtrar, exceto que a correspondência pode ser um prefixo da mensagem de URI. Por exemplo, um filtro que especifica o endereço http://www.adatum.com corresponde as mensagens destinadas a http://www.adatum.com/userA.  
  
### <a name="xpath-message-filters"></a>Filtros de mensagem do XPath  
 Um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> usa uma expressão XPath para determinar se um documento XML contém elementos específicos, atributos, texto ou outros XML sintático constrói. O filtro é otimizado para ser extremamente eficiente para um subconjunto restrito de XPath. O XML Path Language é descrito no [especificação W3C XML caminho Language 1.0](http://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Normalmente, um aplicativo usa um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> em um ponto de extremidade para consultar o conteúdo de uma mensagem SOAP e, em seguida, usa a ação apropriada com base nos resultados da consulta. Um processo de enfileiramento de mensagens, por exemplo, pode usar uma consulta XPath para inspecionar o elemento de prioridade de um cabeçalho conhecido para decidir se deseja mover uma mensagem para o início da fila.  
  
## <a name="filter-tables"></a>Filtrar tabelas  
 Tabelas de filtro são usadas para armazenar pares de chave-valor, em que um filtro é a chave e alguns dados associados são o valor. Os dados de filtro podem ser usados para indicar quais ações a serem tomadas se uma mensagem corresponde ao filtro e o tipo de dados do filtro é o parâmetro genérico para a classe de tabela do filtro. Os dados de filtro podem consistir em regras de roteamento, estado de segurança de sessão, ouvintes de canal e assim por diante. Os dados podem ser usados em controle de fluxo de dados é necessário.  
  
 Filtrar tabelas implementam a interface genérica <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Tabelas de filtro tem vários métodos que correspondem a uma mensagem com todos os filtros na tabela e retornam uma coleção não ordenada de correspondência de dados ou filtros. Alguns dos métodos de correspondência são vários-match e retornam todos os itens correspondentes. Outras são único-match, retornando somente um item e geram um <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> se corresponder a mais de um filtro.  
  
### <a name="message-filter-table"></a>Tabela de filtro de mensagem  
 O <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> é a implementação mais geral de <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Você pode armazenar os filtros de todos os tipos na tabela.  
  
 Você pode atribuir prioridades numéricas para filtros, em que a prioridade mais alta é representada pelo número mais alto. Vários tipos de filtros podem ter a mesma prioridade. Um tipo específico de filtro pode aparecer em mais de um nível de prioridade.  
  
 A correspondência é feita começando com a prioridade mais alta e correspondem a filtros de uma vez encontrada com determinada prioridade, nenhum filtro prioridades mais baixas é examinado. Portanto, se você estiver usando um filtro de único método, match mais de um filtro corresponde a uma mensagem, mas cada filtro de correspondência com uma prioridade de diferente, nenhuma exceção é gerada e o filtro com a prioridade mais alta é retornado. Da mesma forma, um filtro de vários corresponder método retorna apenas aqueles que correspondem a filtros com a prioridade mais alta.  
  
### <a name="xpath-message-filter-table"></a>Tabela de filtro de mensagem do XPath  
 O <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> é otimizado para filtros de XPath declarativos, portanto, a chave de tabela é um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 O <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> otimiza a classe correspondente para um subconjunto de XPath que aborda a maioria dos cenários de mensagens e também oferece suporte à gramática XPath 1.0 completa. Ele tem otimização de algoritmos para correspondência paralela eficiente.  
  
 Esta tabela tem várias especializado `Match` métodos que operam em um <xref:System.Xml.XPath.XPathNavigator> e um <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. Um <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> estende o <xref:System.Xml.XPath.XPathNavigator> classe adicionando um <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> propriedade. Essa propriedade permite posições dentro do documento XML a serem salvos e carregados rapidamente sem a necessidade de clonar o navegador, uma alocação de memória caro que o <xref:System.Xml.XPath.XPathNavigator> requer para essa operação. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mecanismo XPath frequentemente deve registrar a posição do cursor no decorrer da execução de consultas em documentos XML, portanto, o <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> oferece uma otimização importante para processamento de mensagens.  
  
## <a name="customer-scenarios"></a>Cenários de cliente  
 Você pode usar a filtragem a qualquer momento em que você deseja enviar uma mensagem para os módulos de processamento diferentes dependendo dos dados contidos na mensagem. Dois cenários típicos são rotear uma mensagem com base no seu código de ação e Cancelar multiplexação um fluxo de mensagens com base no endereço de ponto de extremidade as mensagens.  
  
### <a name="routing"></a>Roteamento  
 O ouvinte de um ponto de extremidade de escuta as mensagens que têm um ou mais códigos de ação no cabeçalho SOAP da mensagem. Você pode implementar isso criando um <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> passando uma matriz que contém os códigos de ação para o construtor. Ele usa o filtro para registrar com o `ListenerFactory`, portanto, apenas as mensagens cuja ação corresponde a um no filtro de obtém esse ponto de extremidade.  
  
### <a name="de-multiplexing"></a>Eliminação multiplexação  
 Quando vários pontos de extremidade realizar fan-out do mesmo `ServiceListener` fora da conexão, a única maneira de cancelar multiplex mensagens e saber se eles pertencem a um determinado endereço do ponto de extremidade, é usar <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, que seleciona as mensagens para os pontos de extremidade registrados pelo executando uma pesquisa sobre as informações armazenadas nos cabeçalhos. Esses filtros, somente as mensagens que passam tem todos os cabeçalhos necessários que correspondem a ambas:  
  
-   O URI no `EndpointAddress`.  
  
-   O restante dos parâmetros no ponto de extremidade de `EndpointAddress` conforme especificado no <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Consulte também  
 [Serialização e transferência de dados](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
