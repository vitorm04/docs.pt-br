---
title: 'Como: usar funções definidas pelo usuário com valor de tabela'
description: Use estes exemplos para aprender a criar uma função com valor de tabela, que retorna um único conjunto de linhas. Use essa função com valor de tabela, assim como uma tabela.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 68a2b54c8fd541595d36bf9c864257b1be1f7856
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203573"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="d4408-104">Como: usar funções definidas pelo usuário com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="d4408-104">How to: Use Table-Valued User-Defined Functions</span></span>

<span data-ttu-id="d4408-105">Uma função de tabela valorizada retorna um único rowset (em vez de procedimentos armazenados, que podem retornar várias formas de resultado).</span><span class="sxs-lookup"><span data-stu-id="d4408-105">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="d4408-106">Porque o tipo de retorno de uma função de tabela valorizada é `Table`, você pode usar uma função de tabela valorizada em qualquer lugar em SQL que você pode usar uma tabela.</span><span class="sxs-lookup"><span data-stu-id="d4408-106">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="d4408-107">Você também pode tratar a função de tabela valorizada assim como você uma tabela.</span><span class="sxs-lookup"><span data-stu-id="d4408-107">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4408-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4408-108">Example</span></span>  

 <span data-ttu-id="d4408-109">A função a seguir indica explicitamente SQL que retorna `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="d4408-109">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="d4408-110">Portanto, a estrutura de rowset retornado é definida implicitamente.</span><span class="sxs-lookup"><span data-stu-id="d4408-110">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d4408-111">mapeia a função como segue:</span><span class="sxs-lookup"><span data-stu-id="d4408-111">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d4408-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4408-112">Example</span></span>  

 <span data-ttu-id="d4408-113">O código a seguir mostra SQL que você pode se juntar a tabela que a função e retorna a trata de outra maneira como você faria qualquer outra tabela:</span><span class="sxs-lookup"><span data-stu-id="d4408-113">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="d4408-114">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a consulta será processada como segue:</span><span class="sxs-lookup"><span data-stu-id="d4408-114">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d4408-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="d4408-115">See also</span></span>

- [<span data-ttu-id="d4408-116">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="d4408-116">User-Defined Functions</span></span>](user-defined-functions.md)
