---
title: "Calcular a soma dos valores em uma sequência numérica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 547d9f245d41fac2e2d65877ddbb2a8660d73c42
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Calcular a soma dos valores em uma sequência numérica
Use o operador <xref:System.Linq.Enumerable.Sum%2A> para calcular a soma de valores numéricos em uma sequência.  
  
 Observe as seguintes características do operador `Sum` no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   O operador de agregação do operador de consulta padrão `Sum` avalia uma sequência vazia ou uma sequência que contém somente nulos como zero. No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a semântica do SQL é deixada inalterada. Por esse motivo, `Sum` avalia como nulo em vez de zero para uma sequência vazia ou para uma sequência que contém somente nulos.  
  
-   As limitações do SQL em resultados intermediários se aplicam às agregações no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Soma das quantidades de inteiro de 32 bits não é calculada usando resultados de 64 bits e estouro pode ocorrer devido a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tradução do `Sum`. Essa possibilidade existe mesmo se a implementação do operador de consulta padrão não causa um estouro para a sequência correspondente na memória.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir localiza o frete total de todos os pedidos na tabela `Order`.  
  
 Se você executar essa consulta no banco de dados de exemplo do Northwind, a saída será: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir localiza o número total de unidades no pedido para todos os produtos.  
  
 Se você executar essa consulta no banco de dados de exemplo do Northwind, a saída será: `780`.  
  
 Observe que você deve converter tipos `short` (por exemplo, `UnitsOnOrder`) porque `Sum` não tem sobrecarga para tipos curtos.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultas agregadas](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)
