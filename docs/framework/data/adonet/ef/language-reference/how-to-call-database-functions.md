---
title: "Como: Funções de base de dados de chamada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7d385917940e1359b2dc5bef24bb1353db707424
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="99b77-102">Como: Funções de base de dados de chamada</span><span class="sxs-lookup"><span data-stu-id="99b77-102">How to: Call Database Functions</span></span>
<span data-ttu-id="99b77-103">A classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> contém os métodos que expõe funções do SQL Server para usar em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="99b77-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="99b77-104">Quando você usa métodos de <xref:System.Data.Objects.SqlClient.SqlFunctions> em consultas LINQ to Entities, as funções de base de dados correspondentes são executadas em base de dados.</span><span class="sxs-lookup"><span data-stu-id="99b77-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99b77-105">Funções de base de dados que executar um cálculo em um conjunto de valores e retornar um valor único (também conhecido como funções de base de dados agregadas) podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="99b77-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="99b77-106">Outras funções canônicas só podem ser chamados como parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="99b77-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="99b77-107">Para chamar diretamente uma função agregada, você deve passar <xref:System.Data.Objects.ObjectQuery%601> à função.</span><span class="sxs-lookup"><span data-stu-id="99b77-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="99b77-108">Para obter mais informações, consulte o segundo exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="99b77-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99b77-109">Os métodos na classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> são específicos para funções SQL Server.</span><span class="sxs-lookup"><span data-stu-id="99b77-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="99b77-110">As classes semelhantes que expõe funções de base de dados podem estar disponíveis através de outros provedores.</span><span class="sxs-lookup"><span data-stu-id="99b77-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99b77-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99b77-111">Example</span></span>  
 <span data-ttu-id="99b77-112">O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="99b77-112">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="99b77-113">O exemplo executa uma consulta LINQ to entidades que usa o método de <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> para retornar todos os contatos cujo nome começa com “si”:</span><span class="sxs-lookup"><span data-stu-id="99b77-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="99b77-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99b77-114">Example</span></span>  
 <span data-ttu-id="99b77-115">O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="99b77-115">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="99b77-116">O exemplo chama o método agregado de <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> diretamente.</span><span class="sxs-lookup"><span data-stu-id="99b77-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="99b77-117">Observe que <xref:System.Data.Objects.ObjectQuery%601> é passado para a função, que permite que é chamado sem ser parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="99b77-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="99b77-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99b77-118">See Also</span></span>  
 [<span data-ttu-id="99b77-119">Chamando funções em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="99b77-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="99b77-120">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="99b77-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
