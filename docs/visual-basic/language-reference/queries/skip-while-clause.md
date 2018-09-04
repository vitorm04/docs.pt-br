---
title: Ignorar cláusula While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: a3c0749560d8cea1e46d96298347ce54f0bf9185
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537166"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="1caa4-102">Ignorar cláusula While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1caa4-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="1caa4-103">Ignora elementos em uma coleção, desde que uma condição especificada seja `true` e, em seguida, retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="1caa4-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1caa4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1caa4-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1caa4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1caa4-105">Parts</span></span>  
  
|<span data-ttu-id="1caa4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="1caa4-106">Term</span></span>|<span data-ttu-id="1caa4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="1caa4-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="1caa4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1caa4-108">Required.</span></span> <span data-ttu-id="1caa4-109">Uma expressão que representa uma condição para testar elementos.</span><span class="sxs-lookup"><span data-stu-id="1caa4-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="1caa4-110">A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliada como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1caa4-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1caa4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1caa4-111">Remarks</span></span>  
 <span data-ttu-id="1caa4-112">O `Skip While` cláusula ignora elementos desde o início de um resultado de consulta até que o fornecido `expression` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="1caa4-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="1caa4-113">Após `expression` retorna `false`, a consulta retorna todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="1caa4-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="1caa4-114">O `expression` é ignorado para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="1caa4-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="1caa4-115">O `Skip While` cláusula difere de `Where` cláusula em que o `Where` cláusula pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma determinada condição.</span><span class="sxs-lookup"><span data-stu-id="1caa4-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="1caa4-116">O `Skip While` cláusula excluir elementos apenas até a primeira vez em que a condição não for atendida.</span><span class="sxs-lookup"><span data-stu-id="1caa4-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="1caa4-117">O `Skip While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="1caa4-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="1caa4-118">Você pode ignorar um número específico de resultados desde o início de uma consulta usando o `Skip` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1caa4-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1caa4-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1caa4-119">Example</span></span>  
 <span data-ttu-id="1caa4-120">O seguinte exemplo de código usa o `Skip While` cláusula para ignorar resultados até que o primeiro cliente dos Estados Unidos é encontrado.</span><span class="sxs-lookup"><span data-stu-id="1caa4-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1caa4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1caa4-121">See Also</span></span>  
 [<span data-ttu-id="1caa4-122">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1caa4-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1caa4-123">Consultas</span><span class="sxs-lookup"><span data-stu-id="1caa4-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="1caa4-124">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="1caa4-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="1caa4-125">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="1caa4-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1caa4-126">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="1caa4-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="1caa4-127">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="1caa4-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="1caa4-128">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="1caa4-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
