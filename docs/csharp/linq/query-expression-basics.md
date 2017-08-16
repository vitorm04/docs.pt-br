---
title: "Noções básicas sobre expressões de consulta"
description: "Apresenta os conceitos relacionados a expressões de consulta"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: be8e2374f89366c6a98df900674a957bd2f531cc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="query-expression-basics"></a>Noções básicas sobre expressões de consulta

## <a name="what-is-a-query-and-what-does-it-do"></a>O que é uma consulta e o que ela faz? 

 Uma *consulta* é um conjunto de instruções que descreve quais dados recuperar de uma determinada fonte de dados (ou fontes) e que forma e organização os dados retornados devem ter. Uma consulta é diferente dos resultados que ela produz.  
  
 Em geral, os dados de origem são organizados de forma lógica como uma sequência de elementos do mesmo tipo. Por exemplo, uma tabela de banco de dados SQL contém uma sequência de linhas. Em um arquivo XML, há uma "sequência" de elementos XML (embora eles estejam organizados hierarquicamente em uma estrutura de árvore). Uma coleção na memória contém uma sequência de objetos. 
  
 Do ponto de vista do aplicativo, o tipo específico e a estrutura dos dados de origem original não são importantes. O aplicativo sempre vê os dados de origem como uma coleção de <xref:System.Collections.Generic.IEnumerable%601> ou de <xref:System.Linq.IQueryable%601>. Por exemplo, no LINQ to XML, os dados de origem ficam visíveis como um `IEnumerable`\<<xref:System.Xml.Linq.XElement>>.  
  
 Dada essa sequência de origem, uma consulta pode executar uma das três ações:  
  
-   Recuperar um subconjunto dos elementos para produzir uma nova sequência sem modificar os elementos individuais. A consulta pode, em seguida, classificar ou agrupar a sequência retornada de várias maneiras, conforme mostrado no exemplo a seguir (suponha que `scores` é um `int[]`):  
  
     [!code-cs[csrefQueryExpBasics#45](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]  
  
-   Recuperar uma sequência de elementos, como no exemplo anterior, mas transformá-los em um novo tipo de objeto. Por exemplo, uma consulta pode recuperar apenas os sobrenomes de determinados registros de cliente em uma fonte de dados. Ou pode recuperar o registro completo e, em seguida, usá-lo para construir outro tipo de objeto na memória ou até mesmo dados XML antes de gerar a sequência de resultados final. O exemplo a seguir mostra uma projeção de um `int` para um `string`. Observe o novo tipo de `highScoresQuery`.  
  
     [!code-cs[csrefQueryExpBasics#46](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]  
  
-   Recuperar um valor singleton sobre os dados de origem, como:  
  
    -   O número de elementos que correspondem a uma determinada condição.  
  
    -   O elemento que tem o maior ou menor valor.  
  
    -   O primeiro elemento que corresponde a uma condição ou a soma dos valores específicos em um conjunto de elementos especificado. Por exemplo, a consulta a seguir retorna o número pontuações maiores que 80 na matriz de inteiros `scores`:  
  
     [!code-cs[csrefQueryExpBasics#47](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]  
  
     No exemplo anterior, observe o uso de parênteses ao redor da expressão de consulta antes da chamada para o método `Count`. Também é possível expressar isso usando uma nova variável para armazenar o resultado concreto. Essa técnica é mais legível porque mantém a variável que armazena a consulta separada da consulta que armazena um resultado.  
  
     [!code-cs[csrefQueryExpBasics#48](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]  
  
 No exemplo anterior, a consulta é executada na chamada para `Count`, pois `Count` deve iterar os resultados para determinar o número de elementos retornados por `highScoresQuery`.  
  
## <a name="what-is-a-query-expression"></a>O que é uma expressão de consulta?  

 Uma *expressão de consulta* é uma consulta expressada na sintaxe da consulta. Uma expressão de consulta é um constructo de linguagem de primeira classe. É exatamente como qualquer outra expressão e pode ser usada em qualquer contexto em que uma expressão C# é válida. Uma expressão de consulta consiste em um conjunto de cláusulas escritas em uma sintaxe declarativa semelhante ao SQL ou XQuery. Cada cláusula, por sua vez, contém uma ou mais expressões C# e essas expressões podem ser uma expressão de consulta ou conter uma expressão de consulta.  
  
 Uma expressão de consulta deve começar com uma cláusula [from](../language-reference/keywords/from-clause.md) e deve terminar com uma cláusula [select](../language-reference/keywords/select-clause.md) ou [group](../language-reference/keywords/group-clause.md). Entre a primeira cláusula `from` e a última cláusula `select` ou `group`, ela pode conter uma ou mais dessas cláusulas opcionais: [where](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [join](../language-reference/keywords/join-clause.md), [let](../language-reference/keywords/let-clause.md) e até mesmo cláusulas [from](../language-reference/keywords/from-clause.md) adicionais. Você também pode usar a palavra-chave [into](../language-reference/keywords/into.md) para permitir que o resultado de uma cláusula `join` ou `group` sirva como a fonte para cláusulas de consulta adicionais na mesma expressão de consulta.  
  
### <a name="query-variable"></a>Variável da consulta  
 
 Em LINQ, uma variável de consulta é qualquer variável que armazena uma *consulta* em vez dos *resultados* de uma consulta. Mais especificamente, uma variável de consulta é sempre um tipo enumerável que produzirá uma sequência de elementos quando for iterada em uma instrução `foreach` ou uma chamada direta para seu método `IEnumerator.MoveNext`.  
  
 O exemplo de código a seguir mostra uma expressão de consulta simples com uma fonte de dados, uma cláusula de filtragem, uma cláusula de ordenação e nenhuma transformação dos elementos de origem. A cláusula `select` termina a consulta.  
  
 [!code-cs[csrefQueryExpBasics#49](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]  
  
 No exemplo anterior, `scoreQuery` é uma *variável de consulta*, o que às vezes é chamado apenas de uma *consulta*. A variável de consulta não armazena nenhum dado de resultado real, que é produzido no loop `foreach`. E quando instrução `foreach` é executada, os resultados da consulta não são retornados pela variável de consulta `scoreQuery`. Em vez disso, eles são retornados pela variável de iteração `testScore`. A variável `scoreQuery` pode ser iterada em um segundo loop `foreach`. Ele produzirá os mesmos resultados contanto que nem ele nem a fonte de dados tenham sido modificados.  
  
 Uma variável de consulta pode armazenar uma consulta que é expressada na sintaxe de consulta ou na sintaxe de método ou uma combinação das duas. Nos exemplos a seguir, `queryMajorCities` e `queryMajorCities2` são variáveis de consulta:  
  
 [!code-cs[csrefQueryExpBasics#50](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]  
  
 Por outro lado, os dois exemplos a seguir mostram variáveis que não são variáveis de consulta embora sejam inicializadas com uma consulta. Elas não são variáveis de consulta porque armazenam resultados:  
  
 [!code-cs[csrefQueryExpBasics#51](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]  
  
 Para obter mais informações sobre as diferentes maneiras de expressar consultas, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Tipagem explícita e implícita de variáveis de consulta  
 
 Esta documentação normalmente fornece o tipo explícito da variável de consulta para mostrar a relação de tipo entre a variável de consulta e a [cláusula select](../language-reference/keywords/select-clause.md). No entanto, você também pode usar a palavra-chave [var](../language-reference/keywords/var.md) para instruir o compilador a inferir o tipo de uma variável de consulta (ou qualquer outra variável local) em tempo de compilação. Por exemplo, o exemplo de consulta que foi mostrado anteriormente neste tópico também pode ser expressado usando a tipagem implícita:  
  
 [!code-cs[csrefQueryExpBasics#52](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]  
  
 Para obter mais informações, consulte [Variáveis locais de tipo implícito](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) e [Relacionamentos de tipo em operações de consulta LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
### <a name="starting-a-query-expression"></a>Iniciando uma expressão de consulta  
 
 Uma expressão de consulta deve começar com uma cláusula `from`. Especifica uma fonte de dados junto com uma variável de intervalo. A variável de intervalo representa cada elemento sucessivo na sequência de origem como a sequência de origem que está sendo percorrida. A variável de intervalo é fortemente tipada com base no tipo dos elementos na fonte de dados. No exemplo a seguir, como `countries` é uma matriz de objetos `Country`, a variável de intervalo também é tipada como `Country`. Como a variável de intervalo é fortemente tipada, você pode usar o operador ponto para acessar todos os membros disponíveis do tipo.  
  
 [!code-cs[csrefQueryExpBasics#53](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]  
  
 A variável de intervalo está no escopo até a consulta ser encerrada com ponto e vírgula ou com uma cláusula *continuation*.  
  
 Uma expressão de consulta pode conter várias cláusulas `from`. Use cláusulas `from` adicionais quando cada elemento na sequência de origem for uma coleção em si ou contiver uma coleção. Por exemplo, suponha que você tem uma coleção de objetos `Country` e cada um dos quais contém uma coleção de objetos `City` chamada `Cities`. Para consular os objetos `City` em cada `Country`, use duas cláusulas `from` como mostrado aqui:  
  
 [!code-cs[csrefQueryExpBasics#54](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]  
  
 Para obter mais informações, consulte [Cláusula from](../language-reference/keywords/from-clause.md).  
  
### <a name="ending-a-query-expression"></a>Encerrando uma expressão de consulta  
 
 Uma expressão de consulta deve ser encerrada com uma cláusula `group` ou uma cláusula `select`.  
  
#### <a name="group-clause"></a>Cláusula group  
 
 Use a cláusula `group` para produzir uma sequência de grupos organizada por uma chave que você especificar. A chave pode ter qualquer tipo de dados. Por exemplo, a consulta a seguir cria uma sequência de grupos que contém um ou mais objetos `Country` e cuja chave é um valor `char`.  
  
 [!code-cs[csrefQueryExpBasics#55](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]  
  
 Para obter mais informações sobre o agrupamento, consulte [Cláusula group](../language-reference/keywords/group-clause.md).  
  
#### <a name="select-clause"></a>Cláusula select  
 Use a cláusula `select` para produzir todos os outros tipos de sequências. Uma cláusula `select` simples produz apenas uma sequência do mesmo tipo dos objetos contidos na fonte de dados. Neste exemplo, a fonte de dados contém objetos `Country`. A cláusula `orderby` simplesmente classifica os elementos em uma nova ordem e a cláusula `select` produz uma sequência dos objetos `Country` reordenados.  
  
 [!code-cs[csrefQueryExpBasics#56](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]  
  
 A cláusula `select` pode ser usada para transformar dados de origem em sequências de novos tipos. Essa transformação também é chamada de *projeção*. No exemplo a seguir, a cláusula `select` *projeta* uma sequência de tipos anônimos que contém apenas um subconjunto dos campos no elemento original. Observe que os novos objetos são inicializados usando um inicializador de objeto.  
  
 [!code-cs[csrefQueryExpBasics#57](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]  
  
 Para obter mais informações sobre todas as maneiras que uma cláusula `select` pode ser usada para transformar os dados de origem, consulte [Cláusula select](../language-reference/keywords/select-clause.md).  
  
#### <a name="continuations-with-into"></a>Continuações com "into"  
 
 Você pode usar a palavra-chave `into` em uma cláusula `select` ou `group` para criar um identificador temporário que armazena uma consulta. Faça isso quando precisar executar operações de consulta adicionais em uma consulta após a operação de agrupamento ou seleção. No exemplo a seguir `countries` são agrupados de acordo com a população em intervalos de 10 milhões. Depois que esses grupos são criados, cláusulas adicionais filtram alguns grupos e, em seguida, classificam os grupos em ordem crescente. Para executar essas operações adicionais, a continuação representada por `countryGroup` é necessária.  
  
 [!code-cs[csrefQueryExpBasics#58](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]  
  
 Para obter mais informações, consulte [into](../language-reference/keywords/into.md).  
  
### <a name="filtering-ordering-and-joining"></a>Filtragem, ordenação e junção

 Entre a cláusula `from` inicial e a cláusula `select` ou `group` final, todas as outras cláusulas (`where`, `join`, `orderby`, `from`, `let`) são opcionais. Todas as cláusulas opcionais podem ser usadas várias vezes ou nenhuma vez no corpo de uma consulta.  
  
#### <a name="where-clause"></a>Cláusula where  

 Use a cláusula `where` para filtrar os elementos dos dados de origem com base em uma ou mais expressões de predicado. A cláusula `where` no exemplo a seguir tem um predicado com duas condições.  
  
 [!code-cs[csrefQueryExpBasics#59](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]  
  
 Para obter mais informações, consulte [Cláusula where](../language-reference/keywords/where-clause.md).  
  
#### <a name="orderby-clause"></a>Cláusula orderby

 Use a cláusula `orderby` para classificar os resultados em ordem crescente ou decrescente. Você também pode especificar as ordens de classificação secundárias. O exemplo a seguir executa uma classificação primária nos objetos `country` usando a propriedade `Area`. Em seguida, ele executa a classificação secundária usando a propriedade `Population`.  
  
 [!code-cs[csrefQueryExpBasics#60](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]  
  
 A palavra-chave `ascending` é opcional. Será a ordem de classificação padrão se nenhuma ordem for especificada. Para obter mais informações, consulte [Cláusula orderby](../language-reference/keywords/orderby-clause.md).  
  
#### <a name="join-clause"></a>Cláusula join

 Use a cláusula `join` para associar e/ou combinar elementos de uma fonte de dados com elementos de outra fonte de dados com base em uma comparação de igualdade entre as chaves especificadas em cada elemento. Na LINQ, as operações join são executadas em sequências de objetos cujos elementos são de tipos diferentes. Após ter unido duas sequências, você deve usar uma instrução `select` ou `group` para especificar qual elemento armazenar na sequência de saída. Você também pode usar um tipo anônimo para combinar propriedades de cada conjunto de elementos associados em um novo tipo para a sequência de saída. O exemplo a seguir associa objetos `prod` cuja propriedade `Category` corresponde a uma das categorias na matriz de cadeias de caracteres `categories`. Produtos cuja `Category` não corresponde a nenhuma cadeia de caracteres em `categories` são filtrados. A instrução `select` projeta um novo tipo cujas propriedades são tiradas de `cat` e `prod`.  
  
 [!code-cs[csrefQueryExpBasics#61](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]  
  
 Você também pode executar uma junção de grupo armazenando os resultados da operação `join` em uma variável temporária usando a palavra-chave [into](../language-reference/keywords/into.md). Para obter mais informações, consulte [Cláusula join](../language-reference/keywords/join-clause.md).  
  
#### <a name="let-clause"></a>Cláusula let 

 Use a cláusula `let` para armazenar o resultado de uma expressão, como uma chamada de método, em uma nova variável de intervalo. No exemplo a seguir, a variável de intervalo `firstName` armazena o primeiro elemento da matriz de cadeias de caracteres que é retornado pelo `Split`.  
  
 [!code-cs[csrefQueryExpBasics#62](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]  
  
 Para obter mais informações, consulte [Cláusula let](../language-reference/keywords/let-clause.md).  
  
### <a name="subqueries-in-a-query-expression"></a>Subconsultas em uma expressão de consulta  

 Uma cláusula de consulta pode conter uma expressão de consulta, que às vezes é chamada de *subconsulta*. Cada subconsulta começa com sua própria cláusula `from` que não necessariamente aponta para a mesma fonte de dados na primeira cláusula `from`. Por exemplo, a consulta a seguir mostra uma expressão de consulta que é usada na instrução select para recuperar os resultados de uma operação de agrupamento.  
  
 [!code-cs[csrefQueryExpBasics#63](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]  
  
 Para obter mais informações, consulte [Como executar uma subconsulta em uma operação de agrupamento](perform-a-subquery-on-a-grouping-operation.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de programação em C#](../programming-guide/index.md)   
 [Expressões de consulta LINQ](index.md)   
 [Palavras-chave de consulta (LINQ)](../language-reference/keywords/query-keywords.md)   
 [Visão geral de operadores de consulta padrão](../programming-guide/concepts/linq/standard-query-operators-overview.md)

