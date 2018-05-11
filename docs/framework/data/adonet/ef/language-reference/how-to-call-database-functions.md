---
title: 'Como: Funções de base de dados de chamada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: b885cedbb324ee0a076990bceb28bf256814bb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="9c96b-102">Como: Funções de base de dados de chamada</span><span class="sxs-lookup"><span data-stu-id="9c96b-102">How to: Call Database Functions</span></span>
<span data-ttu-id="9c96b-103">A classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> contém os métodos que expõe funções do SQL Server para usar em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9c96b-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="9c96b-104">Quando você usa métodos de <xref:System.Data.Objects.SqlClient.SqlFunctions> em consultas LINQ to Entities, as funções de base de dados correspondentes são executadas em base de dados.</span><span class="sxs-lookup"><span data-stu-id="9c96b-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c96b-105">Funções de base de dados que executar um cálculo em um conjunto de valores e retornar um valor único (também conhecido como funções de base de dados agregadas) podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="9c96b-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="9c96b-106">Outras funções canônicas só podem ser chamados como parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9c96b-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="9c96b-107">Para chamar diretamente uma função agregada, você deve passar <xref:System.Data.Objects.ObjectQuery%601> à função.</span><span class="sxs-lookup"><span data-stu-id="9c96b-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="9c96b-108">Para obter mais informações, consulte o segundo exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="9c96b-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c96b-109">Os métodos na classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> são específicos para funções SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c96b-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="9c96b-110">As classes semelhantes que expõe funções de base de dados podem estar disponíveis através de outros provedores.</span><span class="sxs-lookup"><span data-stu-id="9c96b-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c96b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c96b-111">Example</span></span>  
 <span data-ttu-id="9c96b-112">O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="9c96b-112">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="9c96b-113">O exemplo executa uma consulta LINQ to entidades que usa o método de <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> para retornar todos os contatos cujo nome começa com “si”:</span><span class="sxs-lookup"><span data-stu-id="9c96b-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="9c96b-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c96b-114">Example</span></span>  
 <span data-ttu-id="9c96b-115">O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="9c96b-115">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="9c96b-116">O exemplo chama o método agregado de <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> diretamente.</span><span class="sxs-lookup"><span data-stu-id="9c96b-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="9c96b-117">Observe que <xref:System.Data.Objects.ObjectQuery%601> é passado para a função, que permite que é chamado sem ser parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9c96b-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9c96b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c96b-118">See Also</span></span>  
 [<span data-ttu-id="9c96b-119">Chamando funções em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9c96b-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="9c96b-120">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9c96b-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
