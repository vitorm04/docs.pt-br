---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 058856243b2a8daaecd653a9b5999013de5407a8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182531"
---
# <a name="return-the-set-union-of-two-sequences"></a>Retornar a união de sequências de duas
Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países/regiões em que há `Customers` ou `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o <xref:System.Linq.Queryable.Union%2A> operador é definido para conjuntos de valores como a concatenação não ordenada dos conjuntos de multiconjuntos ( [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) efetivamente o resultado da cláusula em SQL).

Para obter mais informações e exemplos, <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>consulte.
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](query-examples.md)
- [Conversão de operador de consulta padrão](standard-query-operator-translation.md)
