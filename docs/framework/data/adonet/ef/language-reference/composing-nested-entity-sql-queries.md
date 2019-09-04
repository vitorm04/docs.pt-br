---
title: Composta consultas aninhadas Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 3aa2e53b584eece9cc5e2d26791c78ffe33f9e35
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251146"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="5e3a9-102">Composta consultas aninhadas Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5e3a9-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5e3a9-103">é uma linguagem funcional rico.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-103">is a rich functional language.</span></span> <span data-ttu-id="5e3a9-104">O bloco de construção [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="5e3a9-105">Ao contrário do SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] convencional, o não está limitado a um conjunto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de resultados de tabela: dá suporte à composição de expressões complexas que podem ter literais, parâmetros ou expressões aninhadas.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="5e3a9-106">Um valor na expressão pode ser parametrizado ou composto por alguma outra expressão.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="5e3a9-107">Expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="5e3a9-107">Nested Expressions</span></span>  
 <span data-ttu-id="5e3a9-108">Uma expressão aninhada pode ser colocadas em qualquer lugar um valor de tipo que retorna é aceito.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="5e3a9-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5e3a9-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="5e3a9-110">Uma consulta aninhada pode ser colocadas em uma cláusula de projeção.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="5e3a9-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5e3a9-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="5e3a9-112">Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultas aninhadas devem sempre ser colocado entre parênteses:</span><span class="sxs-lookup"><span data-stu-id="5e3a9-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="5e3a9-113">O exemplo a seguir demonstra como aninhar expressões corretamente [!INCLUDE[esql](../../../../../../includes/esql-md.md)]em: [Como: Ordenar a União de duas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))consultas.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="5e3a9-114">Consultas aninhadas na projeção</span><span class="sxs-lookup"><span data-stu-id="5e3a9-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="5e3a9-115">Consultas aninhadas na cláusula de projeto podem obter convertido em consultas de produto cartesiano no servidor.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="5e3a9-116">Em alguns servidores backend, incluindo o servidor de SLQ, isso pode fazer com que a tabela de TempDB obtenha muito grande, que pode afetar o desempenho do servidor.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="5e3a9-117">O seguinte é um exemplo de tal consulta:</span><span class="sxs-lookup"><span data-stu-id="5e3a9-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="5e3a9-118">Ordenando consultas aninhadas</span><span class="sxs-lookup"><span data-stu-id="5e3a9-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="5e3a9-119">Em Entity Framework, uma expressão aninhada pode ser colocadas em qualquer lugar na consulta.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="5e3a9-120">Porque Entity SQL permite grande flexibilidade em consultas de escrita, é possível escrever uma consulta que contém a ordem das consultas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="5e3a9-121">No entanto, a ordem de uma consulta aninhada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="5e3a9-121">However, the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e3a9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e3a9-122">See also</span></span>

- [<span data-ttu-id="5e3a9-123">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5e3a9-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
