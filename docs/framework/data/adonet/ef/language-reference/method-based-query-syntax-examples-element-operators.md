---
title: 'Exemplos de sintaxe de consulta baseada em método: Operadores de elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 7add62a2792a0fc82346851b7dd835aad5082742
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397456"
---
# <a name="method-based-query-syntax-examples-element-operators"></a>Exemplos de sintaxe de consulta baseada em método: Operadores de elemento
Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.First%2A> método para consultar o modelo de [vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de consulta baseada em método. O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.  
  
 O exemplo neste tópico usa as seguintes `using` / `Imports` instruções:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a>First  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Linq.Enumerable.First%2A> o método para localizar o primeiro endereço de email que começa com ' Carolina '.  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a>Consulte também

- [Consultas no LINQ to Entities](queries-in-linq-to-entities.md)
