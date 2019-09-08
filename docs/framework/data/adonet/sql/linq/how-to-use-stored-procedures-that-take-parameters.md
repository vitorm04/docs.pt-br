---
title: 'Como: usar procedimentos armazenados que usam parâmetros'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793067"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="5f6ac-102">Como: usar procedimentos armazenados que usam parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f6ac-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5f6ac-103">mapeia parâmetros de saída para definições de referência, e para tipos de valor declara o parâmetro como anulável.</span><span class="sxs-lookup"><span data-stu-id="5f6ac-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="5f6ac-104">Para obter um exemplo de como usar um parâmetro de entrada em uma consulta que retorna um conjunto de [linhas, consulte Como: Retornar conjuntos](how-to-return-rowsets.md)de linhas.</span><span class="sxs-lookup"><span data-stu-id="5f6ac-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f6ac-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f6ac-105">Example</span></span>  
 <span data-ttu-id="5f6ac-106">O exemplo a seguir utiliza um único parâmetro de entrada (a identificação do cliente) e retorna um parâmetro de saída (o total de vendas para aquele cliente.)</span><span class="sxs-lookup"><span data-stu-id="5f6ac-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="5f6ac-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f6ac-107">Example</span></span>  
 <span data-ttu-id="5f6ac-108">Você poderia chamar esse procedimento armazenado como segue:</span><span class="sxs-lookup"><span data-stu-id="5f6ac-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5f6ac-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f6ac-109">See also</span></span>

- [<span data-ttu-id="5f6ac-110">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="5f6ac-110">Stored Procedures</span></span>](stored-procedures.md)
- <span data-ttu-id="5f6ac-111">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="5f6ac-111">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
- [<span data-ttu-id="5f6ac-112">Usando tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="5f6ac-112">Using Nullable Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="5f6ac-113">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="5f6ac-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
