---
title: Retornar a diferença entre duas sequências ajustada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380044"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Retornar a diferença entre duas sequências ajustada
Use o operador de <xref:System.Linq.Queryable.Except%2A> para retornar a diferença entre duas ajustada sequências.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Except%2A> para retornar uma sequência de todos os países/regiões em que `Customers` ativo, mas no qual nenhum `Employees` ao vivo.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Except%2A> é bem definido somente em conjuntos. A semântica de multisets é indefinida.  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Conversão de operador de consulta padrão](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
