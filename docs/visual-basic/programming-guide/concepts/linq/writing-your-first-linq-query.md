---
title: Escrevendo a primeira consulta LINQ (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c16bb28189d5525654328da2dc80d868bbe61bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Escrevendo a primeira consulta LINQ (Visual Basic)
Uma *consulta* é uma expressão que recupera dados de uma fonte de dados. Consultas são expressos em uma linguagem de consulta dedicado. Ao longo do tempo, idiomas diferentes foram desenvolvidos para diferentes tipos de fontes de dados, por exemplo, SQL para bancos de dados relacionais e XQuery para XML. Isso é necessário para o desenvolvedor do aplicativo de aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que tem suporte.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]simplifica a situação, oferecendo um modelo consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você está sempre trabalhando com objetos. Use os mesmos padrões de codificação básicos para consultar e transformar dados em documentos XML, bancos de dados SQL, conjuntos de dados ADO.NET e entidades, coleções do .NET Framework e outras fonte ou formato para o qual um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedor está disponível. Este documento descreve as três fases da criação e uso de basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas.  
  
## <a name="three-stages-of-a-query-operation"></a>Três Estágios de uma Operação de Consulta  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]operações de consulta consistem em três ações:  
  
1.  Obter a fonte de dados ou fontes.  
  
2.  Criar a consulta.  
  
3.  Executar a consulta.  
  
 Em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a execução de uma consulta é diferente da criação da consulta. Você não recuperar os dados apenas criando uma consulta. Esse ponto é abordado com mais detalhes posteriormente neste tópico.  
  
 O exemplo a seguir ilustra as três partes de uma operação de consulta. O exemplo usa uma matriz de inteiros como uma fonte de dados conveniente para fins de demonstração. No entanto, os mesmos conceitos também se aplicam a outras fontes de dados.  
  
> [!NOTE]
>  Sobre o [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), certifique-se de que **Option infer** é definido como **em**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Saída:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>A Fonte de Dados  
 Como a fonte de dados no exemplo anterior é uma matriz, ele suporta implicitamente genérica <xref:System.Collections.Generic.IEnumerable%601> interface. É esse fato que permite que você use uma matriz como uma fonte de dados para um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta. Tipos que dão suporte a <xref:System.Collections.Generic.IEnumerable%601> ou uma interface derivada, como a genérica <xref:System.Linq.IQueryable%601>, são chamados *tipos passíveis de consulta*.  
  
 Como um tipo implicitamente passível de consulta, a matriz não requer modificação ou tratamento especial para servir como um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fonte de dados. O mesmo é verdadeiro para qualquer tipo de coleção que oferece suporte a <xref:System.Collections.Generic.IEnumerable%601>, incluindo genérica <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>e outras classes na biblioteca de classes do .NET Framework.  
  
 Se os dados de origem já não implementam <xref:System.Collections.Generic.IEnumerable%601>, um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedor é necessário para implementar a funcionalidade do *operadores de consulta padrão* para essa fonte de dados. Por exemplo, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] manipula o trabalho de carregamento de um documento XML em uma consulta <xref:System.Xml.Linq.XElement> tipo, conforme mostrado no exemplo a seguir. Para obter mais informações sobre operadores de consulta padrão, consulte [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Com [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], primeiro você cria um mapeamento relacional de objeto em tempo de design, manualmente ou usando o [LINQ to SQL Tools no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) no Visual Studio. Você escreve suas consultas aos objetos e o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] manipula a comunicação com o banco de dados em tempo de execução. No exemplo a seguir, `customers` representa uma tabela específica no banco de dados, e <xref:System.Data.Linq.Table%601> oferece suporte a genéricos <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Para obter mais informações sobre como criar tipos específicos de fontes de dados, consulte a documentação para os diversos provedores do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. (Para obter uma lista desses provedores, consulte [LINQ (consulta integrada à linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) A regra básica é simple: um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fonte de dados é qualquer objeto que oferece suporte o genéricos <xref:System.Collections.Generic.IEnumerable%601> interface ou uma interface que herda a partir dela.  
  
> [!NOTE]
>  Tipos, como <xref:System.Collections.ArrayList> que dão suporte a não genéricas <xref:System.Collections.IEnumerable> interface também pode ser usada como [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fontes de dados. Para obter um exemplo que usa um <xref:System.Collections.ArrayList>, consulte [como: consultar um ArrayList com LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>A Consulta  
 Na consulta, você deve especificar quais informações você deseja recuperar da fonte de dados ou fontes. Você também tem a opção de especificar como essas informações devem ser classificadas, agrupadas ou estruturadas antes de ser retornado. Para habilitar a criação da consulta, Visual Basic incorporou a nova sintaxe de consulta de linguagem.  
  
 Quando ele é executado, a consulta no exemplo a seguir retorna todos os números pares de uma matriz de inteiros, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 A expressão de consulta contém três cláusulas: `From`, `Where`, e `Select`. A função específica e a finalidade de cada cláusula de expressão de consulta é abordado em [operações básicas de consulta (Visual Basic)](basic-query-operations.md). Para obter mais informações, consulte [consultas](../../../../visual-basic/language-reference/queries/queries.md). Observe que em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], uma definição de consulta normalmente é armazenada em uma variável e executada mais tarde. A consulta a variável, como `evensQuery` no exemplo anterior, deve ser um tipo passível de consulta. O tipo de `evensQuery` é `IEnumerable(Of Integer)`, atribuído pelo compilador usando inferência de tipo local.  
  
 É importante lembrar que a variável de consulta em si não realiza nenhuma ação e não retorna nenhum dado. Ele apenas armazena a definição de consulta. No exemplo anterior, é o `For Each` loop que executa a consulta.  
  
## <a name="query-execution"></a>Execução da Consulta  
 A execução da consulta é separada da criação da consulta. Criação de consulta define a consulta, mas a execução é disparada por um mecanismo diferente. Uma consulta pode ser executada assim que ele é definido (*execução imediata*), ou a definição pode ser armazenada e a consulta pode ser executada mais tarde (*execução diferida*).  
  
### <a name="deferred-execution"></a>Execução Adiada  
 Um típico [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta semelhante no exemplo anterior, no qual `evensQuery` está definido. Ele cria a consulta, mas não executá-lo imediatamente. Em vez disso, a definição de consulta é armazenada na variável de consulta `evensQuery`. Execute a consulta posteriormente, normalmente usando um `For Each` loop, que retorna uma sequência de valores ou aplicando um operador de consulta padrão, como `Count` ou `Max`. Esse processo é conhecido como *execução diferida*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Uma sequência de valores, você deve acessar os dados recuperados usando a variável de iteração no `For Each` loop (`number` no exemplo anterior). Porque a variável de consulta, `evensQuery`, contém a definição de consulta, em vez dos resultados da consulta, você pode executar uma consulta sempre que desejar usando a variável de consulta mais de uma vez. Por exemplo, você pode ter um banco de dados em seu aplicativo que está sendo atualizado continuamente por um aplicativo separado. Depois de criar uma consulta que recupera dados do banco de dados, você pode usar um `For Each` loop para executar a consulta repetidamente, recuperar os dados mais recentes sempre.  
  
 O exemplo a seguir demonstra a execução adiada como funciona. Depois de `evensQuery2` é definido e executado com uma `For Each` loop, como nos exemplos anteriores, alguns elementos na fonte de dados `numbers` são alterados. Em seguida, um segundo `For Each` executa um loop `evensQuery2` novamente. Os resultados são diferentes na segunda vez, pois o `For Each` loop executa a consulta novamente, usando os novos valores no `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Saída:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Execução Imediata  
 Na execução adiada de consultas, a definição de consulta é armazenada em uma variável de consulta para execução posterior. Na execução imediata, a consulta é executada no momento da sua definição. A execução é disparada quando você aplicar um método que exige acesso aos elementos individuais do resultado da consulta. Execução imediata geralmente é forçada, usando um dos operadores de consulta padrão que retornam valores únicos. Os exemplos são `Count`, `Max`, `Average`, e `First`. Esses operadores de consulta padrão executar a consulta assim que elas são aplicadas para calcular e retornar um resultado singleton. Para obter mais informações sobre operadores de consulta padrão que retornam valores únicos, consulte [operações de agregação](aggregation-operations.md), [operações de elemento](element-operations.md), e [operações de quantificador](quantifier-operations.md).  
  
 A consulta a seguir retorna uma contagem de números pares em uma matriz de inteiros. A definição de consulta não é salvo, e `numEvens` é um simples `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Você pode obter o mesmo resultado usando o `Aggregate` método.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Você também pode forçar a execução de uma consulta chamando o `ToList` ou `ToArray` método em uma consulta (imediata) ou a variável de consulta (adiada), conforme mostrado no código a seguir.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Nos exemplos anteriores, `evensQuery3` é uma consulta de variável, mas `evensList` é uma lista e `evensArray` é uma matriz.  
  
 Usando `ToList` ou `ToArray` para forçar imediata a execução é especialmente útil em cenários em que você deseja executar a consulta imediatamente e armazenar em cache os resultados em um único objeto de coleção. Para obter mais informações sobre esses métodos, consulte [converter tipos de dados](converting-data-types.md).  
  
 Você também pode fazer uma consulta a ser executada usando um `IEnumerable` método, como o <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](getting-started-with-linq.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visão geral de operadores de consulta padrão (Visual Basic)](standard-query-operators-overview.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)
