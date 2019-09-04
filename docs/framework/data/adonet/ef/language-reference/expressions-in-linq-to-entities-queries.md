---
title: Expressões em consultas LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250981"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="b2075-102">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b2075-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="b2075-103">Uma expressão é um fragmento de código que pode ser avaliado como um único valor, objeto, método ou namespace.</span><span class="sxs-lookup"><span data-stu-id="b2075-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="b2075-104">As expressões podem conter um valor literal, uma chamada de método, um operador e seus operandos ou um nome simples.</span><span class="sxs-lookup"><span data-stu-id="b2075-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="b2075-105">Os nomes simples podem ser o nome de uma variável, um membro de tipo, um parâmetro de método, um namespace ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="b2075-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="b2075-106">As expressões podem usar operadores que, por sua vez, usam outras expressões como parâmetros ou chamadas de métodos cujos parâmetros são, por sua vez, outras chamadas de métodos.</span><span class="sxs-lookup"><span data-stu-id="b2075-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="b2075-107">Portanto, as expressões podem variar de simples a muito complexas.</span><span class="sxs-lookup"><span data-stu-id="b2075-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="b2075-108">Em consultas LINQ to Entities, as expressões podem conter qualquer coisa permitida pelos tipos dentro <xref:System.Linq.Expressions> do namespace, incluindo expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="b2075-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="b2075-109">As expressões que podem ser usadas em LINQ to Entities consultas são um superconjunto das expressões que podem ser usadas para consultar o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2075-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="b2075-110">As expressões que fazem parte das consultas [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] no são limitadas às operações `ObjectQuery<T>` com suporte no e na fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="b2075-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="b2075-111">No exemplo a seguir, a comparação na cláusula `Where` é uma expressão:</span><span class="sxs-lookup"><span data-stu-id="b2075-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="b2075-112">Construções de linguagem específicas, C# `unchecked`como, não têm significado em LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b2075-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2075-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b2075-113">In This Section</span></span>  
 [<span data-ttu-id="b2075-114">Expressões constantes</span><span class="sxs-lookup"><span data-stu-id="b2075-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="b2075-115">Expressões de comparação</span><span class="sxs-lookup"><span data-stu-id="b2075-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="b2075-116">Comparações nulas</span><span class="sxs-lookup"><span data-stu-id="b2075-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="b2075-117">Expressões de inicialização</span><span class="sxs-lookup"><span data-stu-id="b2075-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="b2075-118">Relações, propriedades de navegação e chaves estrangeiras</span><span class="sxs-lookup"><span data-stu-id="b2075-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="b2075-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2075-119">See also</span></span>

- [<span data-ttu-id="b2075-120">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b2075-120">ADO.NET Entity Framework</span></span>](../index.md)
