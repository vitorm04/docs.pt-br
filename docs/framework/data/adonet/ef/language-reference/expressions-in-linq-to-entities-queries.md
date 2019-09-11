---
title: Expressões em consultas LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: e625ac3968542c65e737093c0ac292de4c2ffa37
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854465"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="5b0ee-102">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5b0ee-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="5b0ee-103">Uma expressão é um fragmento de código que pode ser avaliado como um único valor, objeto, método ou namespace.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="5b0ee-104">As expressões podem conter um valor literal, uma chamada de método, um operador e seus operandos ou um nome simples.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="5b0ee-105">Os nomes simples podem ser o nome de uma variável, um membro de tipo, um parâmetro de método, um namespace ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="5b0ee-106">As expressões podem usar operadores que, por sua vez, usam outras expressões como parâmetros ou chamadas de métodos cujos parâmetros são, por sua vez, outras chamadas de métodos.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="5b0ee-107">Portanto, as expressões podem variar de simples a muito complexas.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="5b0ee-108">Em consultas LINQ to Entities, as expressões podem conter qualquer coisa permitida pelos tipos dentro <xref:System.Linq.Expressions> do namespace, incluindo expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="5b0ee-109">As expressões que podem ser usadas em LINQ to Entities consultas são um superconjunto das expressões que podem ser usadas para consultar o Entity Framework. as expressões que fazem parte das consultas no Entity Framework são limitadas às operações com `ObjectQuery<T>` suporte pelo e a fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="5b0ee-110">No exemplo a seguir, a comparação na cláusula `Where` é uma expressão:</span><span class="sxs-lookup"><span data-stu-id="5b0ee-110">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="5b0ee-111">Construções de linguagem específicas, C# `unchecked`como, não têm significado em LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="5b0ee-111">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b0ee-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5b0ee-112">In This Section</span></span>  
 [<span data-ttu-id="5b0ee-113">Expressões constantes</span><span class="sxs-lookup"><span data-stu-id="5b0ee-113">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="5b0ee-114">Expressões de comparação</span><span class="sxs-lookup"><span data-stu-id="5b0ee-114">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="5b0ee-115">Comparações nulas</span><span class="sxs-lookup"><span data-stu-id="5b0ee-115">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="5b0ee-116">Expressões de inicialização</span><span class="sxs-lookup"><span data-stu-id="5b0ee-116">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="5b0ee-117">Relações, propriedades de navegação e chaves estrangeiras</span><span class="sxs-lookup"><span data-stu-id="5b0ee-117">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="5b0ee-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b0ee-118">See also</span></span>

- [<span data-ttu-id="5b0ee-119">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5b0ee-119">ADO.NET Entity Framework</span></span>](../index.md)
