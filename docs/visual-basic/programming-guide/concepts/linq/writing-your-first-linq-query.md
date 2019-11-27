---
title: Escrevendo a primeira consulta LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: a9fe4241972815a04ec9c6a51a45760d72a8bbb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349341"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Escrevendo a primeira consulta LINQ (Visual Basic)
Uma *consulta* é uma expressão que recupera dados de uma fonte de dados. As consultas são expressas em uma linguagem de consulta dedicada. Ao longo do tempo, diferentes idiomas foram desenvolvidos para diferentes tipos de fontes de dados, por exemplo, SQL para bancos de dados relacionais e XQuery for XML. Isso torna necessário que o desenvolvedor do aplicativo aprenda uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados com suporte.  
  
 o [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] simplifica a situação oferecendo um modelo consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você está sempre trabalhando com objetos. Você usa os mesmos padrões básicos de codificação para consultar e transformar dados em documentos XML, bancos de dados SQL, conjuntos de ADO.NET e entidades, .NET Framework coleções e qualquer outra fonte ou formato para o qual um provedor de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] está disponível. Este documento descreve as três fases da criação e do uso de consultas de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] básicas.  
  
## <a name="three-stages-of-a-query-operation"></a>Três Estágios de uma Operação de Consulta  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operações de consulta consistem em três ações:  
  
1. Obtenha a fonte de dados ou as fontes.  
  
2. Criar a consulta.  
  
3. Executar a consulta.  
  
 No [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a execução de uma consulta é distinta da criação da consulta. Você não recupera dados apenas criando uma consulta. Esse ponto é abordado com mais detalhes posteriormente neste tópico.  
  
 O exemplo a seguir ilustra as três partes de uma operação de consulta. O exemplo usa uma matriz de inteiros como uma fonte de dados conveniente para fins de demonstração. No entanto, os mesmos conceitos também se aplicam a outras fontes de dados.  
  
> [!NOTE]
> Na [página compilar, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), verifique se **Option Infer** está definida como **on**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Saída:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>A Fonte de Dados  
 Como a fonte de dados no exemplo anterior é uma matriz, ela dá suporte implicitamente à interface de <xref:System.Collections.Generic.IEnumerable%601> genérica. É esse fato que permite que você use uma matriz como uma fonte de dados para uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Tipos que dão suporte a <xref:System.Collections.Generic.IEnumerable%601> ou uma interface derivada, como a genérica <xref:System.Linq.IQueryable%601>, são chamados *tipos passíveis de consulta*.  
  
 Como um tipo implicitamente consultável, a matriz não requer nenhuma modificação ou tratamento especial para servir como uma fonte de dados [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. O mesmo é verdadeiro para qualquer tipo de coleção que dê suporte a <xref:System.Collections.Generic.IEnumerable%601>, incluindo o <xref:System.Collections.Generic.List%601>genérico, <xref:System.Collections.Generic.Dictionary%602>e outras classes na biblioteca de classes .NET Framework.  
  
 Se os dados de origem ainda não implementarem <xref:System.Collections.Generic.IEnumerable%601>, um provedor de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] será necessário para implementar a funcionalidade dos *operadores de consulta padrão* para essa fonte de dados. Por exemplo, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] trata o trabalho de carregar um documento XML em um tipo de <xref:System.Xml.Linq.XElement> passível de consulta, conforme mostrado no exemplo a seguir. Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral dos operadores de consulta padrão (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Com [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], primeiro você cria um mapeamento relacional de objeto no tempo de design, seja manualmente ou usando as [ferramentas de LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) no Visual Studio. Você escreve suas consultas aos objetos e o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] manipula a comunicação com o banco de dados em tempo de execução. No exemplo a seguir, `customers` representa uma tabela específica no banco de dados e <xref:System.Data.Linq.Table%601> dá suporte a <xref:System.Linq.IQueryable%601>genérico.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Para obter mais informações sobre como criar tipos específicos de fontes de dados, consulte a documentação para os diversos provedores do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. (Para obter uma lista desses provedores, consulte [LINQ (consulta integrada à linguagem)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) A regra básica é simples: uma [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fonte de dados é qualquer objeto que dê suporte à interface genérica <xref:System.Collections.Generic.IEnumerable%601> ou uma interface que herde dela.  
  
> [!NOTE]
> Tipos como <xref:System.Collections.ArrayList> que dão suporte à interface não genérica <xref:System.Collections.IEnumerable> também podem ser usados como [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fontes de dados. Para obter um exemplo que usa um <xref:System.Collections.ArrayList>, consulte [como consultar um ArrayList com LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>A Consulta  
 Na consulta, você especifica quais informações deseja recuperar da fonte de dados ou das fontes. Você também tem a opção de especificar como essas informações devem ser classificadas, agrupadas ou estruturadas antes de serem retornadas. Para habilitar a criação de consultas, Visual Basic incorporou uma nova sintaxe de consulta à linguagem.  
  
 Quando é executado, a consulta no exemplo a seguir retorna todos os números pares de uma matriz de inteiros, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 A expressão de consulta contém três cláusulas: `From`, `Where`e `Select`. A função específica e a finalidade de cada cláusula de expressão de consulta são discutidas em [operações de consulta básica (Visual Basic)](basic-query-operations.md). Para obter mais informações, consulte [consultas](../../../../visual-basic/language-reference/queries/index.md). Observe que em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], uma definição de consulta geralmente é armazenada em uma variável e executada mais tarde. A variável de consulta, como `evensQuery` no exemplo anterior, deve ser um tipo consultável. O tipo de `evensQuery` é `IEnumerable(Of Integer)`, atribuído pelo compilador usando inferência de tipo local.  
  
 É importante lembrar que a variável de consulta não executa nenhuma ação e não retorna nenhum dado. Ele armazena apenas a definição de consulta. No exemplo anterior, é o loop de `For Each` que executa a consulta.  
  
## <a name="query-execution"></a>Execução da Consulta  
 A execução da consulta é separada da criação da consulta. A criação de consulta define a consulta, mas a execução é disparada por um mecanismo diferente. Uma consulta pode ser executada assim que é definida (*execução imediata*) ou a definição pode ser armazenada e a consulta pode ser executada mais tarde (*execução adiada*).  
  
### <a name="deferred-execution"></a>Execução Adiada  
 Uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] típica é semelhante à do exemplo anterior, na qual `evensQuery` está definida. Ele cria a consulta, mas não a executa imediatamente. Em vez disso, a definição de consulta é armazenada na variável de consulta `evensQuery`. Você executa a consulta mais tarde, normalmente usando um loop `For Each`, que retorna uma sequência de valores ou aplicando um operador de consulta padrão, como `Count` ou `Max`. Esse processo é conhecido como *execução adiada*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Para uma sequência de valores, você acessa os dados recuperados usando a variável de iteração no loop de `For Each` (`number` no exemplo anterior). Como a variável de consulta, `evensQuery`, mantém a definição de consulta em vez dos resultados da consulta, você pode executar uma consulta sempre que desejar usando a variável de consulta mais de uma vez. Por exemplo, você pode ter um banco de dados em seu aplicativo que está sendo atualizado continuamente por um aplicativo separado. Depois de criar uma consulta que recupere os dados desse banco, você pode usar um loop de `For Each` para executar a consulta repetidamente, recuperando os dados mais recentes a cada vez.  
  
 O exemplo a seguir demonstra como funciona a execução retardada. Depois que `evensQuery2` é definido e executado com um loop de `For Each`, como nos exemplos anteriores, alguns elementos na fonte de dados `numbers` são alterados. Em seguida, um segundo loop de `For Each` é executado `evensQuery2` novamente. Os resultados são diferentes na segunda vez, porque o loop de `For Each` executa a consulta novamente, usando os novos valores em `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Saída:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Execução Imediata  
 Na execução adiada de consultas, a definição de consulta é armazenada em uma variável de consulta para execução posterior. Na execução imediata, a consulta é executada no momento da definição. A execução é disparada quando você aplica um método que requer acesso a elementos individuais do resultado da consulta. A execução imediata geralmente é forçada usando um dos operadores de consulta padrão que retornam valores únicos. Os exemplos são `Count`, `Max`, `Average`e `First`. Esses operadores de consulta padrão executam a consulta assim que são aplicados para calcular e retornar um resultado singleton. Para obter mais informações sobre operadores de consulta padrão que retornam valores únicos, consulte operações de [agregação](aggregation-operations.md), [operações de elemento](element-operations.md)e [operações de quantificador](quantifier-operations.md).  
  
 A consulta a seguir retorna uma contagem dos números pares em uma matriz de inteiros. A definição de consulta não é salva e `numEvens` é uma `Integer`simples.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Você pode obter o mesmo resultado usando o método `Aggregate`.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Você também pode forçar a execução de uma consulta chamando o método `ToList` ou `ToArray` em uma consulta (imediata) ou variável de consulta (adiado), conforme mostrado no código a seguir.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 Nos exemplos anteriores, `evensQuery3` é uma variável de consulta, mas `evensList` é uma lista e `evensArray` é uma matriz.  
  
 Usar `ToList` ou `ToArray` para forçar a execução imediata é especialmente útil em cenários nos quais você deseja executar a consulta imediatamente e armazenar em cache os resultados em um único objeto de coleção. Para obter mais informações sobre esses métodos, consulte [convertendo tipos de dados](converting-data-types.md).  
  
 Você também pode fazer com que uma consulta seja executada usando um método `IEnumerable`, como o método <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>.  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](getting-started-with-linq.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visão geral de operadores de consulta padrão (Visual Basic)](standard-query-operators-overview.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
