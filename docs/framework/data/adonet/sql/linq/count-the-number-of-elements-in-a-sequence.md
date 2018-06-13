---
title: Conta todas o número de elementos em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 928cfd33a187637c6d18da3cccefb22bb2950acf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353825"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Conta todas o número de elementos em uma sequência
Use o operador de <xref:System.Linq.Enumerable.Count%2A> para contar o número de elementos em uma sequência.  
  
 Executando esta consulta na base de dados de exemplo Northwind gerencia uma saída de `91`.  
  
## <a name="example"></a>Exemplo  
 O exemplo conta o número de `Customers` na base de dados.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo conta o número de produtos na base de dados que não foi interrompida.  
  
 Executando este exemplo com o base de dados de exemplo Northwind gerencia uma saída de `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultas agregadas](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)
