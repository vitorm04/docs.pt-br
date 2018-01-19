---
title: "Como: Funções canônicas de chamada"
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
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 02cbcee218db310fdddc7f42d9b6f01a16a8314d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="5b998-102">Como: Funções canônicas de chamada</span><span class="sxs-lookup"><span data-stu-id="5b998-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="5b998-103">A classe de <xref:System.Data.Objects.EntityFunctions> contém os métodos que expõe funções canônicas para usar em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="5b998-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="5b998-104">Para obter informações sobre funções canônicas, consulte [Funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5b998-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b998-105">Os métodos de <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> e de <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> na classe de <xref:System.Data.Objects.EntityFunctions> não têm equivalentes canônicos de função.</span><span class="sxs-lookup"><span data-stu-id="5b998-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="5b998-106">As funções canônicas que executar um cálculo em um conjunto de valores e retornar um valor único (também conhecido como funções agregadas canônicas) podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="5b998-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="5b998-107">Outras funções canônicas só podem ser chamados como parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="5b998-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="5b998-108">Para chamar diretamente uma função agregada, você deve passar <xref:System.Data.Objects.ObjectQuery%601> à função.</span><span class="sxs-lookup"><span data-stu-id="5b998-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="5b998-109">Para obter mais informações, consulte o segundo exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="5b998-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="5b998-110">Você pode chamar algumas funções canônicas usando métodos do Common Language Runtime (CLR) em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="5b998-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="5b998-111">Para obter uma lista dos métodos CLR que são mapeados para funções canônicas, consulte [método CLR ao mapeamento canônico de função](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="5b998-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b998-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b998-112">Example</span></span>  
 <span data-ttu-id="5b998-113">O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="5b998-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="5b998-114">O exemplo executa uma consulta LINQ to entidades que usa o método de <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> para retornar todos os produtos para que a diferença entre `SellEndDate` e `SellStartDate` é menor que 365 dias:</span><span class="sxs-lookup"><span data-stu-id="5b998-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="5b998-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b998-115">Example</span></span>  
 <span data-ttu-id="5b998-116">O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="5b998-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="5b998-117">O exemplo chama o método agregado de <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> diretamente para retornar o desvio padrão de subtotais de `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="5b998-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="5b998-118">Observe que <xref:System.Data.Objects.ObjectQuery%601> é passado para a função, que permite que é chamado sem ser parte de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="5b998-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5b998-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b998-119">See Also</span></span>  
 [<span data-ttu-id="5b998-120">Chamando funções em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5b998-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="5b998-121">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5b998-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
