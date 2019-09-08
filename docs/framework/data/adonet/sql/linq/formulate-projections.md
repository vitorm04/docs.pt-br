---
title: Formule projeções
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793822"
---
# <a name="formulate-projections"></a>Formule projeções
Os exemplos a seguir mostram como `select` a instrução C# in `Select` e a instrução no Visual Basic podem ser combinadas com outros recursos para formar projeções de consulta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) para retornar uma sequência de nomes de `Customers`contato para.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar uma sequência de nomes de contato e `Customers`números de telefone para o.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar uma sequência de nomes e números de telefone para os funcionários. Os `FirstName` campos `LastName` e são combinados em um único campo (`Name`), e o `HomePhone` campo é renomeado para `Phone` na sequência resultante.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar uma sequência `ProductID`de todos os s e um `HalfPrice`valor calculado chamado. Esse valor é definido como `UnitPrice` dividido por 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e uma *instrução condicional* para retornar uma sequência de nome do produto e disponibilidade do produto.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `Select` cláusula Visual Basic`select` (cláusula C#in) e um *tipo conhecido* (Name) para retornar uma sequência dos nomes dos funcionários.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `Select` usa `Where` e em Visual Basic`select` ( `where` e C#em) para retornar uma *sequência filtrada* de nomes de contato para clientes em Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select` uma cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar um *subconjunto formatado* dos dados sobre os clientes.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa consultas aninhadas para retornar os resultados seguintes:  
  
- Uma sequência de todos os pedidos e seu `OrderID`correspondente S.  
  
- Um subsequence dos itens na ordem para que há desconto.  
  
- A quantidade de caixa salva se os custos de enviar não são incluídos.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](query-examples.md)
