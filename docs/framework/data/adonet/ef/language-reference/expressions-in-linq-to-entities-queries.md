---
title: "Expressões em consultas LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f429a354c4042f0e85b9ef078bbc57ebe510d0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="expressions-in-linq-to-entities-queries"></a>Expressões em consultas LINQ to Entities
Uma expressão é um fragmento de código que pode ser avaliado como um único valor, objeto, método ou namespace. As expressões podem conter um valor literal, uma chamada de método, um operador e seus operandos ou um nome simples. Os nomes simples podem ser o nome de uma variável, um membro de tipo, um parâmetro de método, um namespace ou um tipo. As expressões podem usar operadores que, por sua vez, usam outras expressões como parâmetros ou chamadas de métodos cujos parâmetros são, por sua vez, outras chamadas de métodos. Portanto, as expressões podem variar de simples a muito complexas.  
  
 Em [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consultas, as expressões podem conter qualquer coisa permitido pelos tipos de dentro do <xref:System.Linq.Expressions> namespace, incluindo expressões lambda. A expressões que podem ser usadas em consultas [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] são um superconjunto das expressões que podem ser usadas para consultar o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Expressões que fazem parte de consultas em relação a [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] são limitados a operações com suporte pelo `ObjectQuery<T>` e fonte de dados subjacente.  
  
 No exemplo a seguir, a comparação na cláusula `Where` é uma expressão:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Os constructos de linguagens específicos, como `unchecked` do C#, não têm significado no [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Expressões constantes](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Expressões de comparação](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Comparações nulas](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Expressões de inicialização](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Propriedades de navegação](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Consulte também  
 [Entity Framework do ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
