---
title: "Como usar árvores de expressão para compilar consultas dinâmicas (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7de999848870de80996f308affde088088e32e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Como usar árvores de expressão para compilar consultas dinâmicas (C#)
No LINQ, as árvores de expressão são usadas para representar consultas estruturadas que se destinam a fontes de dados que implementam <xref:System.Linq.IQueryable%601>. Por exemplo, o provedor LINQ implementa a interface <xref:System.Linq.IQueryable%601> para consultar repositórios de dados relacionais. O compilador do C# compila as consultas que se destinam a essas fontes de dados, no código que cria uma árvore de expressão em tempo de execução. O provedor de consultas pode percorrer a estrutura de dados da árvore de expressão e convertê-la em uma linguagem de consulta apropriada para a fonte de dados.  
  
 As árvores de expressão também são usadas no LINQ para representar expressões lambda que são atribuídas a variáveis do tipo <xref:System.Linq.Expressions.Expression%601>.  
  
 Este tópico descreve como usar árvores de expressão para criar consultas LINQ dinâmicas. As consultas dinâmicas são úteis quando as especificações de uma consulta não são conhecidas em tempo de compilação. Por exemplo, um aplicativo pode fornecer uma interface do usuário que permite ao usuário final especificar um ou mais predicados para filtrar os dados. Para usar a LINQ para a consulta, esse tipo de aplicativo deve usar árvores de expressão para criar a consulta LINQ em tempo de execução.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar árvores de expressão para construir uma consulta em uma fonte de dados `IQueryable` e, em seguida, executá-la. O código compila uma árvore de expressão para representar a consulta a seguir:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Os métodos de fábrica no namespace <xref:System.Linq.Expressions> são usados para criar árvores de expressão que representam as expressões que compõem a consulta geral. As expressões que representam as chamadas aos métodos do operador de consulta padrão, referem-se às implementações <xref:System.Linq.Queryable> dos métodos a seguir. A árvore de expressão final é passada para a implementação <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> do provedor da fonte de dados `IQueryable`, para criar uma consulta executável do tipo `IQueryable`. Os resultados são obtidos ao enumerar essa variável de consulta.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Esse código usa um número fixo de expressões no predicado que é passado para o método `Queryable.Where`. No entanto, você pode escrever um aplicativo que combina um número variável de expressões de predicado que dependam da entrada do usuário. Você também pode variar os operadores de consulta padrão que são chamados na consulta, dependendo da entrada do usuário.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Crie um novo projeto de **Aplicativo de Console**.  
  
-   Adicione uma referência à System.Core.dll, se ainda não foi referenciada.  
  
-   Inclua o namespace System.Linq.Expressions.  
  
-   Copie o código do exemplo e cole-o no método `Main`.  
  
## <a name="see-also"></a>Consulte também  
 [Árvores de expressão (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [Como executar árvores de expressão (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [Como especificar filtros predicados dinamicamente em tempo de execução](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
