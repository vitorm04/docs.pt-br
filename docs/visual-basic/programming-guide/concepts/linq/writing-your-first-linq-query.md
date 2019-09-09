---
title: Escrevendo a primeira consulta LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952005"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Escrevendo a primeira consulta LINQ (Visual Basic)
Uma *consulta* é uma expressão que recupera dados de uma fonte de dados. As consultas são expressas em uma linguagem de consulta dedicada. Ao longo do tempo, diferentes idiomas foram desenvolvidos para diferentes tipos de fontes de dados, por exemplo, SQL para bancos de dados relacionais e XQuery for XML. Isso torna necessário que o desenvolvedor do aplicativo aprenda uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados com suporte.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]simplifica a situação oferecendo um modelo consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você está sempre trabalhando com objetos. Você usa os mesmos padrões básicos de codificação para consultar e transformar dados em documentos XML, bancos de dados SQL, conjuntos de ADO.net e entidades, .NET Framework coleções e qualquer outra fonte ou formato para o qual [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] um provedor está disponível. Este documento descreve as três fases da criação e do uso de consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] básicas.  
  
## <a name="three-stages-of-a-query-operation"></a>Três Estágios de uma Operação de Consulta  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]as operações de consulta consistem em três ações:  
  
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
 Como a fonte de dados no exemplo anterior é uma matriz, ela dá suporte implicitamente à <xref:System.Collections.Generic.IEnumerable%601> interface genérica. É esse fato que permite que você use uma matriz como uma fonte de dados para uma [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta. Tipos que dão suporte a <xref:System.Collections.Generic.IEnumerable%601> ou uma interface derivada, como a genérica <xref:System.Linq.IQueryable%601>, são chamados *tipos passíveis de consulta*.  
  
 Como um tipo implicitamente consultável, a matriz não requer nenhuma modificação ou tratamento especial para servir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] como uma fonte de dados. O mesmo é verdadeiro para qualquer tipo de coleção com <xref:System.Collections.Generic.IEnumerable%601>suporte, incluindo as <xref:System.Collections.Generic.List%601>classes <xref:System.Collections.Generic.Dictionary%602>genéricas, e outras no .NET Framework biblioteca de classes.  
  
 Se os dados de origem ainda não forem <xref:System.Collections.Generic.IEnumerable%601>implementados [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , um provedor será necessário para implementar a funcionalidade dos *operadores de consulta padrão* para essa fonte de dados. Por exemplo, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] trata o trabalho de carregar um documento XML em um tipo <xref:System.Xml.Linq.XElement> passível de consulta, conforme mostrado no exemplo a seguir. Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral dos operadores de consulta padrão (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Com [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]o, você primeiro cria um mapeamento relacional de objeto no tempo de design, seja manualmente ou usando as [ferramentas de LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) no Visual Studio. Você escreve suas consultas aos objetos e o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] manipula a comunicação com o banco de dados em tempo de execução. No exemplo a seguir, `customers` representa uma tabela específica no banco de dados e <xref:System.Data.Linq.Table%601> dá suporte <xref:System.Linq.IQueryable%601>a Generic.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Para obter mais informações sobre como criar tipos específicos de fontes de dados, consulte a documentação para os diversos provedores do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. (Para obter uma lista desses provedores, consulte [LINQ (consulta integrada à linguagem)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) A regra básica é simples: uma [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fonte de dados é qualquer objeto que dê suporte <xref:System.Collections.Generic.IEnumerable%601> à interface genérica ou uma interface herdada dela.  
  
> [!NOTE]
> Tipos como <xref:System.Collections.ArrayList> o que dão suporte à interface não <xref:System.Collections.IEnumerable> genérica também podem ser usados como [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fontes de dados. Para obter um exemplo que usa <xref:System.Collections.ArrayList>um, [consulte Como: Consulte uma ArrayList com LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>A Consulta  
 Na consulta, você especifica quais informações deseja recuperar da fonte de dados ou das fontes. Você também tem a opção de especificar como essas informações devem ser classificadas, agrupadas ou estruturadas antes de serem retornadas. Para habilitar a criação de consultas, Visual Basic incorporou uma nova sintaxe de consulta à linguagem.  
  
 Quando é executado, a consulta no exemplo a seguir retorna todos os números pares de uma matriz de inteiros, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 A expressão de consulta contém três cláusulas `From`: `Where`, e `Select`. A função específica e a finalidade de cada cláusula de expressão de consulta são discutidas em [operações de consulta básica (Visual Basic)](basic-query-operations.md). Para obter mais informações, consulte [consultas](../../../../visual-basic/language-reference/queries/index.md). Observe que no [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], uma definição de consulta geralmente é armazenada em uma variável e executada mais tarde. A variável de consulta, `evensQuery` como no exemplo anterior, deve ser um tipo consultável. O tipo de `evensQuery` é `IEnumerable(Of Integer)`, atribuído pelo compilador usando inferência de tipo local.  
  
 É importante lembrar que a variável de consulta não executa nenhuma ação e não retorna nenhum dado. Ele armazena apenas a definição de consulta. No exemplo anterior, é o `For Each` loop que executa a consulta.  
  
## <a name="query-execution"></a>Execução da Consulta  
 A execução da consulta é separada da criação da consulta. A criação de consulta define a consulta, mas a execução é disparada por um mecanismo diferente. Uma consulta pode ser executada assim que é definida (*execução imediata*) ou a definição pode ser armazenada e a consulta pode ser executada mais tarde (*execução adiada*).  
  
### <a name="deferred-execution"></a>Execução Adiada  
 Uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] típica é semelhante à do exemplo anterior, em que `evensQuery` é definida. Ele cria a consulta, mas não a executa imediatamente. Em vez disso, a definição de consulta é armazenada `evensQuery`na variável de consulta. Você executa a consulta mais tarde, normalmente usando um `For Each` loop, que retorna uma sequência de valores ou aplicando um operador de consulta padrão, `Count` como ou `Max`. Esse processo é conhecido como *execução adiada*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Para uma sequência de valores, você acessa os dados recuperados usando a variável de iteração `For Each` no loop`number` (no exemplo anterior). Como a variável de consulta `evensQuery`,, mantém a definição de consulta em vez dos resultados da consulta, você pode executar uma consulta sempre que desejar usando a variável de consulta mais de uma vez. Por exemplo, você pode ter um banco de dados em seu aplicativo que está sendo atualizado continuamente por um aplicativo separado. Depois de criar uma consulta que recupere os dados desse banco, você pode usar um `For Each` loop para executar a consulta repetidamente, recuperando os dados mais recentes a cada vez.  
  
 O exemplo a seguir demonstra como funciona a execução retardada. Depois `evensQuery2` que é definido e executado com `For Each` um loop, como nos exemplos anteriores, alguns elementos na fonte `numbers` de dados são alterados. Em seguida, `For Each` um segundo `evensQuery2` loop é executado novamente. Os resultados são diferentes na segunda vez, porque o `For Each` loop executa a consulta novamente, usando os novos valores em. `numbers`  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Saída:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Execução Imediata  
 Na execução adiada de consultas, a definição de consulta é armazenada em uma variável de consulta para execução posterior. Na execução imediata, a consulta é executada no momento da definição. A execução é disparada quando você aplica um método que requer acesso a elementos individuais do resultado da consulta. A execução imediata geralmente é forçada usando um dos operadores de consulta padrão que retornam valores únicos. Os exemplos `Count`são `Max` ,`Average`, e `First`. Esses operadores de consulta padrão executam a consulta assim que são aplicados para calcular e retornar um resultado singleton. Para obter mais informações sobre operadores de consulta padrão que retornam valores únicos, consulte operações de [agregação](aggregation-operations.md), [operações de elemento](element-operations.md)e [operações de quantificador](quantifier-operations.md).  
  
 A consulta a seguir retorna uma contagem dos números pares em uma matriz de inteiros. A definição de consulta não é salva e `numEvens` é simples. `Integer`  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Você pode obter o mesmo resultado usando o `Aggregate` método.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Você também pode forçar a execução de uma consulta chamando o `ToList` método `ToArray` ou em uma consulta (imediata) ou variável de consulta (adiada), conforme mostrado no código a seguir.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 Nos exemplos anteriores, `evensQuery3` é uma variável de consulta, mas `evensList` é uma lista e `evensArray` é uma matriz.  
  
 Usar `ToList` ou`ToArray` para forçar a execução imediata é especialmente útil em cenários nos quais você deseja executar a consulta imediatamente e armazenar em cache os resultados em um único objeto de coleção. Para obter mais informações sobre esses métodos, consulte [convertendo tipos de dados](converting-data-types.md).  
  
 Você também pode fazer com que uma consulta seja executada usando um `IEnumerable` método como o <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> método.  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](getting-started-with-linq.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visão geral de operadores de consulta padrão (Visual Basic)](standard-query-operators-overview.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
