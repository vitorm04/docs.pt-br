---
title: "Formular junções e consultas entre produtos"
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
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b21bee335c5856c961c5abc21ad03c5d1f2c2307
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="formulate-joins-and-cross-product-queries"></a>Formular junções e consultas entre produtos
Os exemplos a seguir mostram como combinar resultados de várias tabelas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a navegação de chave estrangeira no `From` cláusula [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` cláusula em c#) para selecionar todos os pedidos de clientes em Londres.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a navegação de chave estrangeira no `Where` cláusula [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` cláusula em c#) para filtrar a saída de estoque `Products` cujo `Supplier` nos Estados Unidos.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a navegação de chave estrangeira na cláusula `From` no [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (cláusula `from` no C#) para filtrar funcionários em Seattle e para listar seus territórios.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a navegação de chave estrangeira no `Select` cláusula [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` cláusula em c#) para filtrar para pares de funcionários em que um funcionário relata para o outro e em que ambos os funcionários são da mesma `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] exemplo procura todos os clientes e pedidos, certifica-se de que as ordens sejam correspondidas aos clientes e garante que, para cada cliente na lista, é fornecido um nome de contato.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir une explicitamente duas tabelas e os resultados dos projetos das duas tabelas.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir une explicitamente três tabelas e os resultados dos projetos de cada uma delas.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter um `LEFT OUTER JOIN` usando `DefaultIfEmpty()`. O método `DefaultIfEmpty()` retorna nulo quando não há nenhum `Order` para o `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir projeta uma expressão `let` resultante de uma junção.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um `join` com uma chave composta.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como construir um `join` onde um lado é anulável e o outro não.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
