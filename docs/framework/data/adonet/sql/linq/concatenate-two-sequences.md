---
title: Concatenar duas sequências
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 87d341357b8d11eafbc3f3867c45ac5a32270688
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164396"
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
  
## <a name="see-also"></a>Confira também

- [Exemplos de consulta](query-examples.md)
- [Conversão padrão de operador de consulta](standard-query-operator-translation.md)
