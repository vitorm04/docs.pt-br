---
title: Converter um tipo genérico a um IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c2d34ae708f79d9f920679b3714a100fe8943c38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164409"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Converter um tipo genérico a um IEnumerable

Use <xref:System.Linq.Enumerable.AsEnumerable%2A> para retornar o argumento tipado como `IEnumerable`genérico.  
  
## <a name="example"></a>Exemplo  

 Nesse exemplo, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (usando `Query`genérico padrão) tentaria converter a consulta SQL e executados no servidor. Mas a cláusula de `where` referencia um método do lado do cliente definido pelo usuário (`isValidProduct`), que não pode ser convertido para SQL.  
  
 A solução é especificar a implementação genérica do lado do cliente de <xref:System.Collections.Generic.IEnumerable%601> de `where` para substituir <xref:System.Linq.IQueryable%601>genérico. Você faz isso chamando o operador de <xref:System.Linq.Enumerable.AsEnumerable%2A> .  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Confira também

- [Exemplos de consulta](query-examples.md)
