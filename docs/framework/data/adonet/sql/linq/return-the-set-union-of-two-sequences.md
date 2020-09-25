---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200193"
---
# <a name="return-the-set-union-of-two-sequences"></a>Retornar a união de sequências de duas

Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.  
  
## <a name="example"></a>Exemplo  

 Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países/regiões em que há `Customers` ou `Employees` .  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , o <xref:System.Linq.Queryable.Union%2A> operador é definido para conjuntos de valores como a concatenação não ordenada dos conjuntos de multiconjuntos (efetivamente o resultado da [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) cláusula em SQL).

Para obter mais informações e exemplos, consulte <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> .
  
## <a name="see-also"></a>Veja também

- [Exemplos de consulta](query-examples.md)
- [Conversão padrão de operador de consulta](standard-query-operator-translation.md)
