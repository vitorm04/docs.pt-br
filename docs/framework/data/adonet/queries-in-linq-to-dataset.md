---
title: Consultas no LINQ to DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: da9e5bd39cebce27dbaf89ac020c2bf8f154adcc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211834"
---
# <a name="queries-in-linq-to-dataset"></a>Consultas no LINQ to DataSet
Uma consulta é uma expressão que recupera dados de uma fonte de dados. Normalmente, as consultas são expressas em uma linguagem de consulta especializada, como o SQL para bancos de dados relacionais e o XQuery para XML. Portanto, os desenvolvedores precisaram aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que consultam. O [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] oferece um modelo mais simples e consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em uma consulta [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], você sempre trabalha com objetos de programação.  
  
 Uma operação de consulta [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consiste em três ações: obter a fonte ou fontes de dados, criar a consulta e executá-la.  
  
 As fontes de dados que implementam a interface genérica <xref:System.Collections.Generic.IEnumerable%601> podem ser consultadas por meio do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Chamando <xref:System.Data.DataTableExtensions.AsEnumerable%2A> em um <xref:System.Data.DataTable> retorna um objeto que implementa a <xref:System.Collections.Generic.IEnumerable%601> interface, que serve como fonte de dados para [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas.  
  
 Na consulta, você especifica exatamente as informações que deseja recuperar da fonte de dados. Uma consulta também pode especificar como essas informações devem ser classificadas, agrupadas e moldadas antes de serem retornadas. No [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], uma consulta é armazenada em uma variável. Se a consulta foi projetada para retornar uma sequência de valores, a variável de consulta deve ser um tipo enumerável. Essa variável de consulta não toma nenhuma ação e não retorna nenhum dado, ela apenas armazena as informações da consulta. Depois de criar uma consulta, você deve executá-la para recuperar todos os dados.  
  
 Em uma consulta, que retorna uma sequência de valores, a variável de consulta nunca contém os resultados da consulta e armazena somente os comandos da consulta. A execução da consulta é adiada até que a variável da consulta seja iterada em um loop `foreach` ou `For Each`. Isso é chamado *execução adiada*; ou seja, execução da consulta ocorre algum tempo depois que a consulta é construída. Isso significa que você pode executar uma consulta com a frequência que desejar. Isso é útil quando, por exemplo, você tem um banco de dados que está sendo atualizado por outros aplicativos. Em seu aplicativo, você pode criar uma consulta para recuperar as informações mais recentes e executar a consulta repetidamente, retornando informações atualizadas sempre.  
  
 Em comparação com as consultas adiadas, que retornam uma sequência de valores, as consultas que retornam um valor singleton são executadas imediatamente. Alguns exemplos de consultas singleton são <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A> e <xref:System.Linq.Enumerable.First%2A>. Essas consultas são executadas imediatamente porque os resultados da consulta são necessários para calcular o resultado singleton. Por exemplo, para localizar a média dos resultados da consulta, a consulta deve ser executada para que a função de média tenha os dados de entrada com os quais trabalhar. Você também pode usar o método <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A> em uma consulta para forçar a execução imediata de uma consulta que não produz um valor singleton. Essas técnicas para forçar a execução imediata podem ser úteis quando você deseja armazenar os resultados de uma consulta em cache. Para obter mais informações sobre a execução de consultas adiadas e imediatas, consulte [Introdução ao LINQ](https://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).  
  
## <a name="queries"></a>Consultas  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] as consultas podem ser formuladas em duas sintaxes diferentes: sintaxe de expressão consulta e sintaxe de consulta com base em método.  
  
### <a name="query-expression-syntax"></a>Sintaxe de expressão de consulta  
 As expressões de consulta são uma sintaxe declarativa de consulta. Essa sintaxe permite que um desenvolvedor escreva consultas no C# ou no Visual Basic em um formato semelhante ao SQL. Usando a sintaxe de expressão de consulta, você pode executar até operações complexas de filtragem, ordenação e agrupamento em fontes de dados com o mínimo de código. Para obter mais informações, consulte [expressões de consulta LINQ](https://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) e [operações básicas de consulta (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 A sintaxe de expressão de consulta é nova no C# 3.0 e no [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)]. No entanto, o CLR (Common Language Runtime do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] não pode ler a própria sintaxe de expressão de consulta. Portanto, em tempo de compilação, as expressões de consulta são convertidas em algo que o CLR não compreende: chamadas de método. Esses métodos são chamados da *operadores de consulta padrão*. Como desenvolvedor, você tem a opção de chamá-los diretamente usando a sintaxe do método, em vez de usar a sintaxe de consulta. Para obter mais informações, consulte [Sintaxe de consulta e sintaxe de método em LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Para obter mais informações sobre os operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 O exemplo a seguir usa <xref:System.Linq.Enumerable.Select%2A> para retornar todas as linhas da tabela `Product` e exibir os nomes dos produtos.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Sintaxe de pesquisa baseada em método  
 A outra maneira de formular consultas [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] é usar consultas baseadas em método. A sintaxe de consulta baseada em método é uma sequência de chamadas diretas de método para métodos de operadores [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], passando expressões lambda como parâmetros. Para obter mais informações, consulte [Expressões Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Este exemplo usa <xref:System.Linq.Enumerable.Select%2A> para retornar todas as linhas da tabela `Product` e exibir os nomes dos produtos.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Compondo consultas  
 Como mencionado anteriormente neste tópico, a própria variável de consulta armazena somente os comandos de consulta quando a consulta é criada para retornar uma sequência de valores. Se a consulta não contiver um método que provoque execução imediata, a execução atual da consulta é adiada até que você itere sobre a variável de consulta em um loop `foreach` ou `For Each`. A execução adiada permite que várias consultas sejam combinadas ou que uma consulta seja estendida. Quando é estendida, a consulta é modificada para incluir as novas operações, e a execução eventual refletirá as alterações. No exemplo a seguir, a primeira consulta retorna todos os produtos. A segunda consulta estende a primeira usando `Where` para retornar todos os produtos de tamanho “L”:  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Depois que uma consulta foi executada, nenhuma consulta adicional pode ser composta, e todas as consultas subsequentes usarão os operadores do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] na memória. Execução da consulta ocorrerá quando você iterar sobre a variável de consulta em uma `foreach` ou `For Each` instrução, ou por uma chamada para uma da [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operadores de conversão que provocam a execução imediata. Esses operadores incluem: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A> e <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 No exemplo a seguir, a primeira consulta retorna todos os produtos ordenados pelo preço de lista. O método <xref:System.Linq.Enumerable.ToArray%2A> é usado para forçar a execução imediata da consulta:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [Consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Introdução a LINQ em C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Introdução ao LINQ no Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
