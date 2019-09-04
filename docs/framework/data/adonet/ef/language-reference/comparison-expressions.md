---
title: Expressões de comparação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d0926bb1a0e35caa058f268f0a0c414e805a8674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251167"
---
# <a name="comparison-expressions"></a><span data-ttu-id="3f505-102">Expressões de comparação</span><span class="sxs-lookup"><span data-stu-id="3f505-102">Comparison Expressions</span></span>
<span data-ttu-id="3f505-103">Uma expressão de comparação verifica se um valor, um valor de propriedade, ou um resultado constante do método sejam iguais, não iguais, maior do que, ou menor que outro valor.</span><span class="sxs-lookup"><span data-stu-id="3f505-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="3f505-104">Se uma comparação específica não for válida para LINQ to Entities, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="3f505-104">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="3f505-105">Todas as comparações, explícita e implícita, exigem que todos os componentes são comparáveis na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3f505-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="3f505-106">As expressões de comparação são usados nas cláusulas de `Where` para os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="3f505-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="3f505-107">O exemplo a seguir na sintaxe da expressão de consulta a seguir mostra uma consulta que retorna os resultados onde o número de ordem de venda é igual a “SO43663”:</span><span class="sxs-lookup"><span data-stu-id="3f505-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="3f505-108">O exemplo a seguir na sintaxe da consulta com base em método mostra uma consulta que retorna os resultados onde o número de ordem de venda é igual a “SO43663”:</span><span class="sxs-lookup"><span data-stu-id="3f505-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="3f505-109">O exemplo a seguir na sintaxe da expressão de consulta a seguir mostra uma consulta que retorna informações de venda ordem de onde a data de enviar é igual ao 8 de julho de 2001:</span><span class="sxs-lookup"><span data-stu-id="3f505-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="3f505-110">O exemplo a seguir na sintaxe da consulta com base em método mostra uma consulta que retorna informações de venda ordem de onde a data de enviar é igual ao 8 de julho de 2001:</span><span class="sxs-lookup"><span data-stu-id="3f505-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="3f505-111">Expressões que produzem uma constante são convertidas no servidor, e em qualquer tentativa para fazer a avaliação local são executadas.</span><span class="sxs-lookup"><span data-stu-id="3f505-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="3f505-112">O exemplo a seguir usa uma expressão na cláusula `Where` que produz uma constante.</span><span class="sxs-lookup"><span data-stu-id="3f505-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="3f505-113">LINQ to Entities não dá suporte ao uso de uma classe de usuário como uma constante.</span><span class="sxs-lookup"><span data-stu-id="3f505-113">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="3f505-114">No entanto, uma referência de propriedade em uma classe de usuário é considerada uma constante, e será convertida em uma expressão constante de árvore de comando e executada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3f505-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="3f505-115">Os métodos que retornam uma expressão constante não são suportados.</span><span class="sxs-lookup"><span data-stu-id="3f505-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="3f505-116">O exemplo a seguir contém um método na cláusula `Where` que retorna uma constante.</span><span class="sxs-lookup"><span data-stu-id="3f505-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="3f505-117">Este exemplo irá acionar uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3f505-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="3f505-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f505-118">See also</span></span>

- [<span data-ttu-id="3f505-119">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3f505-119">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
