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
ms.openlocfilehash: c9a8149ecf4f2a1c76ba00b0f80bc703114e11ca
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660781"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Introdução a LINQ no Visual Basic
A consulta integrada à linguagem (LINQ) adiciona funcionalidades de consulta para Visual Basic e fornece recursos simples e poderosos quando você trabalha com todos os tipos de dados. Em vez de enviar uma consulta para um banco de dados a ser processado ou trabalhar com sintaxe de consulta diferente para cada tipo de dado que você está pesquisando, o LINQ apresenta consultas como parte da linguagem de Visual Basic. Ele usa uma sintaxe unificada, independentemente do tipo de dados.  
  
 O LINQ permite que você consulte dados de um banco de dados SQL Server, XML, matrizes na memória e coleções, conjuntos de ADO.NET, ou qualquer outra fonte de dado local ou remota que ofereça suporte a LINQ. Você pode fazer tudo isso com elementos de linguagem de Visual Basic comuns. Como as consultas são gravadas na linguagem Visual Basic, os resultados da consulta são retornados como objetos fortemente tipados. Esses objetos dão suporte ao IntelliSense, que permite escrever código mais rapidamente e capturar erros em suas consultas em tempo de compilação em vez de em tempo de execução. Consultas LINQ podem ser usadas como a fonte de consultas adicionais para refinar os resultados. Eles também podem ser associados a controles para que os usuários possam exibir e modificar facilmente os resultados da consulta.  
  
 Por exemplo, o exemplo de código a seguir mostra uma consulta LINQ que retorna uma lista de clientes de uma coleção e os agrupa com base em sua localização.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>Como executar os exemplos  
 Para executar os exemplos na introdução e na [estrutura de uma seção de consulta LINQ](#structure-of-a-linq-query) , inclua o código a seguir, que retorna listas de clientes e pedidos.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>Provedores de LINQ  
 Um *provedor LINQ* mapeia suas consultas Visual Basic LINQ para a fonte de dados que está sendo consultada. Quando você escreve uma consulta LINQ, o provedor usa essa consulta e a converte em comandos que a fonte de dados poderá executar. O provedor também converte dados da origem nos objetos que compõem o resultado da consulta. Por fim, ele converte objetos em dados quando você envia atualizações para a fonte de dados.  
  
 O Visual Basic inclui os seguintes provedores de LINQ.  
  
|Provider|Descrição|  
|---|---|  
|Objetos LINQ to|O provedor de LINQ to Objects permite consultar coleções e matrizes na memória. Se um objeto oferecer suporte <xref:System.Collections.IEnumerable> à interface ou <xref:System.Collections.Generic.IEnumerable%601> , o provedor de LINQ to Objects permitirá que você a consulte.<br /><br /> Você pode habilitar o provedor de LINQ to Objects importando o <xref:System.Linq> namespace, que é importado por padrão para todos os projetos de Visual Basic.<br /><br /> Para obter mais informações sobre o provedor de LINQ to Objects, consulte [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ to SQL|O provedor de LINQ to SQL permite consultar e modificar dados em um banco de SQL Server. Isso facilita mapear o modelo de objeto para um aplicativo para as tabelas e objetos em um banco de dados.<br /><br /> Visual Basic torna mais fácil trabalhar com o LINQ to SQL incluindo o Object Relational Designer (O/R Designer). Esse designer é usado para criar um modelo de objeto em um aplicativo que é mapeado para objetos em um banco de dados. O o/R Designer também fornece funcionalidade para mapear procedimentos armazenados e funções para <xref:System.Data.Linq.DataContext> o objeto, que gerencia a comunicação com o banco de dados e armazena o estado para verificações de simultaneidade otimistas.<br /><br /> Para obter mais informações sobre o provedor de LINQ to SQL, consulte [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Para obter mais informações sobre o Object Relational Designer, consulte [ferramentas de LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|O provedor de LINQ to XML permite consultar e modificar XML. Você pode modificar XML na memória, ou pode carregar XML de e salvar XML em um arquivo.<br /><br /> Além disso, o provedor de LINQ to XML habilita literais XML e propriedades de eixo XML que permitem escrever XML diretamente em seu código de Visual Basic. Para obter mais informações, consulte [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|O provedor de LINQ to DataSet permite que você consulte e atualize dados em um DataSet ADO.NET. Você pode adicionar o poder do LINQ a aplicativos que usam conjuntos de dados para simplificar e estender seus recursos para consultar, agregar e atualizar os dados em seu conjunto.<br /><br /> Para obter mais informações, consulte [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Estrutura de uma consulta LINQ  
 Uma consulta LINQ, geralmente conhecida como expressão de *consulta*, consiste em uma combinação de cláusulas de consulta que identificam as fontes de dados e as variáveis de iteração para a consulta. Uma expressão de consulta também pode incluir instruções para classificação, filtragem, agrupamento e junção, ou cálculos a serem aplicados aos dados de origem. Sintaxe de expressão de consulta é semelhante à sintaxe do SQL; Portanto, você pode achar grande parte da sintaxe familiar.  
  
 Uma expressão de consulta começa com `From` uma cláusula. Essa cláusula identifica os dados de origem para uma consulta e as variáveis que são usadas para fazer referência a cada elemento dos dados de origem individualmente. Essas variáveis são variáveis de *intervalo* nomeadas ou *variáveis*de iteração. A `From` cláusula é necessária para uma consulta, exceto para `Aggregate` consultas, em que `From` a cláusula é opcional. Depois que o escopo e a origem da consulta são identificados nas `From` cláusulas ou `Aggregate` , você pode incluir qualquer combinação de cláusulas de consulta para refinar a consulta. Para obter detalhes sobre as cláusulas de consulta, consulte Visual Basic operadores de consulta LINQ mais adiante neste tópico. Por exemplo, a consulta a seguir identifica uma coleção de fonte de dados do `customers` cliente como a variável e uma variável `cust`de iteração chamada.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 Este exemplo é uma consulta válida por si só; no entanto, a consulta se torna muito mais eficiente quando você adiciona mais cláusulas de consulta para refinar o resultado. Por exemplo, você pode adicionar uma `Where` cláusula para filtrar o resultado por um ou mais valores. As expressões de consulta são uma única linha de código; Você pode apenas acrescentar cláusulas de consulta adicionais ao final da consulta. Você pode dividir uma consulta em várias linhas de texto para melhorar a legibilidade usando o caractere de continuação de linha\_sublinhado (). O exemplo de código a seguir mostra um exemplo de uma consulta que `Where` inclui uma cláusula.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 Outra cláusula de consulta avançada é `Select` a cláusula, que permite retornar apenas os campos selecionados da fonte de dados. Consultas LINQ retornam coleções enumeráveis de objetos fortemente tipados. Uma consulta pode retornar uma coleção de tipos anônimos ou tipos nomeados. Você pode usar a `Select` cláusula para retornar apenas um único campo da fonte de dados. Quando você faz isso, o tipo da coleção retornada é o tipo desse campo único. Você também pode usar a `Select` cláusula para retornar vários campos da fonte de dados. Quando você faz isso, o tipo da coleção retornada é um novo tipo anônimo. Você também pode corresponder os campos retornados pela consulta aos campos de um tipo nomeado especificado. O exemplo de código a seguir mostra uma expressão de consulta que retorna uma coleção de tipos anônimos que têm Membros populados com dados dos campos selecionados da fonte de dados.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 Consultas LINQ também podem ser usadas para combinar várias fontes de dados e retornar um único resultado. Isso pode ser feito com uma ou mais `From` cláusulas ou usando as cláusulas `Join` de `Group Join` consulta ou. O exemplo de código a seguir mostra uma expressão de consulta que combina os dados do cliente e do pedido e retorna uma coleção de tipos anônimos que contêm os dados do cliente e do pedido.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 Você pode usar a `Group Join` cláusula para criar um resultado de consulta hierárquico que contém uma coleção de objetos Customer. Cada objeto Customer tem uma propriedade que contém uma coleção de todos os pedidos para esse cliente. O exemplo de código a seguir mostra uma expressão de consulta que combina os dados do cliente e do pedido como um resultado hierárquico e retorna uma coleção de tipos anônimos. A consulta retorna um tipo que inclui uma `CustomerOrders` propriedade que contém uma coleção de dados de pedidos para o cliente. Ele também inclui uma `OrderTotal` propriedade que contém a soma dos totais de todos os pedidos para esse cliente. (Essa consulta é equivalente a uma junção externa esquerda.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 Há vários operadores de consulta LINQ adicionais que você pode usar para criar expressões de consulta poderosas. A próxima seção deste tópico discute as várias cláusulas de consulta que você pode incluir em uma expressão de consulta. Para obter detalhes sobre Visual Basic cláusulas de consulta, consulte [consultas](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Operadores de consulta do Visual Basic LINQ  

As classes no <xref:System.Linq> namespace e os outros namespaces que oferecem suporte a consultas LINQ incluem métodos que você pode chamar para criar e refinar consultas com base nas necessidades do seu aplicativo. Visual Basic inclui palavras-chave para as seguintes cláusulas de consulta comuns. Para obter detalhes sobre Visual Basic cláusulas de consulta, consulte [consultas](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Cláusula From

`Aggregate` [ Uma`From` cláusula](../../../../visual-basic/language-reference/queries/from-clause.md) ou uma cláusula é necessária para iniciar uma consulta. Uma `From` cláusula Especifica uma coleção de origem e uma variável de iteração para uma consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>cláusula Select

Opcional. Uma cláusula declara um conjunto de variáveis de iteração para uma consulta. [ `Select` ](../../../../visual-basic/language-reference/queries/select-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

Se uma `Select` cláusula não for especificada, as variáveis de iteração da consulta consistirão nas variáveis de iteração `From` especificadas `Aggregate` pela cláusula or.

### <a name="where-clause"></a>Cláusula Where

Opcional. Uma cláusula Especifica uma condição de filtragem para uma consulta. [ `Where` ](../../../../visual-basic/language-reference/queries/where-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Cláusula order by]

| Adicional. Uma cláusula Especifica a ordem de classificação das colunas em uma consulta. [ `Order By` ](../../../../visual-basic/language-reference/queries/order-by-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>cláusula Join

Opcional. Uma cláusula combina duas coleções em uma única coleção. [ `Join` ](../../../../visual-basic/language-reference/queries/join-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>cláusula Group By

Opcional. Uma cláusula agrupa os elementos de um resultado de consulta. [ `Group By` ](../../../../visual-basic/language-reference/queries/group-by-clause.md) Ele pode ser usado para aplicar funções de agregação a cada grupo. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>cláusula Group Join

Opcional. Uma cláusula combina duas coleções em uma única coleção hierárquica. [ `Group Join` ](../../../../visual-basic/language-reference/queries/group-join-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>cláusula Aggregate

Uma cláusula ou uma `From` cláusula é necessária para iniciar uma consulta. [ `Aggregate` ](../../../../visual-basic/language-reference/queries/aggregate-clause.md) Uma `Aggregate` cláusula aplica uma ou mais funções de agregação a uma coleção. Por exemplo, você pode usar a `Aggregate` cláusula para calcular uma soma para todos os elementos retornados por uma consulta, como faz o exemplo a seguir.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

Você também pode usar a `Aggregate` cláusula para modificar uma consulta. Por exemplo, você pode usar a `Aggregate` cláusula para executar um cálculo em uma coleção de consulta relacionada. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>cláusula Let

Opcional. Uma cláusula computa um valor e o atribui a uma nova variável na consulta. [ `Let` ](../../../../visual-basic/language-reference/queries/let-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>cláusula Distinct

Opcional. Uma `Distinct` cláusula restringe os valores da variável de iteração atual para eliminar valores duplicados nos resultados da consulta. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>cláusula Skip

Opcional. Uma cláusula ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes. [ `Skip` ](../../../../visual-basic/language-reference/queries/skip-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>cláusula Skip While

Opcional. `true` [ Uma`Skip While` cláusula](../../../../visual-basic/language-reference/queries/skip-while-clause.md) ignora os elementos de uma coleção desde que uma condição especificada seja e, em seguida, retorna os elementos restantes. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>cláusula Take

Opcional. Uma cláusula retorna um número especificado de elementos contíguos do início de uma coleção. [ `Take` ](../../../../visual-basic/language-reference/queries/take-clause.md) Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>cláusula Take While

Opcional. `true` [ Uma`Take While` cláusula](../../../../visual-basic/language-reference/queries/take-while-clause.md) inclui elementos em uma coleção, desde que uma condição especificada seja e ignore os elementos restantes. Por exemplo:

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Usar recursos adicionais de consulta LINQ  
  
Você pode usar recursos adicionais de consulta LINQ chamando membros dos tipos Enumerable e consultáveis fornecidos pelo LINQ. Você pode usar esses recursos adicionais chamando um operador de consulta específico no resultado de uma expressão de consulta. Por exemplo, o exemplo a seguir usa <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> o método para combinar os resultados de duas consultas em um resultado de consulta. Ele usa o <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> método para retornar o resultado da consulta como uma lista genérica.
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 Para obter detalhes sobre recursos adicionais do LINQ, consulte [visão geral de operadores de consulta padrão](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Conectar-se a um banco de dados usando LINQ to SQL  
 No Visual Basic, você identifica os objetos de banco de dados do SQL Server, como tabelas, exibições e procedimentos armazenados, que você deseja acessar usando um arquivo LINQ to SQL. Um arquivo de LINQ to SQL tem uma extensão de. dbml.  
  
 Quando você tem uma conexão válida com um banco de dados SQL Server, você pode adicionar um modelo de item de **classes de LINQ to SQL** ao seu projeto. Isso exibirá o Object Relational Designer (O/R Designer). O o/R Designer permite arrastar os itens que você deseja acessar em seu código do **Gerenciador de servidores**/**Gerenciador de banco de dados** na superfície do designer. O arquivo de LINQ to SQL adiciona <xref:System.Data.Linq.DataContext> um objeto ao seu projeto. Esse objeto inclui propriedades e coleções para as tabelas e exibições às quais você deseja acessar e métodos para os procedimentos armazenados que você deseja chamar. Depois de salvar as alterações no arquivo LINQ to SQL (. dbml), você pode acessar esses objetos em seu código referenciando o <xref:System.Data.Linq.DataContext> objeto que é definido pelo o/R Designer. O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo de LINQ to SQL. Por exemplo, um arquivo LINQ to SQL chamado Northwind. dbml criará um <xref:System.Data.Linq.DataContext> objeto chamado. `NorthwindDataContext`  
  
 Para obter exemplos de instruções passo a passo, consulte [como: Consulte um banco](how-to-query-a-database-by-using-linq.md) de [dados e como: Chame um procedimento](how-to-call-a-stored-procedure-by-using-linq.md)armazenado.  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic recursos que dão suporte ao LINQ  
 O Visual Basic inclui outros recursos notáveis que tornam o uso do LINQ simples e reduzem a quantidade de código que você deve escrever para executar consultas LINQ. Eles incluem o seguinte:  
  
- **Tipos anônimos**, que permitem que você crie um novo tipo com base em um resultado de consulta.  
  
- **Variáveis digitadas implicitamente**, que permitem adiar a especificação de um tipo e permitir que o compilador inferirá o tipo com base no resultado da consulta.  
  
- **Métodos de extensão**, que permitem estender um tipo existente com seus próprios métodos sem modificar o próprio tipo.  
  
 Para obter detalhes, consulte [Visual Basic recursos que dão suporte ao LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Execução de consulta adiada e imediata

 A execução da consulta é separada da criação de uma consulta. Depois que uma consulta é criada, sua execução é disparada por um mecanismo separado. Uma consulta pode ser executada assim que é definida (*execução imediata*) ou a definição pode ser armazenada e a consulta pode ser executada mais tarde (*execução adiada*).  
  
 Por padrão, quando você cria uma consulta, a consulta em si não é executada imediatamente. Em vez disso, a definição de consulta é armazenada na variável que é usada para referenciar o resultado da consulta. Quando a variável de resultado da consulta é acessada posteriormente no código, `For…Next` como em um loop, a consulta é executada. Esse processo é conhecido como *execução adiada*.  
  
 As consultas também podem ser executadas quando são definidas, o que é conhecido como *execução imediata*. Você pode disparar a execução imediata aplicando um método que exige acesso a elementos individuais do resultado da consulta. Isso pode ser o resultado de incluir uma função de agregação, `Count`como `Sum` `Average`, `Min`,, ou `Max`. Para obter mais informações sobre funções de agregação, consulte [cláusula Aggregate](../../../language-reference/queries/aggregate-clause.md).  
  
 Usar os `ToList` métodos `ToArray` ou também forçará a execução imediata. Isso pode ser útil quando você deseja executar a consulta imediatamente e armazenar em cache os resultados. Para obter mais informações sobre esses métodos, consulte [convertendo tipos de dados](../../concepts/linq/converting-data-types.md).  
  
 Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML no Visual Basic  
 Os recursos XML no Visual Basic incluem literais XML e propriedades de eixo XML, que permitem criar, acessar, consultar e modificar XML em seu código facilmente. Os literais XML permitem que você grave XML diretamente em seu código. O compilador Visual Basic trata o XML como um objeto de dados de primeira classe.  
  
 O exemplo de código a seguir mostra como criar um elemento XML, acessar seus subelementos e atributos e consultar o conteúdo do elemento usando LINQ.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Para obter mais informações, consulte [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Recursos relacionados  
  
|Tópico|Descrição|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Descreve os recursos XML no Visual Basic que podem ser consultados e que permitem incluir XML como objetos de dados de primeira classe em seu código de Visual Basic.|  
|[Consultas](../../../language-reference/queries/index.md)|Fornece informações de referência sobre as cláusulas de consulta que estão disponíveis no Visual Basic.|  
|[LINQ (Consulta Integrada à Linguagem)](../../concepts/linq/index.md)|Inclui informações gerais, diretrizes de programação e exemplos para LINQ.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|Inclui informações gerais, diretrizes de programação e exemplos para LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Inclui informações gerais, diretrizes de programação e exemplos para LINQ to Objects.|  
|[LINQ to ADO.NET (página do portal)](../../concepts/linq/linq-to-adonet-portal-page.md)|Inclui links para informações gerais, diretrizes de programação e exemplos para LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Inclui informações gerais, diretrizes de programação e exemplos para LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Tópicos de instruções e instruções
 [Como: Consultar um banco de dados](how-to-query-a-database-by-using-linq.md)  
  
 [Como: Chamar um procedimento armazenado](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Como: Modificar dados em um banco de dado](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Como: Combinar dados com junções](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Como: Classificar resultados da consulta](how-to-sort-query-results-by-using-linq.md)  
  
 [Como: Filtrar resultados da consulta](how-to-filter-query-results-by-using-linq.md)  
  
 [Como: Contagem, soma ou média de dados](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Como: Localizar o valor mínimo ou máximo em um resultado de consulta](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Capítulos do livro em destaque  
 [Capítulo 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) em [programação Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](../../concepts/linq/index.md)
- [Visão geral do LINQ to XML no Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [Visão geral de LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
