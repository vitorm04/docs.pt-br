---
title: 'Como: usar procedimentos armazenados que usam parâmetros'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: c2b657f704d072b987578be5520a58d007ecac37
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353009"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="c9b3f-102">Como: usar procedimentos armazenados que usam parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9b3f-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c9b3f-103">mapeia parâmetros de saída para definições de referência, e para tipos de valor declara o parâmetro como anulável.</span><span class="sxs-lookup"><span data-stu-id="c9b3f-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="c9b3f-104">Para obter um exemplo de como usar um parâmetro de entrada em uma consulta que retorna um conjunto de linhas, consulte [How para: Retornar conjuntos de linhas @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="c9b3f-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9b3f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9b3f-105">Example</span></span>  
 <span data-ttu-id="c9b3f-106">O exemplo a seguir utiliza um único parâmetro de entrada (a identificação do cliente) e retorna um parâmetro de saída (o total de vendas para aquele cliente.)</span><span class="sxs-lookup"><span data-stu-id="c9b3f-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c9b3f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9b3f-107">Example</span></span>  
 <span data-ttu-id="c9b3f-108">Você poderia chamar esse procedimento armazenado como segue:</span><span class="sxs-lookup"><span data-stu-id="c9b3f-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c9b3f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9b3f-109">See also</span></span>

- [<span data-ttu-id="c9b3f-110">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="c9b3f-110">Stored Procedures</span></span>](stored-procedures.md)
- <span data-ttu-id="c9b3f-111">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="c9b3f-111">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
- [<span data-ttu-id="c9b3f-112">Usando tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="c9b3f-112">Using Nullable Value Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="c9b3f-113">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="c9b3f-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
