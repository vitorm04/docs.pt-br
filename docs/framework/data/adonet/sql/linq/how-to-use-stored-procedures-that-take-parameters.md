---
title: 'Como: Use os procedimentos armazenados que têm parâmetros'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 05ecc467f75fbeda785b4bac1c3b8b1ceeb173b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174323"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="680b4-102">Como: Use os procedimentos armazenados que têm parâmetros</span><span class="sxs-lookup"><span data-stu-id="680b4-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="680b4-103">mapeia parâmetros de saída para definições de referência, e para tipos de valor declara o parâmetro como anulável.</span><span class="sxs-lookup"><span data-stu-id="680b4-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="680b4-104">Para obter um exemplo de como usar um parâmetro de entrada em uma consulta que retorna um conjunto de linhas, consulte [Como: Retorneio conjuntos de linhas](how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="680b4-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="680b4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="680b4-105">Example</span></span>  
 <span data-ttu-id="680b4-106">O exemplo a seguir utiliza um único parâmetro de entrada (a identificação do cliente) e retorna um parâmetro de saída (o total de vendas para aquele cliente.)</span><span class="sxs-lookup"><span data-stu-id="680b4-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="680b4-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="680b4-107">Example</span></span>  
 <span data-ttu-id="680b4-108">Você poderia chamar esse procedimento armazenado como segue:</span><span class="sxs-lookup"><span data-stu-id="680b4-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="680b4-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="680b4-109">See also</span></span>

- [<span data-ttu-id="680b4-110">Procedimentos Armazenados</span><span class="sxs-lookup"><span data-stu-id="680b4-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="680b4-111">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="680b4-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="680b4-112">Tipos de valor anulados (C#)</span><span class="sxs-lookup"><span data-stu-id="680b4-112">Nullable Value Types (C#)</span></span>](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="680b4-113">Tipos de valor que permitem valor nulo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="680b4-113">Nullable Value Types (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
