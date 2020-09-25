---
title: 'Como: usar procedimentos armazenados que usam parâmetros'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: a54e2ee553629179022b68658d44cbcb02ab590f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184957"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Como: usar procedimentos armazenados que usam parâmetros

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapeia parâmetros de saída para definições de referência, e para tipos de valor declara o parâmetro como anulável.  
  
 Para obter um exemplo de como usar um parâmetro de entrada em uma consulta que retorna um conjunto de linhas, consulte [How to: Return DataSets](how-to-return-rowsets.md).  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir utiliza um único parâmetro de entrada (a identificação do cliente) e retorna um parâmetro de saída (o total de vendas para aquele cliente.)  
  
```sql
CREATE PROCEDURE [dbo].[CustOrderTotal]
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>Exemplo  

 Você poderia chamar esse procedimento armazenado como segue:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Veja também

- [Procedimentos armazenados](stored-procedures.md)
- [Baixar bancos de dados de amostra](downloading-sample-databases.md)
- [Tipos de valor anulável (C#)](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [Tipos de valor que permitem valor nulo (Visual Basic)](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
