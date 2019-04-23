---
title: Formule projeções
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223297"
---
# <a name="formulate-projections"></a>Formule projeções
Os exemplos a seguir mostram como o `select` instrução no C# e `Select` instrução no Visual Basic pode ser combinada com outros recursos para formar projeções de consulta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula C#) para retornar uma sequência de nomes de contato para `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula C#) e *tipos anônimos* para retornar uma sequência de nomes de contato e números de telefone para `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula C#) e *tipos anônimos* para retornar uma sequência de nomes e números de telefone para funcionários. O `FirstName` e `LastName` campos são combinados em um único campo (`Name`) e o `HomePhone` campo foi renomeado para `Phone` na sequência resultante.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula C#) e *tipos anônimos* para retornar uma sequência de todos os `ProductID`s e um valor calculado chamado `HalfPrice`. Esse valor é definido como `UnitPrice` dividido por 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula C#) e um *instrução condicional* para retornar uma sequência de nome do produto e a disponibilidade do produto.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um Visual Basic `Select` cláusula (`select` cláusula C#) e um *tipo conhecido* (nome) para retornar uma sequência de nomes de funcionários.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` e `Where` no Visual Basic (`select` e `where` em C#) para retornar uma *sequência filtrada* de nomes de contato para clientes em Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `Select` cláusula no Visual Basic (`select` cláusula C#) e *tipos anônimos* para retornar uma *um subconjunto moldado* dos dados sobre clientes.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa consultas aninhadas para retornar os resultados seguintes:  
  
-   Uma sequência de todos os pedidos e seu `OrderID`correspondente S.  
  
-   Um subsequence dos itens na ordem para que há desconto.  
  
-   A quantidade de caixa salva se os custos de enviar não são incluídos.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
