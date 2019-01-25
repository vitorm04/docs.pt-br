---
title: Localizar o valor máximo em uma sequência numérica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: 26b7fe7448b9338802f8b8f5e2e91486d1883bbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570233"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Localizar o valor máximo em uma sequência numérica
Use o operador de <xref:System.Linq.Enumerable.Max%2A> para localizar o valor mais alto em uma sequência de valores numéricos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir localiza a última data de aluguer para qualquer funcionários.  
  
 Se você executa essa consulta na base de dados de exemplo Northwind, a saída são: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir localiza a maioria de unidades em estoque para qualquer produto.  
  
 Se você executa esse exemplo com o base de dados de exemplo Northwind, a saída são: `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Exemplo  
 Os seguintes o exemplo usa máximo para localizar `Products` que têm o preço unitário o maior em cada categoria. A saída listam os resultados por categoria.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Se você executa a consulta anterior com o base de dados de exemplo Northwind, resultados assemelhar-se-ão o seguinte:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a>Consulte também
- [Consultas agregadas](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)
