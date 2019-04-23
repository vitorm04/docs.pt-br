---
title: Concatenar duas sequências
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: a2f2510cb334f4e22a7b0c6015a0a93b4dc11579
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142773"
---
# <a name="concatenate-two-sequences"></a>Concatenar duas sequências
Use o operador de <xref:System.Linq.Queryable.Concat%2A> para concatenar duas sequências.  
  
 O operador de <xref:System.Linq.Queryable.Concat%2A> é definido para os multisets ordenados onde os pedidos do receptor e argumento são os mesmos.  
  
 Ordenação em SQL é a etapa final antes que os resultados são gerados. Por esse motivo, o operador de <xref:System.Linq.Queryable.Concat%2A> é implementado usando `UNION ALL` e não preserva a ordem dos argumentos. Para certificar-se de ordenação está correta nos resultados, certifique-se pedir explicitamente os resultados.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Concat%2A> para retornar uma sequência de todos os números de `Customer` e de telefone e fax de `Employee` .  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Queryable.Concat%2A> para retornar uma sequência mapeamentos de qualquer nome de `Customer` e de `Employee` e de número de telefone.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Conversão de operador de consulta padrão](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
