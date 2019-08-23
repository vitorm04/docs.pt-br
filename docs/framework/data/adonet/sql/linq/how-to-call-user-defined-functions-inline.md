---
title: 'Como: chamar funções embutidas definidas pelo usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 26eafb9a6ea1a0b416d205e94b0e420b0f4059d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941069"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="e40e0-102">Como: chamar funções embutidas definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e40e0-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="e40e0-103">Embora você possa chamar funções definidas pelo usuário embutidos, as funções que são incluídas em uma consulta cuja execução é adiada não são executadas até que a consulta.</span><span class="sxs-lookup"><span data-stu-id="e40e0-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="e40e0-104">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="e40e0-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="e40e0-105">Quando você chama a mesma função fora de uma consulta, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria uma consulta simples de expressão de chamada de método.</span><span class="sxs-lookup"><span data-stu-id="e40e0-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="e40e0-106">A seguir está a sintaxe do SQL (parâmetro `@p0` é associado à constante passada dentro):</span><span class="sxs-lookup"><span data-stu-id="e40e0-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e40e0-107">cria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e40e0-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="e40e0-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e40e0-108">Example</span></span>  
 <span data-ttu-id="e40e0-109">Na consulta a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] seguir, você pode ver uma chamada embutida para o método `ReverseCustName`de função definido pelo usuário gerado.</span><span class="sxs-lookup"><span data-stu-id="e40e0-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="e40e0-110">A função não é executada imediatamente porque a execução da consulta é adiada.</span><span class="sxs-lookup"><span data-stu-id="e40e0-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="e40e0-111">O SQL compilado para esta consulta converte a uma chamada para a função definida pelo usuário na base de dados (consulte o código SQL seguir a consulta).</span><span class="sxs-lookup"><span data-stu-id="e40e0-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="e40e0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e40e0-112">See also</span></span>

- [<span data-ttu-id="e40e0-113">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e40e0-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
