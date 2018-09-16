---
title: Filtragem
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: 74915a45ed5ca1d13790f64c7921d1f750fa04d3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45673968"
---
# <a name="filtering"></a>Filtragem
O Windows Communication Foundation (WCF) filtragem de sistema pode usar filtros declarativos para corresponder as mensagens e tomar decisões operacionais. Você pode usar filtros para determinar o que fazer com uma mensagem, examinando a parte da mensagem. Um processo de enfileiramento de mensagens, por exemplo, pode usar uma consulta XPath 1.0 para verificar o elemento de prioridade de um cabeçalho conhecido para determinar se deseja mover uma mensagem para o início da fila.  
  
 O sistema de filtragem é composto de um conjunto de classes que podem com eficiência determinar quais um conjunto de filtros estão `true` para uma mensagem específica do WCF.  
  
 O sistema de filtragem é um componente principal do sistema de mensagens do WCF; ele é projetado para ser extremamente rápido. Cada implementação do filtro foi otimizada para um determinado tipo de correspondência com base em mensagens do WCF.  
  
 O sistema de filtragem não é thread-safe. O aplicativo deve tratar qualquer semântica de bloqueio. No entanto, ele suporta um gravador de várias leitor, o único.  
  
## <a name="where-filtering-fits"></a>Filtragem se encaixa  
 Filtragem será executada depois que uma mensagem é recebida e faz parte do processo de expedição a mensagem para o componente de aplicativo apropriado. O design do sistema de filtragem atende aos requisitos dos vários subsistemas WCF, incluindo o sistema de mensagens, roteamento, segurança, manipulação de eventos e gerenciamento do sistema.  
  
## <a name="filters"></a>Filtros  
 O mecanismo de filtro tem dois componentes principais, filtros e tabelas de filtro. Um filtro toma decisões Boolianas sobre uma mensagem com base em condições lógicas especificado pelo usuário. Implementam filtros de <xref:System.ServiceModel.Dispatcher.MessageFilter> classe.  
  
 O <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> métodos são usados para determinar se uma mensagem satisfaz um filtro. Um dos métodos de testes de cabeçalho da mensagem, mas não é possível inspecionar o corpo da mensagem. O outro método utiliza um *buffer de mensagem* como um parâmetro de entrada e pode inspecionar o corpo da mensagem.  
  
 Filtros não são geralmente testados individualmente, mas como parte de uma tabela de filtro, que é um genérico de classe que o <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> método cria.  
  
 Os vários tipos de filtros de cada são especializados em correspondência em um determinado tipo de condição booleana. Depois que você construir um filtro, você não pode alterar os critérios que usa um filtro; Para modificar de critérios um filtro, construir um novo e excluir o filtro existente.  
  
### <a name="action-filters"></a>Filtros de ação  
 O <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> contém uma lista de cadeias de caracteres de ação. Se qualquer uma das ações na lista do filtro corresponder o cabeçalho de ação na mensagem ou buffer de mensagem, o `Match` retorno do método `true`. Se a lista estiver vazia, o filtro é considerado corresponde a um buffer de filtro e qualquer mensagem ou mensagem de correspondência total e `Match` retorna `true`. Se nenhuma das ações na lista do filtro corresponder o cabeçalho de ação na mensagem ou buffer de mensagem `Match` retorna `false`. Se não há nenhuma ação na mensagem e lista de filtros não estiver vazio, então `Match` retorna `false`.  
  
### <a name="endpoint-address-filters"></a>Filtros de endereço do ponto de extremidade  
 O <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtra as mensagens e buffers de mensagens com base em um endereço de ponto de extremidade, conforme representado em sua coleção de cabeçalho. Para uma mensagem passar um filtro, as seguintes condições devem ser atendidas:  
  
-   Endereço do filtro identificador de recurso uniforme (URI) deve ser o mesmo que aquele em que a mensagem de cabeçalho.  
  
-   Cada parâmetro de ponto de extremidade no endereço do filtro (`address.Headers` coleção) deve localizar um cabeçalho na mensagem para mapear no. Cabeçalhos adicionais na mensagem ou buffer de mensagem são aceitáveis para a correspondência permaneça `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Filtros de endereço do ponto de extremidade de prefixo  
  
1.  O <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> funciona como o <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtrar, exceto que a correspondência pode ser em um prefixo da mensagem de URI. Por exemplo, um filtro especificando o endereço http://www.adatum.com corresponde a mensagens endereçadas a http://www.adatum.com/userA.  
  
### <a name="xpath-message-filters"></a>Filtros de mensagem de XPath  
 Um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> usa uma expressão XPath para determinar se um documento XML contém elementos específicos, atributos, texto ou outros XML sintático constrói. O filtro é otimizado para ser extremamente eficiente para um subconjunto estrito do XPath. O XML Path Language é descrito na [especificação W3C XML caminho Language 1.0](https://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Normalmente, um aplicativo usa um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> em um ponto de extremidade para consultar o conteúdo de uma mensagem SOAP e, em seguida, usa a ação apropriada com base nos resultados da consulta. Um processo de enfileiramento de mensagens, por exemplo, pode usar uma consulta XPath para inspecionar o elemento do cabeçalho conhecido para decidir se deseja mover uma mensagem para o início da fila de prioridade.  
  
## <a name="filter-tables"></a>Filtrar tabelas  
 Filtrar tabelas são usadas para armazenar pares chave-valor, em que um filtro é a chave e alguns dados associados são o valor. Os dados de filtro podem ser usados para indicar quais ações a serem tomadas se uma mensagem corresponde ao filtro e o tipo de dados é o parâmetro genérico para a classe de filtro de tabela. Os dados de filtro podem consistir em regras de roteamento, estado de segurança de sessão, ouvintes em um canal e assim por diante. Os dados podem ser usados em que o controle de fluxo de dados é necessária.  
  
 Filtrar tabelas implementam a interface genérica <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Filtrar tabelas têm vários métodos que correspondem a uma mensagem em relação a todos os filtros na tabela e retornam uma coleção não ordenada de dados ou filtros de correspondência. Alguns dos métodos de correspondência são vários-match e retornam todos os itens correspondentes. Outras são o único-match, retornando somente um item e geram um <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> se corresponder a mais de um filtro.  
  
### <a name="message-filter-table"></a>Tabela de filtro de mensagem  
 O <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> é a implementação mais geral de <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Você pode armazenar os filtros de todos os tipos na tabela.  
  
 Você pode atribuir prioridades numéricas para filtros, em que a prioridade mais alta é demonstrada pelo número mais alto. Vários tipos de filtros podem ter a mesma prioridade. Um tipo específico de filtro pode aparecer em mais de um nível de prioridade.  
  
 A correspondência é feita começando com a prioridade mais alta e filtros de correspondência de uma vez encontrado com determinada prioridade, sem filtros com prioridades mais baixas são examinados. Portanto, se você estiver usando um único filtro corresponde ao método, mais de um filtro corresponde a uma mensagem, mas cada filtro correspondente tem uma prioridade diferente, nenhuma exceção é lançada e o filtro com a prioridade mais alta será retornado. Da mesma forma, um múltiplo de filtro corresponde ao método retorna apenas aqueles que correspondem a filtros com a prioridade mais alta.  
  
### <a name="xpath-message-filter-table"></a>Tabela de filtro de mensagem de XPath  
 O <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> é otimizada para filtros de XPath declarativos, portanto, a chave de tabela é um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 O <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> otimiza a classe correspondente para um subconjunto de XPath que aborda a maioria dos cenários de mensagens e também oferece suporte à gramática XPath 1.0 completa. Ele tem algoritmos otimizados para correspondência paralela eficiente.  
  
 Esta tabela tem várias especializado `Match` métodos que operam em um <xref:System.Xml.XPath.XPathNavigator> e um <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. Um <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> estende o <xref:System.Xml.XPath.XPathNavigator> classe adicionando um <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> propriedade. Essa propriedade permite posições dentro do documento XML a ser salvos e carregados rapidamente sem precisar clona o navegador, uma alocação de memória caro que o <xref:System.Xml.XPath.XPathNavigator> requer para essa operação. O mecanismo de XPath do WCF frequentemente deve registrar a posição do cursor no decorrer da execução de consultas em documentos XML, portanto, o <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> fornece uma otimização importante para o processamento da mensagem.  
  
## <a name="customer-scenarios"></a>Cenários de cliente  
 Você pode usar a filtragem a qualquer momento que você deseja enviar uma mensagem para os módulos de processamento diferentes dependendo dos dados contidos na mensagem. Dois cenários típicos são rotear uma mensagem com base no seu código de ação e da demultiplexação em um fluxo de mensagens com base no endereço do ponto de extremidade de mensagens recebidas.  
  
### <a name="routing"></a>Roteamento  
 O ouvinte de um ponto de extremidade escuta as mensagens que tenham um ou mais códigos de ação no cabeçalho SOAP da mensagem. Você implementa isso criando um <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> , passando uma matriz que contém os códigos de ação para seu construtor. Ele usa o filtro para registrar com o `ListenerFactory`, portanto, apenas as mensagens cuja ação corresponde a um no filtro de Introdução ao ponto de extremidade específico.  
  
### <a name="de-multiplexing"></a>Demultiplexação  
 Quando vários pontos de extremidade realizar fan-out do mesmo `ServiceListener` transmissão, a única maneira de cancelar multiplexar as mensagens e saber se eles pertencem a um determinado endereço de ponto de extremidade, é usar <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, que seleciona mensagens para pontos de extremidade registrados pelo executando uma pesquisa sobre as informações armazenadas nos cabeçalhos. Esses filtros, somente as mensagens que passam tem todos os cabeçalhos necessários que correspondem a ambas:  
  
-   O URI no `EndpointAddress`.  
  
-   O restante dos parâmetros no ponto de extremidade a `EndpointAddress` conforme especificado no <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Consulte também  
 [Serialização e transferência de dados](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
