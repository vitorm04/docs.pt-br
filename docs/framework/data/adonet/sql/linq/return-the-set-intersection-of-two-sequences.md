---
title: Retornar a interseção de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 944d0b2efe1e74f901a493d1c3202d0f180d599d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792710"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Retornar a interseção de sequências de duas
Use o operador de <xref:System.Linq.Queryable.Intersect%2A> para retornar a interseção ajustada de duas sequências.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Intersect%2A> para retornar uma sequência de todos os países/regiões nos quais `Customers` o `Employees` e o dinâmico.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Intersect%2A> é bem definido somente em conjuntos. A semântica de multisets é indefinida.  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](query-examples.md)
- [Conversão de operador de consulta padrão](standard-query-operator-translation.md)
