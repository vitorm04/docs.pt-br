---
title: Introdução a LINQ no Visual Basic
ms.date: 08/28/2018
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
ms.openlocfilehash: d9af75474f6b0aec2bdf6aa2f550c280209f91e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633492"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Introdução a LINQ no Visual Basic
Consulta integrada à linguagem (LINQ) adiciona recursos de consulta para o Visual Basic e fornece recursos simples e eficientes quando você trabalha com todos os tipos de dados. Em vez de enviar uma consulta para um banco de dados a serem processados ou trabalhar com diferentes sintaxes de consulta para cada tipo de dados que você está procurando, o LINQ apresenta consultas como parte da linguagem Visual Basic. Ele usa uma sintaxe unificada independentemente do tipo de dados.  
  
 LINQ permite consultar dados de um banco de dados do SQL Server, XML, matrizes de memória e coleções, conjuntos de dados ADO.NET ou qualquer outra fonte de dados local ou remoto que ofereça suporte ao LINQ. Você pode fazer tudo isso com elementos de linguagem comuns do Visual Basic. Como as consultas são gravadas na linguagem do Visual Basic, os resultados da consulta são retornados como objetos fortemente tipados. Esses objetos dão suporte a IntelliSense, que permite que você escreva código mais rápido e detecte erros nas suas consultas em tempo de compilação em vez de em tempo de execução. Consultas LINQ podem ser usadas como a fonte de consultas adicionais para refinar os resultados. Elas também podem ser associadas a controles, para que os usuários podem facilmente exibir e modificar os resultados da consulta.  
  
 Por exemplo, o exemplo de código a seguir mostra uma consulta LINQ que retorna uma lista de clientes de uma coleção e os agrupa com base em sua localização.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>Como executar os exemplos  
 Para executar os exemplos na introdução e nos [estrutura de uma consulta LINQ](#structure-of-a-linq-query) seção, inclua o código a seguir, que retorna uma lista de clientes e pedidos.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>Provedores de LINQ  
 Um *provedor LINQ* mapeia suas consultas LINQ do Visual Basic para a fonte de dados que está sendo consultada. Quando você escreve uma consulta LINQ, o provedor leva essa consulta e converte em comandos que a fonte de dados será capaz de executar. O provedor também converte dados da origem para os objetos que compõem o resultado da consulta. Por fim, ele converte objetos em dados quando você envia atualizações para a fonte de dados.  
  
 Visual Basic inclui os seguintes provedores LINQ.  
  
|Provider|Descrição|  
|---|---|  
|Objetos LINQ to|O provedor LINQ to Objects permite que você consultar matrizes e coleções na memória. Se um objeto oferecer suporte a <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> interface, o provedor LINQ to Objects permite que você consultá-lo.<br /><br /> Você pode ativar o provedor LINQ to Objects importando o <xref:System.Linq> namespace, que é importado por padrão para todos os projetos do Visual Basic.<br /><br /> Para obter mais informações sobre o provedor LINQ to Objects, consulte [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ to SQL|O provedor LINQ to SQL permite consultar e modificar dados em um banco de dados do SQL Server. Isso facilita mapear o modelo de objeto para um aplicativo para as tabelas e objetos em um banco de dados.<br /><br /> Visual Basic torna mais fácil trabalhar com LINQ to SQL, incluindo o Object Relational Designer (O/R Designer). Esse designer é usado para criar um modelo de objeto em um aplicativo que mapeia para objetos em um banco de dados. O O/R Designer também fornece funcionalidade para mapear procedimentos armazenados e funções para o <xref:System.Data.Linq.DataContext> object, que gerencia a comunicação com o banco de dados e armazena o estado para concorrência otimista verificações.<br /><br /> Para obter mais informações sobre o provedor LINQ to SQL, consulte [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Para obter mais informações sobre o Object Relational Designer, consulte [ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|O provedor LINQ to XML permite consultar e modificar XML. Você pode modificar o XML na memória, ou você pode carregar XML de e salvar XML em um arquivo.<br /><br /> Além disso, o provedor LINQ to XML permite literais XML e propriedades de eixo XML que permitem escrever XML diretamente em seu código Visual Basic. Para obter mais informações, consulte [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|O provedor LINQ to DataSet permite consultar e atualizar dados em um [!INCLUDE[vstecado](~/includes/vstecado-md.md)] conjunto de dados. Você pode adicionar o poder do LINQ para aplicativos que usam conjuntos de dados para simplificar e estender seus recursos para consultar, agregar e atualizar os dados no conjunto de dados.<br /><br /> Para obter mais informações, consulte [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Estrutura de uma consulta LINQ  
 Uma consulta LINQ, geralmente conhecida como uma *expressão de consulta*, consiste em uma combinação de cláusulas de consulta que identificam as fontes de dados e variáveis de iteração para a consulta. Uma expressão de consulta também pode incluir instruções para classificação, filtragem, agrupamento e unindo ou cálculos para aplicar a fonte de dados. Sintaxe de expressão de consulta é semelhante à sintaxe do SQL; Portanto, você pode achar grande parte da sintaxe familiar.  
  
 Uma expressão de consulta começa com um `From` cláusula. Essa cláusula identifica os dados de origem para uma consulta e as variáveis que são usadas para se referir a cada elemento da fonte de dados individualmente. Essas variáveis são denominadas *variáveis de alcance* ou *variáveis de iteração*. O `From` cláusula é necessária para uma consulta, exceto para `Aggregate` consultas, em que o `From` cláusula é opcional. Depois que o escopo e a fonte da consulta são identificados na `From` ou `Aggregate` cláusulas, você pode incluir qualquer combinação de cláusulas de consulta para refinar a consulta. Para obter detalhes sobre cláusulas de consulta, consulte operadores de consulta de LINQ do Visual Basic, mais adiante neste tópico. Por exemplo, a consulta a seguir identifica um conjunto de dados do cliente como o `customers` variável e uma variável de iteração chamada `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 Este exemplo é uma consulta válida por si só; No entanto, a consulta se torna muito mais poderosa quando você adicionar mais cláusulas de consulta para refinar os resultados. Por exemplo, você pode adicionar um `Where` cláusula para filtrar o resultado por um ou mais valores. Expressões de consulta são uma única linha de código; Você apenas pode acrescentar cláusulas de consulta adicionais ao final da consulta. Você pode dividir uma consulta em várias linhas de texto para melhorar a legibilidade, usando o caractere de sublinhado (\_) o caractere de continuação de linha. O exemplo de código a seguir mostra um exemplo de uma consulta que inclui um `Where` cláusula.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 Outra cláusula de consulta poderosa é a `Select` cláusula, que permite retornar somente os campos selecionados da fonte de dados. Consultas LINQ retornam coleções enumeráveis de objetos fortemente tipados. Uma consulta pode retornar uma coleção de tipos anônimos ou tipos nomeados. Você pode usar o `Select` cláusula para retornar apenas um único campo da fonte de dados. Quando você fizer isso, o tipo da coleção retornada é o tipo daquele campo único. Você também pode usar o `Select` cláusula para retornar vários campos da fonte de dados. Quando você fizer isso, o tipo da coleção retornada é um novo tipo anônimo. Você também pode combinar os campos retornados pela consulta para os campos de um tipo nomeado especificado. O exemplo de código a seguir mostra uma expressão de consulta que retorna uma coleção de tipos anônimos que possuem membros preenchidos com dados dos campos da fonte de dados selecionados.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 Consultas LINQ também podem ser usadas para combinar várias fontes de dados e retornar um único resultado. Isso pode ser feito com um ou mais `From` cláusulas, ou usando o `Join` ou `Group Join` cláusulas de consulta. O exemplo de código a seguir mostra uma expressão de consulta que combina dados de cliente e pedido e retorna uma coleção de tipos anônimas contendo dados do cliente e pedido.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 Você pode usar o `Group Join` cláusula para criar um resultado de consulta hierárquico que contém uma coleção de objetos customer. Cada objeto customer tem uma propriedade que contém uma coleção de todos os pedidos desse cliente. O exemplo de código a seguir mostra uma expressão de consulta que combina dados de cliente e pedido como um resultado hierárquico e retorna uma coleção de tipos anônimos. A consulta retorna um tipo que inclui um `CustomerOrders` propriedade que contém uma coleção de dados de pedidos do cliente. Ele também inclui um `OrderTotal` propriedade que contém a soma dos totais para todos os pedidos desse cliente. (Esta consulta é equivalente a um LEFT OUTER JOIN).  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 Há várias adicionais operadores de consulta LINQ que você pode usar para criar expressões de consulta eficiente. A próxima seção deste tópico discute as várias cláusulas de consulta que você pode incluir em uma expressão de consulta. Para obter detalhes sobre cláusulas de consulta do Visual Basic, consulte [consultas](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Operadores de consulta LINQ do Visual Basic  

As classes de <xref:System.Linq> namespace e em outros namespaces que dão suporte a consultas LINQ incluem métodos que você pode chamar para criar e refinar consultas com base nas necessidades do seu aplicativo. Visual Basic inclui palavras-chave para as seguintes cláusulas de consulta comuns. Para obter detalhes sobre cláusulas de consulta do Visual Basic, consulte [consultas](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Cláusula From

Qualquer um [ `From` cláusula](../../../../visual-basic/language-reference/queries/from-clause.md) ou um `Aggregate` cláusula é necessária para iniciar uma consulta. Um `From` cláusula Especifica uma coleção de origem e uma variável de iteração para uma consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>cláusula Select

Opcional. Um [ `Select` cláusula](../../../../visual-basic/language-reference/queries/select-clause.md) declara um conjunto de variáveis de iteração para uma consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

Se um `Select` cláusula não for especificada, as variáveis de iteração para a consulta consistem as variáveis de iteração especificadas pela `From` ou `Aggregate` cláusula.

### <a name="where-clause"></a>Cláusula Where

Opcional. Um [ `Where` cláusula](../../../../visual-basic/language-reference/queries/where-clause.md) Especifica uma condição de filtragem para uma consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Cláusula Order By]

| Opcional. Uma [ `Order By` cláusula](../../../../visual-basic/language-reference/queries/order-by-clause.md) Especifica a ordem de classificação para colunas em uma consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>cláusula Join

Opcional. Um [ `Join` cláusula](../../../../visual-basic/language-reference/queries/join-clause.md) combina duas coleções em uma única coleção. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>cláusula Group By

Opcional. Um [ `Group By` cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md) agrupa os elementos de um resultado de consulta. Ele pode ser usado para aplicar funções de agregação a cada grupo. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>cláusula Group Join

Opcional. Um [ `Group Join` cláusula](../../../../visual-basic/language-reference/queries/group-join-clause.md) combina duas coleções em uma única coleção hierárquica. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>cláusula Aggregate

Qualquer um [ `Aggregate` cláusula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ou um `From` cláusula é necessária para iniciar uma consulta. Um `Aggregate` cláusula aplica um ou mais funções de agregação a uma coleção. Por exemplo, você pode usar o `Aggregate` cláusula para calcular uma soma de todos os elementos retornados por uma consulta, como o exemplo a seguir faz.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

Você também pode usar o `Aggregate` cláusula para modificar uma consulta. Por exemplo, você pode usar o `Aggregate` cláusula para executar um cálculo em uma coleção relacionada de consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>cláusula Let

Opcional. Um [ `Let` cláusula](../../../../visual-basic/language-reference/queries/let-clause.md) calcula um valor e o atribui a uma nova variável na consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>cláusula Distinct

Opcional. Um `Distinct` cláusula restringe os valores da variável de iteração atual para eliminar valores duplicados nos resultados da consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>cláusula Skip

Opcional. Um [ `Skip` cláusula](../../../../visual-basic/language-reference/queries/skip-clause.md) ignora um número especificado de elementos em uma coleção e retorna os elementos restantes. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>cláusula Skip While

Opcional. Um [ `Skip While` cláusula](../../../../visual-basic/language-reference/queries/skip-while-clause.md) ignora elementos em uma coleção, desde que uma condição especificada seja `true` e, em seguida, retorna os elementos restantes. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>cláusula Take

Opcional. Um [ `Take` cláusula](../../../../visual-basic/language-reference/queries/take-clause.md) retorna um número especificado de elementos contíguos do início de uma coleção. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>cláusula Take While

Opcional. Um [ `Take While` cláusula](../../../../visual-basic/language-reference/queries/take-while-clause.md) inclui elementos em uma coleção, desde que uma condição especificada seja `true` e ignora os elementos restantes. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Usar recursos adicionais de consulta LINQ  
  
Você pode usar recursos adicionais de consulta LINQ chamando membros dos tipos enumeráveis e consultáveis fornecidos pelo LINQ. Você pode usar esses recursos adicionais, chamando um operador de consulta específica no resultado de uma expressão de consulta. Por exemplo, o exemplo a seguir usa o <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> método para combinar os resultados das duas consultas em um resultado da consulta. Ele usa o <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> método para retornar o resultado da consulta como uma lista genérica.
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 Para obter detalhes sobre recursos adicionais do LINQ, consulte [visão geral de operadores de consulta padrão](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Conectar-se ao banco de dados usando LINQ to SQL  
 No Visual Basic, você deve identificar os objetos de banco de dados do SQL Server, como tabelas, exibições e procedimentos armazenados, que você deseja acessar por meio de um LINQ para arquivo SQL. Um arquivo LINQ to SQL tem uma extensão. dbml.  
  
 Quando você tiver uma conexão válida para um banco de dados do SQL Server, você pode adicionar um **Classes LINQ to SQL** modelo de item ao seu projeto. Isso exibirá o Object Relational Designer (O/R designer). O O/R Designer permite que você arraste os itens que você deseja acessar no código do **Gerenciador de servidores**/**Database Explorer** na superfície do designer. O arquivo LINQ to SQL adiciona um <xref:System.Data.Linq.DataContext> objeto ao seu projeto. Este objeto inclui propriedades e coleções para as tabelas e exibições que você deseja acesso e métodos para os procedimentos armazenados que você deseja chamar. Depois de salvar suas alterações para o arquivo LINQ to SQL (. dbml), você pode acessar esses objetos no seu código referenciando o <xref:System.Data.Linq.DataContext> objeto definido pelo Designer relacional de objetos. O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo LINQ to SQL. Por exemplo, um arquivo LINQ to SQL denominado dbml criará um <xref:System.Data.Linq.DataContext> objeto chamado `NorthwindDataContext`.  
  
 Para obter exemplos com instruções passo a passo, consulte [como: Consultar um banco de dados](how-to-query-a-database-by-using-linq.md) e [como: Chamar um procedimento armazenado](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Funcionalidades do Visual Basic que suportam LINQ  
 Visual Basic inclui outros recursos notáveis que tornam o uso de LINQ simples e reduzem a quantidade de código que você deve escrever para executar consultas LINQ. Eles incluem o seguinte:  
  
- **Tipos anônimos**, que permitem que você crie um novo tipo com base em um resultado de consulta.  
  
- **Variáveis de tipo implícito**, que permitem adiar a especificação de um tipo e deixar o compilador inferir o tipo com base no resultado da consulta.  
  
- **Métodos de extensão**, que permitem estender um tipo existente com seus próprios métodos sem modificar o próprio tipo.  
  
 Para obter detalhes, consulte [Visual Basic recursos que suporte LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Execução de consultas adiadas e imediatas

 Execução da consulta é separada da criação de uma consulta. Depois que uma consulta é criada, sua execução é disparada por um mecanismo separado. Uma consulta pode ser executada assim que ele é definido (*execução imediata*), ou a definição pode ser armazenada e a consulta pode ser executada posteriormente (*execução adiada*).  
  
 Por padrão, quando você cria uma consulta, a consulta em si não é executada imediatamente. Em vez disso, a definição de consulta é armazenada na variável que é usado para referenciar o resultado da consulta. Quando a variável de resultados de consulta for acessada mais tarde no código, como em um `For…Next` loop, a consulta é executada. Esse processo é conhecido como *execução adiada*.  
  
 Consultas também podem ser executadas quando eles são definidos, o que é conhecido como *execução imediata*. Você pode disparar a execução imediata, aplicando um método que exige acesso aos elementos individuais do resultado da consulta. Isso pode ser o resultado de uma função de agregação, como `Count`, `Sum`, `Average`, `Min`, ou `Max`. Para obter mais informações sobre funções de agregação, consulte [cláusula Aggregate](../../../language-reference/queries/aggregate-clause.md).  
  
 Usando o `ToList` ou `ToArray` métodos também forçará a execução imediata. Isso pode ser útil quando você deseja executar a consulta imediatamente e armazenar em cache os resultados. Para obter mais informações sobre esses métodos, consulte [convertendo tipos de dados](../../concepts/linq/converting-data-types.md).  
  
 Para obter mais informações sobre a execução da consulta, consulte [escrever sua primeira consulta de LINQ](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML no Visual Basic  
 Os recursos XML no Visual Basic incluem literais XML e propriedades de eixo XML, que permitem facilmente criar, acessarem, consultar e modificar XML no seu código. Literais XML permitem escrever XML diretamente em seu código. O compilador do Visual Basic trata o XML como um objeto de dados de primeira classe.  
  
 O exemplo de código a seguir mostra como criar um elemento XML, acessar seus subelementos e atributos e consultar o conteúdo do elemento usando LINQ.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Para obter mais informações, consulte [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Recursos relacionados  
  
|Tópico|Descrição|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Descreve os recursos XML no Visual Basic que podem ser consultados e que permitem incluir XML como objetos de dados de primeira classe no seu código Visual Basic.|  
|[Consultas](../../../language-reference/queries/index.md)|Fornece informações de referência sobre as cláusulas de consulta que estão disponíveis no Visual Basic.|  
|[LINQ (Consulta Integrada à Linguagem)](../../concepts/linq/index.md)|Inclui informações gerais, orientação de programação e exemplos para LINQ.|  
|[LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)|Inclui informações gerais, orientação de programação e exemplos para LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Inclui informações gerais, orientação de programação e exemplos para LINQ to Objects.|  
|[LINQ to ADO.NET (página do portal)](../../concepts/linq/linq-to-adonet-portal-page.md)|Inclui links para informações gerais, orientação de programação e exemplos para LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Inclui informações gerais, orientação de programação e exemplos para LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Como e tópicos de instruções passo a passo
 [Como: Consultar um banco de dados](how-to-query-a-database-by-using-linq.md)  
  
 [Como: Chamar um procedimento armazenado](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Como: Modificar dados em um banco de dados](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Como: Combinar dados com junções](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Como: Classificar os resultados de consulta](how-to-sort-query-results-by-using-linq.md)  
  
 [Como: Filtrar resultados de consulta](how-to-filter-query-results-by-using-linq.md)  
  
 [Como: Contar, somar ou fazer média de dados](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Como: Localizar o valor mínimo ou máximo em um resultado de consulta](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Capítulos do livro em destaque  
 [Capítulo 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) em [programação Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](../../concepts/linq/index.md)
- [Visão geral do LINQ to XML no Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [Visão geral de LINQ to DataSet](~/docs/framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)
- [Ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
