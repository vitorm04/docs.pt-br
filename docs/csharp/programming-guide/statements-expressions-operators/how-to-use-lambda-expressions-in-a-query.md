---
title: Como usar expressões lambda em um guia de C# programação de consulta
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: e66239174d5598d7cf532d21426a9e15d5075085
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635113"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Como usar expressões lambda em uma consulta (C# guia de programação)
Você não usa expressões lambda diretamente na sintaxe da consulta, mas as usa em chamadas de método e as expressões de consulta podem conter chamadas de método. Na verdade, algumas operações de consulta podem ser expressas na sintaxe de método. Para obter mais informações sobre a diferença entre a sintaxe de consulta e sintaxe de método, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar uma expressão lambda em uma consulta baseada em método usando operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>. O método <xref:System.Linq.Enumerable.Where%2A> nesse exemplo tem um parâmetro de entrada do tipo delegado <xref:System.Func%602>, e esse delegado utiliza um inteiro como entrada e retorna um booliano. A expressão lambda pode ser convertida para esse delegado. Se essa fosse uma consulta [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] que usasse o método <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>, o tipo de parâmetro seria um `Expression<Func<int,bool>>`, mas a expressão lambda teria exatamente a mesma aparência. Para saber mais sobre o tipo de expressão, confira <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar uma expressão lambda em uma chamada de método de uma expressão de consulta. O lambda é necessário porque o operador de consulta padrão <xref:System.Linq.Enumerable.Sum%2A> não pode ser invocado usando a sintaxe de consulta.  
  
 A consulta primeiro agrupa os alunos de acordo com o nível de ensino, conforme definido no enum `GradeLevel`. Em seguida, para cada grupo, ela adiciona as pontuações totais de cada aluno. Isso requer duas operações `Sum`. O `Sum` interno calcula a pontuação total para cada estudante e o `Sum` externo mantém um total acumulado combinado para todos os alunos no grupo.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Para executar esse código, copie e cole o método no `StudentClass` fornecido em [consultar uma coleção de objetos](../../linq/query-a-collection-of-objects.md) e chame-o do método `Main`.
  
## <a name="see-also"></a>Veja também

- [Expressões Lambda](./lambda-expressions.md)
- [Árvores de expressão (C#)](../concepts/expression-trees/index.md)
