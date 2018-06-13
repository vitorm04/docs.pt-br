---
title: Formule projeções
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f554007bd8c9e69f6a8dc475c122d3fbdfc43a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364942"
---
# <a name="formulate-projections"></a>Formule projeções
Os exemplos a seguir mostram como o `select` instrução em c# e `Select` instrução no Visual Basic pode ser combinada com outros recursos para projeções de consulta do formulário.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula em c#) para retornar uma sequência de nomes de contato para `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula em c#) e *tipos anônimos* para retornar uma sequência de nomes de contatos e números de telefone `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula em c#) e *tipos anônimos* para retornar uma sequência de nomes e números de telefone para os funcionários. O `FirstName` e `LastName` campos são combinados em um único campo (`Name`) e o `HomePhone` campo é renomeado para `Phone` na sequência resultante.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula em c#) e *tipos anônimos* para retornar uma sequência de todos os `ProductID`s e um valor calculado chamado `HalfPrice`. Esse valor é definido como `UnitPrice` dividido por 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Select` cláusula no Visual Basic (`select` cláusula em c#) e um *instrução condicional* para retornar uma sequência de nome do produto e a disponibilidade do produto.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um Visual Basic `Select` cláusula (`select` cláusula em c#) e um *conhecido tipo* (nome) para retornar uma sequência de nomes de funcionários.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` e `Where` no Visual Basic (`select` e `where` em c#) para retornar um *filtrados sequência* de nomes de contato para clientes em Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `Select` cláusula no Visual Basic (`select` cláusula em c#) e *tipos anônimos* para retornar um *em forma de subconjunto* dos dados sobre clientes.  
  
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
 [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
