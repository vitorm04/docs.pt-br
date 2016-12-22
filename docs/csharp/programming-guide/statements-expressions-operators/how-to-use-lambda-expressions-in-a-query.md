---
title: "Como usar express&#245;es lambda em uma consulta (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "expressões lambda [C#], em LINQ"
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar express&#245;es lambda em uma consulta (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você não usa expressões lambda diretamente na sintaxe de consulta, mas você usa em chamadas de método e expressões de consulta que contenham chamadas de método.  Na verdade, algumas operações de consulta só podem ser expressa na sintaxe do método.  Para obter mais informações sobre a diferença entre a sintaxe de consulta e a sintaxe do método, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## Exemplo  
 O exemplo a seguir demonstra como usar uma expressão lambda em uma consulta baseada em método usando o <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> o operador de consulta padrão.  Observe que o <xref:System.Linq.Enumerable.Where%2A> método neste exemplo possui um parâmetro de entrada do tipo delegado <xref:System.Func%601> e esse delegado tem um inteiro como entrada e retorna um valor booleano.  A expressão lambda pode ser convertida para esse representante.  Se fosse um [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)] de consulta que usou o <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName> método, o tipo de parâmetro seria uma `Expression<Func\<int,bool>>` , mas a expressão lambda ficaria exatamente o mesmo.  Para obter mais informações sobre o tipo de expressão, consulte <xref:System.Linq.Expressions.Expression?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## Exemplo  
 O exemplo a seguir demonstra como usar uma expressão lambda em uma chamada de método de uma expressão de consulta.  Lambda é necessário porque o <xref:System.Linq.Enumerable.Sum%2A> não é possível chamar o operador de consulta padrão, usando a sintaxe de consulta.  
  
 A consulta agrupa pela primeira vez que os alunos de acordo com seu nível de graduação, conforme definido na `GradeLevel` enum.  Em seguida, para cada grupo, ele adiciona a pontuação total para cada aluno.  Isso requer dois `Sum` as operações.  Interno `Sum` calcula a pontuação total para cada aluno e o externo `Sum` mantém um em execução, o total combinado para todos os alunos do grupo.  
  
 [!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## Compilando o código  
 Para executar esse código, copie e cole o método para o `StudentClass` que é fornecido em [Como consultar uma coleção de objetos](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) e chamá\-la da `Main` método.  
  
## Consulte também  
 [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)