---
title: 'Como: retornar conjuntos de linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: be03107db73ed230a87c2518e7825461afc2bc7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155738"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="02814-102">Como: retornar conjuntos de linhas</span><span class="sxs-lookup"><span data-stu-id="02814-102">How to: Return Rowsets</span></span>

<span data-ttu-id="02814-103">Este exemplo retorna um conjunto de linhas do banco de dados e inclui um parâmetro de entrada para filtrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="02814-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="02814-104">Ao executar um procedimento armazenado que retorna um conjunto de linhas, você usa uma classe *Result* que armazena os retornos do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="02814-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="02814-105">Para obter mais informações, consulte [analisando LINQ to SQL código-fonte](analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="02814-105">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02814-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02814-106">Example</span></span>  

 <span data-ttu-id="02814-107">O exemplo a seguir representa um procedimento armazenado que retorna linhas de clientes e usa um parâmetro de entrada para retornar somente as linhas que listam "London" como a cidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="02814-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="02814-108">O exemplo supõe uma classe `CustomersByCityResult` enumerável.</span><span class="sxs-lookup"><span data-stu-id="02814-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="02814-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="02814-109">See also</span></span>

- [<span data-ttu-id="02814-110">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="02814-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="02814-111">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="02814-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
