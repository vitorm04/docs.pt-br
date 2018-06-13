---
title: Retornar o primeiro elemento em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: fd228b2d7534feca3cff49586ac0d43fbf9bcb1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361342"
---
# <a name="return-the-first-element-in-a-sequence"></a>Retornar o primeiro elemento em uma sequência
Use o operador de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma sequência. Consultas que usam <xref:System.Linq.Enumerable.First%2A> é executado imediatamente.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não suporta o operador de <xref:System.Linq.Enumerable.Last%2A> .  
  
## <a name="example"></a>Exemplo  
 O código a seguir localiza o primeiro `Shipper` em uma tabela:  
  
 Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir localiza único `Customer` que tem `CustomerID` BONAP.  
  
 Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)
