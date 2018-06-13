---
title: 'Como: Chamar funções definidas pelo usuário in-line'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 39eeab06952e1d8a1128580a2be79ed4711d58d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359394"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="631c3-102">Como: Chamar funções definidas pelo usuário in-line</span><span class="sxs-lookup"><span data-stu-id="631c3-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="631c3-103">Embora você possa chamar funções definidas pelo usuário embutidos, as funções que são incluídas em uma consulta cuja execução é adiada não são executadas até que a consulta.</span><span class="sxs-lookup"><span data-stu-id="631c3-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="631c3-104">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="631c3-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="631c3-105">Quando você chama a mesma função fora de uma consulta, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria uma consulta simples de expressão de chamada de método.</span><span class="sxs-lookup"><span data-stu-id="631c3-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="631c3-106">A seguir está a sintaxe do SQL (parâmetro `@p0` é associado à constante passada dentro):</span><span class="sxs-lookup"><span data-stu-id="631c3-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="631c3-107"> cria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="631c3-107"> creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="631c3-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="631c3-108">Example</span></span>  
 <span data-ttu-id="631c3-109">A seguir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consulta, você pode ver um embutido chamada para o método de função definida pelo usuário gerado `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="631c3-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="631c3-110">A função não é executada imediatamente porque a execução da consulta é adiada.</span><span class="sxs-lookup"><span data-stu-id="631c3-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="631c3-111">O SQL compilado para esta consulta converte a uma chamada para a função definida pelo usuário na base de dados (consulte o código SQL seguir a consulta).</span><span class="sxs-lookup"><span data-stu-id="631c3-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="631c3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="631c3-112">See Also</span></span>  
 [<span data-ttu-id="631c3-113">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="631c3-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
