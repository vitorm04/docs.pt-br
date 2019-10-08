---
title: 'Como: usar funções definidas pelo usuário com valor de tabela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: c4b5290e4f1aa69c7f55951d526ccb303a5a95ec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003178"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="99c1e-102">Como: usar funções definidas pelo usuário com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="99c1e-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="99c1e-103">Uma função de tabela valorizada retorna um único rowset (em vez de procedimentos armazenados, que podem retornar várias formas de resultado).</span><span class="sxs-lookup"><span data-stu-id="99c1e-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="99c1e-104">Porque o tipo de retorno de uma função de tabela valorizada é `Table`, você pode usar uma função de tabela valorizada em qualquer lugar em SQL que você pode usar uma tabela.</span><span class="sxs-lookup"><span data-stu-id="99c1e-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="99c1e-105">Você também pode tratar a função de tabela valorizada assim como você uma tabela.</span><span class="sxs-lookup"><span data-stu-id="99c1e-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c1e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99c1e-106">Example</span></span>  
 <span data-ttu-id="99c1e-107">A função a seguir indica explicitamente SQL que retorna `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="99c1e-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="99c1e-108">Portanto, a estrutura de rowset retornado é definida implicitamente.</span><span class="sxs-lookup"><span data-stu-id="99c1e-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="99c1e-109">mapeia a função como segue:</span><span class="sxs-lookup"><span data-stu-id="99c1e-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="99c1e-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99c1e-110">Example</span></span>  
 <span data-ttu-id="99c1e-111">O código a seguir mostra SQL que você pode se juntar a tabela que a função e retorna a trata de outra maneira como você faria qualquer outra tabela:</span><span class="sxs-lookup"><span data-stu-id="99c1e-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="99c1e-112">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a consulta será processada como segue:</span><span class="sxs-lookup"><span data-stu-id="99c1e-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="99c1e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99c1e-113">See also</span></span>

- [<span data-ttu-id="99c1e-114">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="99c1e-114">User-Defined Functions</span></span>](user-defined-functions.md)
