---
title: Introdução a LINQ no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
ms.openlocfilehash: 7e6d299bafff2a5a34a8f0942ba6dc9c25fcdd83
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805731"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Introdução a LINQ no Visual Basic
Consulta integrada à linguagem (LINQ) adiciona recursos de consulta para o Visual Basic e fornece recursos simples e eficientes quando você trabalha com todos os tipos de dados. Em vez de enviar uma consulta para um banco de dados a ser processado ou trabalhar com a sintaxe de consulta diferente para cada tipo de dados que você está procurando, LINQ apresenta consultas como parte da linguagem do Visual Basic. Ele usa uma sintaxe unificada independentemente do tipo de dados.  
  
 LINQ permite consultar dados de um banco de dados do SQL Server, XML, matrizes de memória e coleções, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] conjuntos de dados, ou quaisquer outros dados locais ou remotos que ofereça suporte a LINQ de origem. Você pode fazer tudo isso com elementos de linguagem comuns do Visual Basic. Como as consultas são gravadas na linguagem do Visual Basic, os resultados da consulta são retornados como objetos fortemente tipados. Esses objetos dão suporte a IntelliSense, que permite que você escrever código mais rápido e detectar erros em suas consultas em tempo de compilação em vez de em tempo de execução. Consultas LINQ podem ser usadas como a fonte de consultas adicionais para refinar os resultados. Eles também poderão estar associados a controles, para que os usuários podem facilmente exibir e modificar os resultados da consulta.  
  
 Por exemplo, o exemplo de código a seguir mostra uma consulta LINQ que retorna uma lista de clientes de uma coleção e grupos com base em sua localização.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 Neste tópico, você encontrará informações sobre as seguintes áreas:  
  
-   [Executar os exemplos](#RunningtheExamples)  
  
-   [Provedores LINQ](#LINQProviders)  
  
-   [Estrutura de uma consulta LINQ](#StructureOfALINQQuery)  
  
-   [Operadores de consulta LINQ Visual Basic](#VisualBasicLINQQueryOperators)  
  
-   [Conexão com um banco de dados usando LINQ to SQL](#ConnectingToADatabase)  
  
-   [Funcionalidades do Visual Basic que dão suporte a LINQ](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [Execução de consultas adiadas e imediatas](#QueryExecution)  
  
-   [XML no Visual Basic](#XMLInVisualBasic)  
  
-   [Recursos relacionados](#RelatedResources)  
  
-   [Como e tópicos de instruções passo a passo](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a> Executar os exemplos  
 Para executar os exemplos na introdução e na seção "Estrutura de uma consulta LINQ", inclua o código a seguir, que retorna a lista de clientes e pedidos.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a> Provedores LINQ  
 Um *provedor LINQ* suas consultas LINQ do Visual Basic é mapeado para a fonte de dados que está sendo consultada. Quando você escreve uma consulta LINQ, o provedor leva essa consulta e converte em comandos que a fonte de dados será capaz de executar. O provedor também converte dados de origem para os objetos que compõem o resultado da consulta. Finalmente, ele converte objetos em dados quando você envia atualizações para a fonte de dados.  
  
 Visual Basic inclui os seguintes provedores LINQ.  
  
|Provider|Descrição|  
|---|---|  
|Objetos LINQ to|O provedor LINQ to Objects permite consultar matrizes e coleções na memória. Se um objeto oferecer suporte a <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> interface, o provedor LINQ to Objects permite que você consultá-lo.<br /><br /> Você pode ativar o provedor LINQ to Objects importando o <xref:System.Linq> namespace, que é importado por padrão para todos os projetos do Visual Basic.<br /><br /> Para obter mais informações sobre o provedor LINQ to Objects, consulte [objetos LINQ to](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).|  
|LINQ to SQL|O provedor LINQ to SQL permite consultar e modificar dados em um banco de dados do SQL Server. Isso facilita mapear o modelo de objeto para um aplicativo para as tabelas e objetos em um banco de dados.<br /><br /> Visual Basic facilita a trabalhar com LINQ to SQL, incluindo o Object Relational Designer (O/R Designer). Esse designer é usado para criar um modelo de objeto em um aplicativo que mapeia para objetos em um banco de dados. O Object Relational Designer também fornece funcionalidade para mapear os procedimentos armazenados e funções para o <xref:System.Data.Linq.DataContext> objeto, que gerencia a comunicação com o banco de dados e armazena o estado para verificações de simultaneidade otimista.<br /><br /> Para obter mais informações sobre o provedor LINQ to SQL, consulte [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Para obter mais informações sobre o Object Relational Designer, consulte [LINQ to SQL Tools no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|O provedor LINQ to XML permite consultar e modificar o XML. Você pode modificar o XML na memória, ou você pode carregar XML de e salvar XML em um arquivo.<br /><br /> Além disso, o provedor LINQ to XML permite literais XML e propriedades de eixo XML que permitem escrever XML diretamente no seu código do Visual Basic. Para obter mais informações, consulte [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|O provedor LINQ to DataSet permite consultar e atualizar dados em um [!INCLUDE[vstecado](~/includes/vstecado-md.md)] conjunto de dados. Você pode adicionar o poder do LINQ para aplicativos que usam conjuntos de dados para simplificar e estender seus recursos para consultar, agregar e atualizar os dados no conjunto de dados.<br /><br /> Para obter mais informações, consulte [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
##  <a name="StructureOfALINQQuery"></a> Estrutura de uma consulta LINQ  
 Uma consulta LINQ, geralmente conhecida como uma *expressão de consulta*, consiste em uma combinação de cláusulas de consulta que identificam as fontes de dados e variáveis de iteração para a consulta. Uma expressão de consulta também pode incluir instruções para classificação, filtragem, agrupamento e unir ou cálculos para aplicar a fonte de dados. Sintaxe de expressão de consulta é semelhante à sintaxe de SQL; Portanto, você pode achar grande parte da sintaxe familiar.  
  
 Uma expressão de consulta começa com um `From` cláusula. Essa cláusula identifica a fonte de dados de uma consulta e as variáveis que são usadas para se referir a cada elemento da fonte de dados individualmente. Essas variáveis são denominadas *variáveis de intervalo* ou *variáveis de iteração*. O `From` cláusula é necessária para uma consulta, exceto para `Aggregate` consultas, onde o `From` cláusula é opcional. Depois que o escopo e a fonte da consulta são identificados no `From` ou `Aggregate` cláusulas, você pode incluir qualquer combinação de cláusulas de consulta para refinar a consulta. Para obter detalhes sobre as cláusulas de consulta, consulte operadores de consulta LINQ Visual Basic, posteriormente neste tópico. Por exemplo, a consulta a seguir identifica um conjunto de dados do cliente como o `customers` variável e uma variável de iteração chamada `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 Este exemplo é uma consulta válida por si só; No entanto, a consulta se torna muito mais eficiente quando você adicionar mais cláusulas de consulta para refinar o resultados. Por exemplo, você pode adicionar um `Where` cláusula para filtrar o resultado por um ou mais valores. Expressões de consulta são uma única linha de código; Você apenas pode acrescentar cláusulas de consulta adicionais ao final da consulta. Você pode dividir uma consulta em várias linhas de texto para melhorar a legibilidade usando o caractere de continuação de linha sublinhado (_). O exemplo de código a seguir mostra um exemplo de uma consulta que inclui um `Where` cláusula.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 É outra cláusula de consulta avançada de `Select` cláusula, que permite retornar somente os campos selecionados da fonte de dados. Consultas LINQ retornam coleções enumeráveis de objetos fortemente tipados. Uma consulta pode retornar uma coleção de tipos anônimos ou tipos nomeados. Você pode usar o `Select` cláusula para retornar apenas um único campo da fonte de dados. Quando você fizer isso, o tipo de coleção retornada é o tipo de campo único. Você também pode usar o `Select` cláusula para retornar vários campos da fonte de dados. Quando você fizer isso, o tipo de coleção retornada é um novo tipo anônimo. Você também pode combinar os campos retornados pela consulta para os campos de um tipo nomeado especificado. O exemplo de código a seguir mostra uma expressão de consulta que retorna uma coleção de tipos anônimos que possuem membros preenchidos com dados dos campos da fonte de dados selecionados.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 Consultas LINQ também podem ser usadas para combinar várias fontes de dados e retornar um único resultado. Isso pode ser feito com um ou mais `From` cláusulas, ou usando o `Join` ou `Group Join` cláusulas de consulta. O exemplo de código a seguir mostra uma expressão de consulta que combina dados customer e order e retorna uma coleção de tipos anônimos que contém dados do cliente e ordem.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Você pode usar o `Group Join` cláusula para criar um resultado de consulta hierárquico que contém uma coleção de objetos do cliente. Cada objeto do cliente tem uma propriedade que contém uma coleção de todos os pedidos do cliente. O exemplo de código a seguir mostra uma expressão de consulta que combina dados de cliente e do pedido como um resultado hierárquico e retorna uma coleção de tipos anônimos. A consulta retorna um tipo que inclui um `CustomerOrders` propriedade que contém uma coleção de dados de pedidos do cliente. Ele também inclui um `OrderTotal` propriedade que contém a soma dos totais para todos os pedidos do cliente. (Esta consulta é equivalente a uma junção externa esquerda).  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Há vários operadores consulta LINQ adicionais que você pode usar para criar expressões de consulta eficiente. A próxima seção deste tópico discute as várias cláusulas de consulta que você pode incluir em uma expressão de consulta. Para obter detalhes sobre as cláusulas de consulta do Visual Basic, consulte [consultas](../../../../visual-basic/language-reference/queries/queries.md).  
  
##  <a name="VisualBasicLINQQueryOperators"></a> Operadores de consulta LINQ Visual Basic  
 As classes de <xref:System.Linq> namespace e outros namespaces que suportam consultas LINQ incluem métodos que você pode chamar para criar e refinar consultas com base nas necessidades do seu aplicativo. Visual Basic inclui palavras-chave para as cláusulas de consulta mais comuns, como descrito pela tabela a seguir.  
  
|Termo|Definição|  
|---|---|  
|[Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md)|Qualquer um `From` cláusula ou um `Aggregate` cláusula é necessária para iniciar uma consulta. Um `From` cláusula Especifica uma coleção de fonte e uma variável de iteração para uma consulta. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[Cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md)|Opcional. Declara um conjunto de variáveis de iteração para uma consulta. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> Se um `Select` cláusula não for especificada, as variáveis de iteração para a consulta consistem as variáveis de iteração especificadas pelo `From` ou `Aggregate` cláusula.|  
|[Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md)|Opcional. Especifica uma condição de filtragem para uma consulta. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md)|Opcional. Especifica a ordem de classificação para colunas em uma consulta. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md)|Opcional. Combina duas coleções em uma única coleção. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)|Opcional. Agrupa os elementos de um resultado de consulta. Pode ser usado para aplicar funções de agregação para cada grupo. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)|Opcional. Combina duas coleções em uma única coleção hierárquica. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|Qualquer um `From` cláusula ou um `Aggregate` cláusula é necessária para iniciar uma consulta. Um `Aggregate` cláusula aplica um ou mais funções de agregação a uma coleção. Por exemplo, você pode usar o `Aggregate` cláusula para calcular uma soma de todos os elementos retornados por uma consulta.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> Você também pode usar o `Aggregate` cláusula para modificar uma consulta. Por exemplo, você pode usar o `Aggregate` cláusula para executar um cálculo em uma coleção relacionada de consulta.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Cláusula Let](../../../../visual-basic/language-reference/queries/let-clause.md)|Opcional. Calcula um valor e o atribui a uma nova variável na consulta. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[Cláusula Distinct](../../../../visual-basic/language-reference/queries/distinct-clause.md)|Opcional. Restringe os valores da variável de iteração atual para eliminar valores duplicados nos resultados da consulta. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[Cláusula Skip](../../../../visual-basic/language-reference/queries/skip-clause.md)|Opcional. Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[Cláusula Skip While](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|Opcional. Ignora elementos em uma coleção desde que uma condição especificada seja `true` e, em seguida, retorna os elementos restantes. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Cláusula Take](../../../../visual-basic/language-reference/queries/take-clause.md)|Opcional. Retorna um número especificado de elementos contíguos do início de uma coleção. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Cláusula Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md)|Opcional. Inclui elementos em uma coleção desde que uma condição especificada seja `true` e ignora os elementos restantes. Por exemplo:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 Para obter detalhes sobre as cláusulas de consulta do Visual Basic, consulte [consultas](../../../../visual-basic/language-reference/queries/queries.md).  
  
 Você pode usar recursos adicionais de consulta LINQ chamando membros dos tipos enumeráveis e consultáveis fornecidos pelo LINQ. Você pode usar esses recursos adicionais, chamando um operador de consulta específica no resultado de uma expressão de consulta. Por exemplo, o seguinte exemplo de código usa o <xref:System.Linq.Enumerable.Union%2A> método para combinar os resultados das duas consultas em um resultado da consulta. Ele usa o <xref:System.Linq.Enumerable.ToList%2A> método para retornar o resultado da consulta como uma lista genérica.  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Para obter detalhes sobre recursos LINQ adicionais, consulte [visão geral de operadores de consulta padrão](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
##  <a name="ConnectingToADatabase"></a> Conexão com um banco de dados usando LINQ to SQL  
 No Visual Basic, você deve identificar os objetos de banco de dados do SQL Server, como tabelas, exibições e procedimentos armazenados, que você deseja acessar usando um LINQ para arquivo SQL. Um arquivo LINQ to SQL tem uma extensão dbml.  
  
 Quando você tem uma conexão válida para um banco de dados do SQL Server, você pode adicionar uma **Classes LINQ to SQL** modelo de item ao seu projeto. Isso exibirá o Object Relational Designer (Object Relational designer). O Object Relational Designer permite que você arraste os itens que você deseja acessar no código do **Server Explorer**/**Pesquisador de objetos de banco de dados** para a superfície de designer. O arquivo LINQ to SQL adiciona um <xref:System.Data.Linq.DataContext> objeto ao seu projeto. Este objeto inclui propriedades e coleções para as tabelas e exibições que você deseja acesso e métodos para os procedimentos armazenados que você deseja chamar. Depois de salvar suas alterações para o arquivo LINQ to SQL (. dbml), você pode acessar esses objetos no seu código referenciando o <xref:System.Data.Linq.DataContext> objeto é definido por Object Relational Designer. O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo LINQ to SQL. Por exemplo, um arquivo LINQ to SQL dbml é chamado criará uma <xref:System.Data.Linq.DataContext> objeto chamado `NorthwindDataContext`.  
  
 Para obter exemplos com instruções passo a passo, consulte [como: consultar um banco de dados](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md) e [como: chamar um procedimento armazenado](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md).  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a> Recursos do Visual Basic que suportam LINQ  
 Visual Basic inclui outros recursos importantes que tornam o uso de LINQ simples e reduzem a quantidade de código que você deve escrever para executar consultas LINQ. Eles incluem o seguinte:  
  
-   **Tipos anônimos**, que permitem que você crie um novo tipo com base no resultado de consulta.  
  
-   **Variáveis de tipo implícito**, que permitem que você adiar a especificação de um tipo e deixar que o compilador inferir o tipo com base no resultado da consulta.  
  
-   **Métodos de extensão**, que permitem estender um tipo existente com seus próprios métodos sem modificar o próprio tipo.  
  
 Para obter detalhes, consulte [Visual Basic recursos que suporte a LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md).  
  
##  <a name="QueryExecution"></a> Execução de consultas adiadas e imediatas  
 A execução da consulta é separada da criação de uma consulta. Depois que uma consulta é criada, sua execução é disparada por um mecanismo separado. Uma consulta pode ser executada assim que ele é definido (*execução imediata*), ou a definição pode ser armazenada e a consulta pode ser executada mais tarde (*execução diferida*).  
  
 Por padrão, quando você cria uma consulta, a consulta em si não será executado imediatamente. Em vez disso, a definição de consulta é armazenada na variável que é usado para referenciar o resultado da consulta. Quando a variável de resultado da consulta for acessada mais tarde no código, como em um `For…Next` loop, a consulta é executada. Esse processo é conhecido como *execução diferida*.  
  
 Consultas também podem ser executadas quando eles são definidos, o que é conhecido como *execução imediata*. Você pode acionar a execução imediata, aplicando um método que exige acesso aos elementos individuais do resultado da consulta. Isso pode ser o resultado de uma função de agregação, incluindo como `Count`, `Sum`, `Average`, `Min`, ou `Max`. Para obter mais informações sobre funções de agregação, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Usando o `ToList` ou `ToArray` métodos também irá forçar a execução imediata. Isso pode ser útil quando você deseja executar a consulta imediatamente e armazenar em cache os resultados. Para obter mais informações sobre esses métodos, consulte [converter tipos de dados](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Para obter mais informações sobre a execução da consulta, consulte [gravar sua consulta LINQ primeiro](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
##  <a name="XMLInVisualBasic"></a> XML no Visual Basic  
 Os recursos XML no Visual Basic incluem literais XML e propriedades de eixo XML, que permitem que você facilmente criar, acessarem, consultar e modificar XML no seu código. Literais XML permitem escrever XML diretamente no seu código. O compilador do Visual Basic trata o XML como um objeto de dados de primeira classe.  
  
 O exemplo de código a seguir mostra como criar um elemento XML, acessar suas subelementos e atributos e o conteúdo do elemento de consulta usando LINQ.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Para obter mais informações, consulte [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).  
  
##  <a name="RelatedResources"></a> Recursos relacionados  
  
|Tópico|Descrição|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|Descreve os recursos XML no Visual Basic que podem ser consultados e que permitem incluir XML como objetos de dados de primeira classe no seu código do Visual Basic.|  
|[Consultas](../../../../visual-basic/language-reference/queries/queries.md)|Fornece informações de referência sobre as cláusulas de consulta que estão disponíveis no Visual Basic.|  
|[LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|Inclui informações gerais, orientação de programação e exemplos para LINQ.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|Inclui informações gerais, orientação de programação e exemplos para LINQ to SQL.|  
|[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|Inclui informações gerais, orientação de programação e exemplos de LINQ para objetos.|  
|[LINQ to ADO.NET (página do portal)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|Inclui links para informações gerais, orientação de programação e exemplos para LINQ to [!INCLUDE[vstecado](~/includes/vstecado-md.md)].|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|Inclui informações gerais, orientação de programação e exemplos para LINQ to XML.|  
  
##  <a name="HowToAndWalkthroughTopics"></a> Como e tópicos de instruções passo a passo  
 [Como consultar um banco de dados](how-to-query-a-database-by-using-linq.md)  
  
 [Como chamar um procedimento armazenado](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Como modificar dados em um banco de dados](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Como combinar dados com junções](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Como classificar resultados de consulta](how-to-sort-query-results-by-using-linq.md)  
  
 [Como filtrar resultados de consulta](how-to-filter-query-results-by-using-linq.md)  
  
 [Como contar, somar ou fazer média de dados](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Como localizar o valor mínimo ou máximo em um resultado de consulta](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Capítulos do Livro em Destaque  
 [Capítulo 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) na [programação Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Consulte também  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Visão geral do LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [Visão geral de LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset-overview.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [Métodos de DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
