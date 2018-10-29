---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: ffdc1dc0f9b5c2ed3b9898d0c71c9b384723fe05
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200543"
---
# <a name="return-the-set-union-of-two-sequences"></a>Retornar a união de sequências de duas
Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países em que há `Customers` ou `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 Na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o <xref:System.Linq.Queryable.Union%2A> operador está definido para multisets como concatenação não ordenada de multisets (efetivamente o resultado das [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) cláusula no SQL).

Para obter mais informações e exemplos, consulte <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Conversão de operador de consulta padrão](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
