---
title: Consultas no LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 52f48fcacd6fbd92e4fd0531c5e1fa3577496941
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738474"
---
# <a name="queries-in-linq-to-entities"></a>Consultas no LINQ to Entities
Uma consulta é uma expressão que recupera dados de uma fonte de dados. Normalmente, as consultas são expressas em uma linguagem de consulta especializada, como o SQL para bancos de dados relacionais e o XQuery para XML. Portanto, os desenvolvedores precisaram aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que consultam. O LINQ (Consulta Integrada à Linguagem) oferece um modelo mais simples e consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em uma consulta LINQ, você sempre trabalha com objetos de programação.  
  
 Uma operação de consulta LINQ consiste em três ações: obter a fonte ou fontes de dados, criar a consulta e executá-la.  
  
 As fontes de dados que implementam a interface genérica <xref:System.Collections.Generic.IEnumerable%601> ou a interface genérica de <xref:System.Linq.IQueryable%601> podem ser consultadas por meio do LINQ. Instâncias da classe <xref:System.Data.Objects.ObjectQuery%601> genérica, que implementa a interface genérica <xref:System.Linq.IQueryable%601>, servem como a fonte de dados para consultas de LINQ to Entities. A classe genérica <xref:System.Data.Objects.ObjectQuery%601> representa uma consulta que retorna uma coleção de zero ou mais objetos tipados. Você também pode deixar o compilador inferir o tipo de uma entidade usando a C# palavra-chave `var` (Dim in Visual Basic).  
  
 Na consulta, você especifica exatamente as informações que deseja recuperar da fonte de dados. Uma consulta também pode especificar como essas informações devem ser classificadas, agrupadas e moldadas antes de serem retornadas. No LINQ, uma consulta é armazenada em uma variável. Se a consulta retornar uma sequência de valores, a própria variável da consulta deverá ser um tipo consultável. Essa variável de consulta não toma nenhuma ação e não retorna nenhum dado, ela apenas armazena as informações da consulta. Depois de criar uma consulta, você deve executá-la para recuperar todos os dados.  
  
## <a name="query-syntax"></a>Sintaxe de consulta  
 As consultas LINQ to Entities podem ser compostas de duas sintaxes diferentes: sintaxe de expressão de consulta e sintaxe de consulta baseada em método. A sintaxe de expressão de consulta C# é nova no 3,0 e Visual Basic 9,0, e consiste em um conjunto de cláusulas escritas em uma sintaxe declarativa semelhante a TRANSACT-SQL ou XQuery. No entanto, o Common Language Runtime de .NET Framework (CLR) não pode ler a própria sintaxe de expressão de consulta. Portanto, em tempo de compilação, as expressões de consulta são convertidas em algo que o CLR não compreende: chamadas de método. Esses métodos são conhecidos como *operadores de consulta padrão*. Como desenvolvedor, você tem a opção de chamá-los diretamente usando a sintaxe do método, em vez de usar a sintaxe de consulta. Para obter mais informações, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Sintaxe de expressão de consulta  
 As expressões de consulta são uma sintaxe declarativa de consulta. Essa sintaxe permite que um desenvolvedor escreva consultas em uma linguagem de alto nível que é formatada de maneira semelhante ao Transact-SQL. Usando a sintaxe de expressão de consulta, você pode executar até operações complexas de filtragem, ordenação e agrupamento em fontes de dados com o mínimo de código. Para obter mais informações, [consulte as operações básicas de consulta (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Consulte os tópicos a seguir, para obter exemplos que demonstram como usar a sintaxe de expressão de consulta:  
  
- [Exemplos de sintaxe de expressão de consulta: projeção](query-expression-syntax-examples-projection.md)  
  
- [Exemplos de sintaxe de expressão de consulta: filtragem](query-expression-syntax-examples-filtering.md)  
  
- [Exemplos de sintaxe de expressão de consulta: classificação](query-expression-syntax-examples-ordering.md)  
  
- [Exemplos de sintaxe de expressão de consulta: operadores de agregação](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Exemplos de sintaxe de expressão de consulta: particionamento](query-expression-syntax-examples-partitioning.md)  
  
- [Exemplos de sintaxe de expressão de consulta: operadores de junção](query-expression-syntax-examples-join-operators.md)  
  
- [Exemplos de sintaxe de expressão de consulta: operadores de elemento](query-expression-syntax-examples-element-operators.md)  
  
- [Exemplos de sintaxe de expressão de consulta: agrupamento](query-expression-syntax-examples-grouping.md)  
  
- [Exemplos de sintaxe de expressão de consulta: navegar em relações](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Sintaxe de pesquisa baseada em método  
 Outra maneira de compor LINQ to Entities consultas é usando consultas baseadas em método. A sintaxe de consulta baseada em método é uma sequência de chamadas de método diretas para métodos de operador LINQ, passando expressões lambda como parâmetros. Para obter mais informações, consulte [Expressões Lambda](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Para obter exemplos que demonstram como usar a sintaxe baseada em método, consulte os seguintes tópicos:  
  
- [Exemplos de sintaxe de consulta baseada em método: projeção](method-based-query-syntax-examples-projection.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: filtragem](method-based-query-syntax-examples-filtering.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: ordenação](method-based-query-syntax-examples-ordering.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: operadores de agregação](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: particionamento](method-based-query-syntax-examples-partitioning.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: conversão](method-based-query-syntax-examples-conversion.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: operadores de junção](method-based-query-syntax-examples-join-operators.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: operadores de elemento](method-based-query-syntax-examples-element-operators.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: agrupamento](method-based-query-syntax-examples-grouping.md)  
  
- [Exemplos de sintaxe de consulta baseada em método: navegar em relações](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Consulte também

- [LINQ to Entities](linq-to-entities.md)
- [Introdução a LINQ em C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Introdução ao LINQ no Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Opções de mesclagem Entity Framework e consultas compiladas](https://go.microsoft.com/fwlink/?LinkId=199591)
