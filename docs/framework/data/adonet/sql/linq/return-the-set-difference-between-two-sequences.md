---
title: Retornar a diferença entre duas sequências ajustada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 7edc60c7ab8510aadd9ac273529a88adeb41352a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124274"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Retornar a diferença entre duas sequências ajustada
Use o operador de <xref:System.Linq.Queryable.Except%2A> para retornar a diferença entre duas ajustada sequências.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Except%2A> para retornar uma sequência de todos os países em que `Customers` ativa mas em que nenhum `Employees` ativa.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Except%2A> é bem definido somente em conjuntos. A semântica de multisets é indefinida.  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Conversão de operador de consulta padrão](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
