---
title: 'Como: Chamar funções de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: c9cb8d32227447d3808dc250a39fef0867257a77
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250777"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="e4340-102">Como: Chamar funções de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e4340-102">How to: Call Database Functions</span></span>
<span data-ttu-id="e4340-103">A classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> contém os métodos que expõe funções do SQL Server para usar em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="e4340-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="e4340-104">Quando você usa métodos de <xref:System.Data.Objects.SqlClient.SqlFunctions> em consultas LINQ to Entities, as funções de base de dados correspondentes são executadas em base de dados.</span><span class="sxs-lookup"><span data-stu-id="e4340-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4340-105">Funções de base de dados que executar um cálculo em um conjunto de valores e retornar um valor único (também conhecido como funções de base de dados agregadas) podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="e4340-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="e4340-106">Outras funções canônicas só podem ser chamados como parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="e4340-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="e4340-107">Para chamar diretamente uma função agregada, você deve passar <xref:System.Data.Objects.ObjectQuery%601> à função.</span><span class="sxs-lookup"><span data-stu-id="e4340-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="e4340-108">Para obter mais informações, consulte o segundo exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="e4340-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4340-109">Os métodos na classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> são específicos para funções SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4340-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="e4340-110">As classes semelhantes que expõe funções de base de dados podem estar disponíveis através de outros provedores.</span><span class="sxs-lookup"><span data-stu-id="e4340-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4340-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4340-111">Example</span></span>  
 <span data-ttu-id="e4340-112">O exemplo a seguir usa o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="e4340-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="e4340-113">O exemplo executa uma consulta LINQ to entidades que usa o método de <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> para retornar todos os contatos cujo nome começa com “si”:</span><span class="sxs-lookup"><span data-stu-id="e4340-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="e4340-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4340-114">Example</span></span>  
 <span data-ttu-id="e4340-115">O exemplo a seguir usa o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="e4340-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="e4340-116">O exemplo chama o método agregado de <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> diretamente.</span><span class="sxs-lookup"><span data-stu-id="e4340-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="e4340-117">Observe que <xref:System.Data.Objects.ObjectQuery%601> é passado para a função, que permite que é chamado sem ser parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="e4340-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e4340-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4340-118">See also</span></span>

- [<span data-ttu-id="e4340-119">Chamando funções em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e4340-119">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="e4340-120">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e4340-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
