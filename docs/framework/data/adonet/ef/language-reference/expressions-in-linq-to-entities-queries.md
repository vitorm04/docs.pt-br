---
title: Expressões em consultas LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250981"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Expressões em consultas LINQ to Entities
Uma expressão é um fragmento de código que pode ser avaliado como um único valor, objeto, método ou namespace. As expressões podem conter um valor literal, uma chamada de método, um operador e seus operandos ou um nome simples. Os nomes simples podem ser o nome de uma variável, um membro de tipo, um parâmetro de método, um namespace ou um tipo. As expressões podem usar operadores que, por sua vez, usam outras expressões como parâmetros ou chamadas de métodos cujos parâmetros são, por sua vez, outras chamadas de métodos. Portanto, as expressões podem variar de simples a muito complexas.  
  
 Em consultas LINQ to Entities, as expressões podem conter qualquer coisa permitida pelos tipos dentro <xref:System.Linq.Expressions> do namespace, incluindo expressões lambda. As expressões que podem ser usadas em LINQ to Entities consultas são um superconjunto das expressões que podem ser usadas para consultar o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  As expressões que fazem parte das consultas [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] no são limitadas às operações `ObjectQuery<T>` com suporte no e na fonte de dados subjacente.  
  
 No exemplo a seguir, a comparação na cláusula `Where` é uma expressão:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Construções de linguagem específicas, C# `unchecked`como, não têm significado em LINQ to Entities.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Expressões constantes](constant-expressions.md)  
  
 [Expressões de comparação](comparison-expressions.md)  
  
 [Comparações nulas](null-comparisons.md)  
  
 [Expressões de inicialização](initialization-expressions.md)  
  
 [Relações, propriedades de navegação e chaves estrangeiras](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Consulte também

- [Entity Framework do ADO.NET](../index.md)
