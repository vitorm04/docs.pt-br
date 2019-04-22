---
title: Expressões em consultas LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 234b3059f9109c23b8ecae4da37e15f7f094fbd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203230"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="1aa71-102">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1aa71-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="1aa71-103">Uma expressão é um fragmento de código que pode ser avaliado como um único valor, objeto, método ou namespace.</span><span class="sxs-lookup"><span data-stu-id="1aa71-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="1aa71-104">As expressões podem conter um valor literal, uma chamada de método, um operador e seus operandos ou um nome simples.</span><span class="sxs-lookup"><span data-stu-id="1aa71-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="1aa71-105">Os nomes simples podem ser o nome de uma variável, um membro de tipo, um parâmetro de método, um namespace ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="1aa71-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="1aa71-106">As expressões podem usar operadores que, por sua vez, usam outras expressões como parâmetros ou chamadas de métodos cujos parâmetros são, por sua vez, outras chamadas de métodos.</span><span class="sxs-lookup"><span data-stu-id="1aa71-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="1aa71-107">Portanto, as expressões podem variar de simples a muito complexas.</span><span class="sxs-lookup"><span data-stu-id="1aa71-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="1aa71-108">Na [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consultas, as expressões podem conter qualquer coisa permitida pelos tipos dentro de <xref:System.Linq.Expressions> namespace, incluindo expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="1aa71-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="1aa71-109">A expressões que podem ser usadas em consultas [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] são um superconjunto das expressões que podem ser usadas para consultar o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1aa71-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="1aa71-110">Expressões que fazem parte de consultas em relação a [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] são limitadas a operações suportadas por `ObjectQuery<T>` e fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="1aa71-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="1aa71-111">No exemplo a seguir, a comparação na cláusula `Where` é uma expressão:</span><span class="sxs-lookup"><span data-stu-id="1aa71-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="1aa71-112">Os constructos de linguagens específicos, como `unchecked` do C#, não têm significado no [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1aa71-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1aa71-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1aa71-113">In This Section</span></span>  
 [<span data-ttu-id="1aa71-114">Expressões constantes</span><span class="sxs-lookup"><span data-stu-id="1aa71-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="1aa71-115">Expressões de comparação</span><span class="sxs-lookup"><span data-stu-id="1aa71-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="1aa71-116">Comparações nulas</span><span class="sxs-lookup"><span data-stu-id="1aa71-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="1aa71-117">Expressões de inicialização</span><span class="sxs-lookup"><span data-stu-id="1aa71-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="1aa71-118">Relações, as propriedades de navegação e chaves estrangeiras</span><span class="sxs-lookup"><span data-stu-id="1aa71-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="1aa71-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1aa71-119">See also</span></span>

- [<span data-ttu-id="1aa71-120">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1aa71-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
