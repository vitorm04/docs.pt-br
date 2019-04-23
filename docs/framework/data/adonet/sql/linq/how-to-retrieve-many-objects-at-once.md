---
title: 'Como: recuperar vários objetos por vez'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: dd53c2fd16a82ce0f69a33e0b7d7ffef7815b91b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220520"
---
# <a name="how-to-retrieve-many-objects-at-once"></a>Como: recuperar vários objetos por vez
Você pode recuperar vários objetos em uma consulta usando <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.  
  
## <a name="example"></a>Exemplo  
 O código a seguir usa o método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para recuperar `Customer` e objetos de `Order` .  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
