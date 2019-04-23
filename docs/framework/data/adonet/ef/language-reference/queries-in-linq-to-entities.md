---
title: Consultas no LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 0e005939c8168606c7f58467f11115666cf1ef24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124730"
---
# <a name="queries-in-linq-to-entities"></a>Consultas no LINQ to Entities
Uma consulta é uma expressão que recupera dados de uma fonte de dados. Normalmente, as consultas são expressas em uma linguagem de consulta especializada, como o SQL para bancos de dados relacionais e o XQuery para XML. Portanto, os desenvolvedores precisaram aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que consultam. O LINQ (Consulta Integrada à Linguagem) oferece um modelo mais simples e consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em uma consulta LINQ, você sempre trabalha com objetos de programação.  
  
 Uma operação de consulta LINQ consiste em três ações: obter a fonte ou fontes de dados, criar a consulta e executá-la.  
  
 As fontes de dados que implementam a interface genérica <xref:System.Collections.Generic.IEnumerable%601> ou a interface genérica de <xref:System.Linq.IQueryable%601> podem ser consultadas por meio do LINQ. Instâncias de genéricos <xref:System.Data.Objects.ObjectQuery%601> classe, que implementa o genérico <xref:System.Linq.IQueryable%601> interface, servem como fonte de dados para [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consultas. A classe genérica <xref:System.Data.Objects.ObjectQuery%601> representa uma consulta que retorna uma coleção de zero ou mais objetos tipados. Você também pode permitir que o compilador inferir o tipo de uma entidade usando a palavra-chave c# `var` (Dim no Visual Basic).  
  
 Na consulta, você especifica exatamente as informações que deseja recuperar da fonte de dados. Uma consulta também pode especificar como essas informações devem ser classificadas, agrupadas e moldadas antes de serem retornadas. No LINQ, uma consulta é armazenada em uma variável. Se a consulta retornar uma sequência de valores, a própria variável da consulta deverá ser um tipo consultável. Essa variável de consulta não toma nenhuma ação e não retorna nenhum dado, ela apenas armazena as informações da consulta. Depois de criar uma consulta, você deve executá-la para recuperar todos os dados.  
  
## <a name="query-syntax"></a>Sintaxe de consulta  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consultas podem ser compostas de duas sintaxes diferentes: sintaxe de expressão consulta e sintaxe de consulta com base em método. Sintaxe de expressão de consulta é nova no c# 3.0 e no Visual Basic 9.0 e consiste em um conjunto de cláusulas escritas em uma sintaxe declarativa semelhante ao Transact-SQL ou XQuery. No entanto, o CLR (Common Language Runtime do [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] não pode ler a própria sintaxe de expressão de consulta. Portanto, em tempo de compilação, as expressões de consulta são convertidas em algo que o CLR não compreende: chamadas de método. Esses métodos são conhecidos como o *operadores de consulta padrão*. Como desenvolvedor, você tem a opção de chamá-los diretamente usando a sintaxe do método, em vez de usar a sintaxe de consulta. Para obter mais informações, consulte [Sintaxe de consulta e sintaxe de método em LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Sintaxe de expressão de consulta  
 As expressões de consulta são uma sintaxe declarativa de consulta. Essa sintaxe permite que um desenvolvedor escreva consultas em uma linguagem de alto nível que é formatada de maneira semelhante ao Transact-SQL. Usando a sintaxe de expressão de consulta, você pode executar até operações complexas de filtragem, ordenação e agrupamento em fontes de dados com o mínimo de código. Para obter mais informações, [operações básicas de consulta (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Consulte os tópicos a seguir, para obter exemplos que demonstram como usar a sintaxe de expressão de consulta:  
  
-   [Exemplos de sintaxe de expressão de consulta: Projection](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: Filtragem](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: Ordenação](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: Operadores de agregação](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: O particionamento](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: Operadores de junção](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: Operadores de elemento](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: agrupamento](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Exemplos de sintaxe de expressão de consulta: Navegando em relações](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Sintaxe de pesquisa baseada em método  
 Outra maneira de compor consultas [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] é usar consultas baseadas em método. A sintaxe de consulta com base em método é uma sequência de chamadas de método direto para os métodos de operadores LINQ, passando expressões lambda como parâmetros. Para obter mais informações, consulte [Expressões Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Para obter exemplos que demonstram como usar a sintaxe baseada em método, consulte os seguintes tópicos:  
  
-   [Exemplos de sintaxe de consulta com base em método: Projection](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Filtragem](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Ordenação](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Operadores de agregação](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: O particionamento](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Conversão](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Operadores de junção](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Operadores de elemento](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: agrupamento](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [Exemplos de sintaxe de consulta com base em método: Navegando em relações](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Consulte também

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Introdução a LINQ em C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Introdução ao LINQ no Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Opções de mesclagem do Entity Framework e consultas compiladas](https://go.microsoft.com/fwlink/?LinkId=199591)
