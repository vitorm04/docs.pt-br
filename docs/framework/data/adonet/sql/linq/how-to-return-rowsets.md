---
title: 'Como: retornar conjuntos de linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 599ad6f722251003ab56547ce050cbd0e8da831d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168708"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="f7397-102">Como: retornar conjuntos de linhas</span><span class="sxs-lookup"><span data-stu-id="f7397-102">How to: Return Rowsets</span></span>
<span data-ttu-id="f7397-103">Este exemplo retorna um conjunto de linhas do banco de dados e inclui um parâmetro de entrada para filtrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="f7397-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="f7397-104">Quando você executar um procedimento armazenado que retorna um conjunto de linhas, você usar um *resultado* classe que armazena os valores retornados pelo procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="f7397-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="f7397-105">Para obter mais informações, consulte [Analisando código LINQ to SQL fonte](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="f7397-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7397-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7397-106">Example</span></span>  
 <span data-ttu-id="f7397-107">O exemplo a seguir representa um procedimento armazenado que retorna linhas de clientes e usa um parâmetro de entrada para retornar somente as linhas que listam "London" como a cidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="f7397-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="f7397-108">O exemplo supõe uma classe `CustomersByCityResult` enumerável.</span><span class="sxs-lookup"><span data-stu-id="f7397-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="f7397-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7397-109">See also</span></span>

- [<span data-ttu-id="f7397-110">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="f7397-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- <span data-ttu-id="f7397-111">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="f7397-111">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>
