---
title: Consulte expressões (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: ca6b79b4b3d3326a74780345decf58367596adb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175597"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="559ed-102">Consulte expressões (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="559ed-102">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="559ed-103">Uma expressão de consulta combina muitos diferentes operadores de consulta em uma única sintaxe.</span><span class="sxs-lookup"><span data-stu-id="559ed-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="559ed-104">fornece vários tipos de expressões, incluindo as seguintes: [literais](literals-entity-sql.md), [parâmetros](parameters-entity-sql.md), [variáveis](variables-entity-sql.md), operadores, [funções](functions-entity-sql.md), operadores de conjunto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="559ed-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="559ed-105">Para obter mais informações, consulte [referência de Entity SQL](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="559ed-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="559ed-106">Cláusulas</span><span class="sxs-lookup"><span data-stu-id="559ed-106">Clauses</span></span>  

 <span data-ttu-id="559ed-107">Uma expressão de consulta é composta de uma série de cláusulas que operações sucessivas aplicam a uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="559ed-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="559ed-108">Elas se baseiam nas mesmas cláusulas encontradas em uma instrução SQL SELECT padrão: [selecionar](select-entity-sql.md), [de](from-entity-sql.md), [onde](where-entity-sql.md), [Agrupar por](group-by-entity-sql.md), [having](having-entity-sql.md)e [ordenar por](order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="559ed-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="559ed-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="559ed-109">Scope</span></span>  

 <span data-ttu-id="559ed-110">Nomes definidos na cláusula são apresentados no escopo por ordem de aparência, da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="559ed-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="559ed-111">Na lista JOIN, as expressões podem referir-se nomes definidos anteriormente na lista.</span><span class="sxs-lookup"><span data-stu-id="559ed-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="559ed-112">As propriedades públicas de elementos identificadas na cláusula não são adicionadas ao escopo: Sempre devem ser referenciados com o nome qualificado alias-.</span><span class="sxs-lookup"><span data-stu-id="559ed-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="559ed-113">Normalmente, todas as partes da expressão selecionar são considerados dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="559ed-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="559ed-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="559ed-114">See also</span></span>

- [<span data-ttu-id="559ed-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="559ed-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
