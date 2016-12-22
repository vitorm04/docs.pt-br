---
title: "Escrevendo a primeira consulta LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consulta escrita [LINQ no Visual Basic]"
  - "consultas LINQ [Visual Basic]"
  - "Escrever consultas da LINQ [Visual Basic]"
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
caps.handback.revision: 56
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Escrevendo a primeira consulta LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *consulta* é uma expressão que recupera dados de uma fonte de dados. Consultas são expressas em uma linguagem de consulta dedicado. Ao longo do tempo, diferentes idiomas foram desenvolvidos para diferentes tipos de fontes de dados, por exemplo, SQL para bancos de dados relacionais e o XQuery para XML. Isso torna necessária para o desenvolvedor de aplicativos aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que tem suporte.  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] simplifica a situação, oferecendo um modelo consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, está sempre trabalhando com objetos. Use os mesmos padrões de codificação básicos para consultar e transformar dados em documentos XML, bancos de dados SQL, datasets ADO.NET e entidades, coleções do .NET Framework e outra fonte ou formato para o qual um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor está disponível. Este documento descreve as três fases da criação e uso do basic [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas.  
  
## Três estágios de uma operação de consulta  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] operações de consulta consiste em três ações:  
  
1.  Obter a fonte de dados ou fontes.  
  
2.  Crie a consulta.  
  
3.  Execute a consulta.  
  
 Em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], a execução de uma consulta é diferente da criação da consulta. Você não recuperar os dados apenas criando uma consulta. Esse ponto é abordado em mais detalhes posteriormente neste tópico.  
  
 O exemplo a seguir ilustra as três partes de uma operação de consulta. O exemplo usa uma matriz de inteiros como uma fonte de dados conveniente para fins de demonstração. No entanto, os mesmos conceitos também se aplicam a outras fontes de dados.  
  
> [!NOTE]
>  Sobre o [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic), certifique\-se de que **Option infer** é definido como **em**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Saída:  
  
 `0 2 4 6`  
  
## A fonte de dados  
 Como a fonte de dados no exemplo anterior é uma matriz, implicitamente suporta genérica <xref:System.Collections.Generic.IEnumerable%601> interface. É esse fato que permite que você use uma matriz como uma fonte de dados para um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta. Tipos que oferecem suporte a <xref:System.Collections.Generic.IEnumerable%601> ou uma interface derivada como genérica <xref:System.Linq.IQueryable%601> são chamados *tipos consultáveis*.  
  
 Como um tipo que podem ser consultado implicitamente, a matriz não requer modificação ou tratamento especial para servir como um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados. O mesmo é verdadeiro para qualquer tipo de coleção que oferece suporte a <xref:System.Collections.Generic.IEnumerable%601>, incluindo genérica <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, e outras classes na biblioteca de classes do .NET Framework.  
  
 Se os dados de origem já não implementam <xref:System.Collections.Generic.IEnumerable%601>, um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor é necessário para implementar a funcionalidade do *operadores de consulta padrão* nessa fonte de dados. Por exemplo, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] manipula o trabalho de carregamento de um documento XML em um que podem ser consultados <xref:System.Xml.Linq.XElement> tipo, conforme mostrado no exemplo a seguir. Para obter mais informações sobre operadores de consulta padrão, consulte [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Com [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], primeiro você deve criar um mapeamento relacional de objeto em tempo de design, manualmente ou usando o [LINQ to SQL Tools no Visual Studio](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2) no Visual Studio. Você escrever suas consultas em relação os objetos e em tempo de execução [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] gerencia a comunicação com o banco de dados. No exemplo a seguir, `customers` representa uma tabela específica no banco de dados, e <xref:System.Data.Linq.Table%601> oferece suporte a genéricos <xref:System.Linq.IQueryable%601>.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Para obter mais informações sobre como criar tipos específicos de fontes de dados, consulte a documentação para os diversos [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedores. \(Para obter uma lista desses provedores, consulte [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).\) A regra básica é simple: um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados é qualquer objeto que oferece suporte o genéricos <xref:System.Collections.Generic.IEnumerable%601> interface ou uma interface que herda dela.  
  
> [!NOTE]
>  Tipos, como <xref:System.Collections.ArrayList> que oferecem suporte a não genérica <xref:System.Collections.IEnumerable> interface também pode ser usada como [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fontes de dados. Para obter um exemplo que usa um <xref:System.Collections.ArrayList>, consulte [Como: consultar um ArrayList com LINQ \(Visual Basic\)](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ%20\(Visual%20Basic\).md).  
  
## A consulta  
 Na consulta, você deve especificar quais informações você deseja recuperar da fonte de dados ou fontes. Você também tem a opção de especificar como essas informações devem ser classificadas, agrupadas ou estruturadas antes de serem retornado. Para habilitar a criação da consulta, Visual Basic incorporou a nova sintaxe de consulta de linguagem.  
  
 Quando ele é executado, a consulta no exemplo a seguir retorna todos os números pares de uma matriz de inteiros, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 A expressão de consulta contém três cláusulas: `From`, `Where`, e `Select`. A função específica e a finalidade de cada cláusula de expressão de consulta é discutida em [Operações de consulta básica \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Para obter mais informações, consulte [Consultas](../../../../visual-basic/language-reference/queries/queries.md). Observe que, em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], uma definição de consulta geralmente é armazenada em uma variável e executada posteriormente. A consulta a variável, como `evensQuery` no exemplo anterior, deve ser um tipo que pode ser consultado. O tipo de `evensQuery` é `IEnumerable(Of Integer)`, atribuído pelo compilador usando inferência de tipo local.  
  
 É importante lembrar que a variável de consulta não faz nada e não retorna nenhum dado. Ela apenas armazena a definição de consulta. No exemplo anterior, ele é o `For Each` loop que executa a consulta.  
  
## Execução da Consulta  
 A execução da consulta é separada da criação da consulta. Criação de consulta define a consulta, mas a execução é disparada por um mecanismo diferente. Uma consulta pode ser executada assim que ela é definida \(*execução imediata*\), ou a definição pode ser armazenada e a consulta pode ser executada posteriormente \(*execução diferida*\).  
  
### Execução adiada  
 Um típico [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta semelhante no exemplo anterior, em que `evensQuery` é definido. Ele cria a consulta, mas não executá\-lo imediatamente. Em vez disso, a definição de consulta é armazenada na variável de consulta `evensQuery`. Executar a consulta posteriormente, normalmente usando um `For Each` loop, que retorna uma seqüência de valores, ou aplicando um operador de consulta padrão, como `Count` ou `Max`. Esse processo é conhecido como *execução diferida*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Uma sequência de valores, você deve acessar os dados recuperados usando a variável de iteração no `For Each` loop \(`number` no exemplo anterior\). Porque a variável de consulta, `evensQuery`, contém a definição de consulta, em vez dos resultados da consulta, você pode executar uma consulta sempre que desejar usando a variável de consulta mais de uma vez. Por exemplo, você pode ter um banco de dados em seu aplicativo que está sendo atualizado continuamente por um aplicativo separado. Depois de criar uma consulta que recupera dados do banco de dados, você pode usar um `For Each` loop para executar a consulta repetidamente, recuperar os dados mais recentes toda vez.  
  
 O exemplo a seguir demonstra como execução adiada funciona. Depois de `evensQuery2` é definido e executado com um `For Each` loop, como nos exemplos anteriores, alguns elementos da fonte de dados `numbers` são alteradas. Em seguida, um segundo `For Each` executa um loop `evensQuery2` novamente. Os resultados são diferentes na segunda vez, porque o `For Each` loop executa a consulta novamente, usando os novos valores no `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Saída:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### Execução imediata  
 Na execução adiada de consultas, a definição de consulta é armazenada em uma variável de consulta para execução posterior. Execução imediata, a consulta é executada no momento de sua definição. Execução é disparada quando você aplica um método que exige acesso aos elementos individuais do resultado da consulta. Execução imediata geralmente é forçada usando um dos operadores de consulta padrão que retornam valores únicos. Os exemplos são `Count`, `Max`, `Average`, e `First`. Esses operadores de consulta padrão execute a consulta assim que elas são aplicadas para calcular e retornar um resultado singleton. Para obter mais informações sobre operadores de consulta padrão que retornam valores únicos, consulte [Operações de agregação](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md), [Operações de elemento](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md), e [Operações de quantificador](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
 A consulta a seguir retorna uma contagem de números pares em uma matriz de inteiros. A definição de consulta não é salvo, e `numEvens` é uma simples `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Você pode obter o mesmo resultado usando o `Aggregate` método.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Você também pode forçar a execução de uma consulta chamando o `ToList` ou `ToArray` método em uma consulta \(imediata\) ou a variável de consulta \(diferido\), conforme mostrado no código a seguir.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Nos exemplos anteriores, `evensQuery3` é uma consulta de variável, mas `evensList` é uma lista e `evensArray` é uma matriz.  
  
 Usando `ToList` ou `ToArray` para forçar imediata execução é especialmente útil em cenários nos quais você deseja executar a consulta imediatamente e armazenar em cache os resultados em um único objeto de coleção. Para obter mais informações sobre esses métodos, consulte [Convertendo tipos de dados](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Você também pode causar uma consulta a ser executada usando um `IEnumerable` método como o <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> método.  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)