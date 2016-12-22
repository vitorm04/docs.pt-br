---
title: "No&#231;&#245;es b&#225;sicas sobre express&#245;es de consulta (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "consultas [LINQ in C#], noções básicas"
  - "expressões de consulta [LINQ em C#], noções básicas"
  - "expressões de consulta [LINQ em C#], execução de consulta"
ms.assetid: d3e1f4e6-1cf0-4066-87e3-1a42387223a6
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# No&#231;&#245;es b&#225;sicas sobre express&#245;es de consulta (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## O que é uma consulta e o que ele faz?  
 A  *consulta* é um conjunto de instruções que descreve quais dados a recuperar de uma determinada fonte de dados \(ou origens\) e qual forma e a organização devem ter aos dados retornados.  Uma query é diferenciada a partir dos resultados que ela produz.  
  
 Geralmente, os dados de origem são organizados logicamente como uma sequência de elementos do mesmo tipo.  Uma tabela de um banco de dados SQL contém uma sequência de linhas.  Da mesma forma, um [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]<xref:System.Data.DataTable> contém uma seqüência de <xref:System.Data.DataRow> objetos.   Em um arquivo XML, existe uma "sequência" de elementos XML \(apesar destes serem organizados hierarquicamente em uma estrutura de árvore\).  Uma coleçao na mémoria contém uma sequência de objetos.  
  
 Do ponto de vista do aplicativo, o tipo específico e a estrutura dos dados de origem original não é importante.  O aplicativo sempre vê os dados de origem como um <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601> coleção.  Na [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], os dados de origem são tornados visíveis como um `IEnumerable`\<<xref:System.Xml.Linq.XElement>\>.  In [!INCLUDE[linq_dataset](../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], it is an `IEnumerable`\<<xref:System.Data.DataRow>\>.  Na [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)], é um `IEnumerable` ou `IQueryable` de quaisquer objetos personalizados que você definiu para representar os dados na tabela SQL.  
  
 Dada essa seqüência de origem, uma consulta pode fazer uma destas três coisas:  
  
-   Recupere um subconjunto dos elementos para produzir uma nova seqüência sem modificar os elementos individuais.  A consulta pode, em seguida, classificar ou agrupar a seqüência retornada de várias maneiras, como mostrado no exemplo a seguir \(suponha `scores` é um `int[]`\):  
  
     [!CODE [csrefQueryExpBasics#45](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#45)]  
  
-   Recuperar uma seqüência de elementos como no exemplo anterior, mas transformá\-los para um novo tipo de objeto.  Por exemplo, uma consulta pode recuperar somente os sobrenomes de certos registros de clientes em uma fonte de dados.  Ou ele pode recuperar o registro completo e, em seguida, use\-o para construir outro tipo de objeto na memória ou até mesmo dados XML antes de gerar a seqüência de resultado final.  O exemplo a seguir mostra uma transformação de um `int` para um `string`.  Observe o novo tipo de `highScoresQuery`.  
  
     [!CODE [csrefQueryExpBasics#46](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#46)]  
  
-   Recupere um valor singleton sobre dados de origem, tais como:  
  
    -   O número de elementos que coincidam com uma determinada condição.  
  
    -   O elemento que contém o valor maior ou menor.  
  
    -   O primeiro elemento corresponde a uma condição ou a soma dos valores específicos em um conjunto especificado de elementos.  Por exemplo, o consulta a seguir retorna o número de pontuações mais de 80 a partir do `scores` matriz de inteiros:  
  
     [!CODE [csrefQueryExpBasics#47](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#47)]  
  
     No exemplo anterior, observe o uso de parênteses em torno da expressão de consulta antes da chamada para o `Count` método.  Você também pode expressar isso usando uma nova variável para armazenar o resultado de concreto.  Essa técnica é mais legível, porque ele mantém a variável que armazenam a consulta separada da consulta que armazena um resultado.  
  
     [!CODE [csrefQueryExpBasics#48](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#48)]  
  
 No exemplo anterior, a consulta é executada na chamada para `Count`, pois `Count` deve iterar nos resultados para determinar o número de elementos retornados por `highScoresQuery`.  
  
## O que é uma expressão de consulta?  
 A  *expressão de consulta* é uma consulta expressa na sintaxe de consulta.  Uma expressão de consulta é uma construção de linguagem de primeira classe.  Ele é exatamente como qualquer outra expressão e pode ser usado em qualquer contexto em que uma expressão de C\# é válida.  Uma expressão de consulta consiste em um conjunto de cláusulas escrito na sintaxe declarativa semelhante a SQL ou XQuery.  Cada cláusula por sua vez contém uma ou mais expressões C\# e essas expressões podem eles próprios ser uma expressão de consulta ou conter uma expressão de consulta.  
  
 Uma expressão de consulta deve começar com um  [de](../../../visual-basic/language-reference/queries/from-clause.md) cláusula e deve terminar com um  [Selecionar](../../../csharp/language-reference/keywords/select-clause.md) ou  [grupo](../../../csharp/language-reference/keywords/group-clause.md) cláusula.  Entre o primeiro `from` cláusula e a última `select` ou `group` cláusula, ele pode conter uma ou mais das seguintes cláusulas opcionais:  [onde](../../../visual-basic/language-reference/queries/where-clause.md),  [orderby](../../../csharp/language-reference/keywords/orderby-clause.md),  [associação](../../../csharp/language-reference/keywords/join-clause.md),  [permitem que](../../../csharp/language-reference/keywords/let-clause.md) e até mesmo adicionais  [de](../../../visual-basic/language-reference/queries/from-clause.md) cláusulas.  Você também pode usar o  [em](../../../csharp/language-reference/keywords/into.md) palavra\-chave para permitir que o resultado de uma `join` ou `group` cláusula para servir como a origem das cláusulas de consulta adicionais na mesma expressão de consulta.  
  
### Variável de consulta  
 Na [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], uma variável de consulta é qualquer variável que armazena um  *consulta* em vez da  *resultados* de uma consulta. Mais especificamente, uma variável de consulta é sempre um tipo enumerable que produzirá uma seqüência de elementos quando ele é iterado em um `foreach` instrução ou uma chamada direta para seus `IEnumerator.MoveNext` método.  
  
 O exemplo de código a seguir mostra uma expressão de consulta simples com uma fonte de dados, uma cláusula de filtragem, uma cláusula de ordenação e sem transformação dos elementos de origem.  O `select` cláusula termina a consulta.  
  
 [!CODE [csrefQueryExpBasics#49](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#49)]  
  
 No exemplo anterior, `scoreQuery` é um  *variável de consulta,*  que às vezes é chamado como apenas um  *consulta*.  A variável de consulta não armazena nenhum dado do resultado real, que é produzido na `foreach` loop.  E quando o `foreach` instrução é executada, os resultados da consulta não são retornados através da variável de consulta `scoreQuery`.  Em vez disso, eles são devolvidos através da variável de iteração `testScore`.  O `scoreQuery` variável pode ser iterado em um segundo `foreach` loop.  Desde que foi modificada nem ele nem a fonte de dados, ele produzirá os mesmos resultados.  
  
 Uma variável de consulta pode armazenar uma consulta que é expressa na sintaxe de consulta ou sintaxe do método ou uma combinação dos dois.  Nos exemplos a seguir, ambos `queryMajorCities` e `queryMajorCities2` são variáveis de consulta:  
  
 [!CODE [csrefQueryExpBasics#50](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#50)]  
  
 Por outro lado, dois exemplos a seguir mostram as variáveis que não são variáveis de consulta, mesmo através de cada uma é inicializada com uma consulta.  Eles não são variáveis de consulta porque eles armazenam resultados:  
  
 [!CODE [csrefQueryExpBasics#51](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#51)]  
  
> [!NOTE]
>  No [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] documentação, variáveis que armazenam uma consulta tem a palavra "consulta" como parte de seus nomes.  Variáveis que armazenam um resultado real não têm "query" em seus nomes.  
  
 Para obter mais informações sobre as diferentes maneiras para consultas express, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
#### Explícitas e implícitas a digitação das variáveis de consulta  
 Esta documentação fornece geralmente do tipo explícito da variável de consulta para mostrar a relação de tipo entre a variável de consulta e o  [cláusula select](../../../csharp/language-reference/keywords/select-clause.md).  No entanto, você também pode usar o  [var](../../../csharp/language-reference/keywords/var.md) palavra\-chave para instruir o compilador para inferir o tipo de uma variável de consulta \(ou qualquer outra variável local\) em tempo de compilação.  Por exemplo, o exemplo de consulta que foi mostrado anteriormente neste tópico também pode ser expresso por meio de digitação implícita:  
  
 [!CODE [csrefQueryExpBasics#52](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#52)]  
  
 Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) e [Relacionamentos de tipo em operações de consulta LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
### Iniciando uma expressão de consulta  
 Uma expressão de consulta deve começar com um `from` cláusula.  Especifica uma fonte de dados em conjunto com uma variável de intervalo.  A variável de intervalo representa cada elemento sucessivo na seqüência de origem, como a seqüência de origem é sendo atravessada.  A variável de intervalo é fortemente tipada com base no tipo de elementos na fonte de dados.  No exemplo a seguir, porque `countries` é uma matriz de `Country` objetos, a variável de intervalo também é digitada como `Country`.  Porque a variável de intervalo tem rigidez de tipos, você pode usar o operador ponto para acessar quaisquer membros disponíveis do tipo.  
  
 [!CODE [csrefQueryExpBasics#53](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#53)]  
  
 A variável de intervalo está no escopo até que a consulta será finalizada com um ponto e vírgula ou com um  *continuação* cláusula.  
  
 Uma expressão de consulta pode conter vários `from` cláusulas.  Uso adicional `from` cláusulas quando cada elemento da seqüência de origem é uma coleção em si ou contém uma coleção.  Por exemplo, suponha que você tem uma coleção de `Country` objetos, cada um deles contém uma coleção de `City` objetos nomeados `Cities`.  A consulta a `City` objetos em cada `Country`, use dois `from` cláusulas, como mostrado aqui:  
  
 [!CODE [csrefQueryExpBasics#54](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#54)]  
  
 Para obter mais informações, consulte [Cláusula from](../../../visual-basic/language-reference/queries/from-clause.md).  
  
### Final de uma expressão de consulta  
 Uma expressão de consulta deve terminar com um um `select` cláusula ou um `group` cláusula.  
  
#### Cláusula de grupo.  
 Use o `group` cláusula para produzir uma seqüência de grupos organizados por uma chave que você especificar.  A chave pode ser qualquer tipo de dados.  Por exemplo, a consulta a seguir cria uma seqüência de grupos que contém um ou mais `Country` de objetos e cuja chave é um `char` valor.  
  
 [!CODE [csrefQueryExpBasics#55](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#55)]  
  
 Para obter mais informações sobre o agrupamento, consulte [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md).  
  
#### Cláusula Select  
 Use o `select` cláusula para produzir todos os outros tipos de seqüências.  Uma simples `select` cláusula produz apenas uma seqüência do mesmo tipo de objetos como os objetos que estão contidos na fonte de dados.  Neste exemplo, a fonte de dados contém `Country` objetos.  O `orderby` cláusula classifica apenas os elementos em uma nova ordem e o `select` cláusula produz uma seqüência do reordenados `Country` objetos.  
  
 [!CODE [csrefQueryExpBasics#56](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#56)]  
  
 O `select` cláusula pode ser usada para transformar dados de origem em seqüências de novos tipos.  Essa transformação também é chamada um  *projeção*.  No exemplo a seguir, o `select` cláusula  *projetos* uma seqüência de tipos anônimos que contém somente um subconjunto dos campos no elemento original.  Observe que os novos objetos são inicializados usando um inicializador de objeto.  
  
 [!CODE [csrefQueryExpBasics#57](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#57)]  
  
 Para obter mais informações sobre as formas que um `select` cláusula pode ser usada para transformar os dados de origem, consulte [Cláusula select](../../../csharp/language-reference/keywords/select-clause.md).  
  
#### Continuação com "em"  
 Você pode usar o `into` palavra\-chave em um `select` ou `group` cláusula para criar um identificador temporário que armazena uma consulta.  Faça isso quando você deve realizar operações de consulta adicional em uma consulta após um agrupamento ou selecionar a operação.  No exemplo a seguir `countries` são agrupados de acordo com a população em intervalos de 10 milhões.  Depois que esses grupos são o filtro criado, additional cláusulas check\-out de alguns grupos e, em seguida, para classificar os grupos em crescente da ordem.  Para executar essas operações adicionais, a continuação é representado por `countryGroup` é necessária.  
  
 [!CODE [csrefQueryExpBasics#58](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#58)]  
  
 Para obter mais informações, consulte [into](../../../csharp/language-reference/keywords/into.md).  
  
### Filtragem, ordenação e ingressando em  
 Entre o início `from` cláusula e a terminação `select` ou `group` cláusula, todas as outras cláusulas \(`where`, `join`, `orderby`, `from`, `let`\) são opcionais.  Qualquer uma das cláusulas opcionais pode ser usado nenhuma vez ou várias vezes no corpo de uma consulta.  
  
#### onde cláusula  
 Use o `where` cláusula para filtrar elementos dos dados de origem com base em uma ou mais expressões de predicado.  O `where` cláusula no exemplo a seguir possui duas predicados.  
  
 [!CODE [csrefQueryExpBasics#59](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#59)]  
  
 Para obter mais informações, consulte [Cláusula where](../../../visual-basic/language-reference/queries/where-clause.md).  
  
#### OrderBy cláusula  
 Use o `orderby` cláusula para classificar os resultados em crescente ou decrescente.  Você também pode especificar as ordens de classificação secundária.  O exemplo a seguir executa uma classificação primária sobre o `country` objetos usando o `Area` propriedade.  Em seguida, realiza uma ordenação secundária usando o `Population` propriedade.  
  
 [!CODE [csrefQueryExpBasics#60](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#60)]  
  
 O `ascending` palavra\-chave é opcional. é a ordem de classificação padrão se nenhuma ordem for especificada.  Para obter mais informações, consulte [Cláusula orderby](../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### Cláusula de associação  
 Use o `join` cláusula para associar e\/ou combinar elementos de uma fonte de dados com elementos de outra fonte de dados com base em uma comparação de igualdade entre chaves especificadas em cada elemento.  Na [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], as operações de associação são executadas em seqüências de objetos cujos elementos são tipos diferentes.  Após ter adicionado duas seqüências, você deve usar um `select` ou `group` instrução para especificar qual elemento para armazenar na seqüência de saída.  Você também pode usar um tipo anônimo para combinar a propriedades de cada conjunto de elementos associados em um novo tipo de seqüência de saída.  O exemplo a seguir associa `prod` objetos cuja `Category` propriedade corresponde a uma das categorias a `categories` matriz de cadeia de caracteres.  Produtos cujo `Category` não coincide com qualquer seqüência de caracteres em `categories` são filtrados.  O `select` instrução projeta um novo tipo cujas propriedades são tiradas de ambos `cat` e `prod`.  
  
 [!CODE [csrefQueryExpBasics#61](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#61)]  
  
 Você também pode executar uma associação de grupo, armazenando os resultados da `join` operação em uma variável temporária usando o  [em](../../../csharp/language-reference/keywords/into.md) palavra\-chave.  Para obter mais informações, consulte [Cláusula join](../../../csharp/language-reference/keywords/join-clause.md).  
  
#### permitir que a cláusula  
 Use o `let` cláusula para armazenar o resultado de uma expressão, como, por exemplo, uma chamada de método em uma nova variável de intervalo.  No exemplo a seguir, a variável de intervalo `firstName` armazena o primeiro elemento da matriz de seqüências de caracteres que é retornado por `Split`.  
  
 [!CODE [csrefQueryExpBasics#62](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#62)]  
  
 Para obter mais informações, consulte [Cláusula let](../../../csharp/language-reference/keywords/let-clause.md).  
  
### Subconsultas em uma expressão de consulta  
 Se uma cláusula de consulta pode conter uma expressão de consulta, às vezes é chamada de um  *subconsulta*.  Cada subconsulta inicia com seu próprio `from` que não necessariamente aponta para a mesma fonte de dados na primeira cláusula `from` cláusula.  Por exemplo, a consulta a seguir mostra uma expressão de consulta que é usada na instrução select para recuperar os resultados de uma operação de agrupamento.  
  
 [!CODE [csrefQueryExpBasics#63](../CodeSnippet/VS_Snippets_VBCSharp/csrefQueryExpBasics#63)]  
  
 Para obter mais informações, consulte [Como executar uma subconsulta em uma operação de agrupamento](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Visão geral de operadores de consulta padrão](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)