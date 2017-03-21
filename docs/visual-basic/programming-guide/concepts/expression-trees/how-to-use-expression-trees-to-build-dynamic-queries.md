---
title: "Como: usar árvores de expressão para compilar consultas dinâmicas (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Como: usar árvores de expressão para compilar consultas dinâmicas (Visual Basic)
Em LINQ, árvores de expressão são usados para representar consultas estruturadas que fontes de destino de dados que implementam <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> Por exemplo, o provedor LINQ implementa o <xref:System.Linq.IQueryable%601>interface para consultar armazenamentos de dados relacionais.</xref:System.Linq.IQueryable%601> O compilador do Visual Basic compila as consultas que essas fontes de dados de destino no código que cria uma árvore de expressão em tempo de execução. O provedor de consultas pode percorrer a estrutura de dados de árvore de expressão e convertê-la em uma linguagem de consulta apropriada para a fonte de dados.  
  
 Árvores de expressão também são usados em LINQ para representar as expressões lambda são atribuídas a variáveis do tipo <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601>  
  
 Este tópico descreve como usar árvores de expressão para criar consultas LINQ dinâmicas. Consultas dinâmicas são úteis quando as especificações de uma consulta não são conhecidas em tempo de compilação. Por exemplo, um aplicativo pode fornecer uma interface de usuário que permite ao usuário final especificar um ou mais predicados para filtrar os dados. Para usar LINQ para consultar, esse tipo de aplicativo deve usar árvores de expressão para criar a consulta LINQ em tempo de execução.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar árvores de expressão para construir uma consulta em relação a um `IQueryable` fonte de dados e, em seguida, executá-lo. O código cria uma árvore de expressão para representar a consulta a seguir:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Os métodos de fábrica no <xref:System.Linq.Expressions>namespace são usados para criar árvores de expressão que representam as expressões que compõem a consulta geral.</xref:System.Linq.Expressions> As expressões que representam as chamadas para os métodos de operador de consulta padrão se referem a <xref:System.Linq.Queryable>implementações dos métodos a seguir.</xref:System.Linq.Queryable> A árvore de expressão final é passada para o <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>implementação do provedor do `IQueryable` fonte de dados para criar uma consulta executável do tipo `IQueryable`.</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> Os resultados são obtidos, enumerando essa variável de consulta.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Esse código usa um número fixo de expressões no predicado que é passado para o `Queryable.Where` método. No entanto, você pode escrever um aplicativo que combina um número variável de expressões de predicado que depende da entrada do usuário. Você também pode variar os operadores de consulta padrão que são chamados na consulta, dependendo da entrada do usuário.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Criar um novo **aplicativo de Console** projeto.  
  
-   Adicione uma referência a System.Core.dll se já não está referenciado.  
  
-   Inclua o namespace System.Linq.Expressions.  
  
-   Copie o código do exemplo e cole-a na `Main` `Sub` procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Como: executar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
