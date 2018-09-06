---
title: Cláusula Take While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 181cc641bb12329c898cc3bb226ea49f0836e979
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736400"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="53fc6-102">Cláusula Take While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53fc6-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="53fc6-103">Inclui elementos em uma coleção, desde que uma condição especificada seja `true` e ignora os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="53fc6-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53fc6-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="53fc6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="53fc6-105">Parts</span></span>  
  
|<span data-ttu-id="53fc6-106">Termo</span><span class="sxs-lookup"><span data-stu-id="53fc6-106">Term</span></span>|<span data-ttu-id="53fc6-107">Definição</span><span class="sxs-lookup"><span data-stu-id="53fc6-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="53fc6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="53fc6-108">Required.</span></span> <span data-ttu-id="53fc6-109">Uma expressão que representa uma condição para testar elementos.</span><span class="sxs-lookup"><span data-stu-id="53fc6-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="53fc6-110">A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliada como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="53fc6-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53fc6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="53fc6-111">Remarks</span></span>  
 <span data-ttu-id="53fc6-112">O `Take While` cláusula inclui elementos desde o início de um resultado de consulta até que o fornecido `expression` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="53fc6-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="53fc6-113">Após o `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="53fc6-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="53fc6-114">O `expression` é ignorado para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="53fc6-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="53fc6-115">O `Take While` cláusula difere de `Where` cláusula em que o `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atendam a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="53fc6-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="53fc6-116">O `Take While` cláusula inclui elementos apenas até a primeira vez em que a condição não for atendida.</span><span class="sxs-lookup"><span data-stu-id="53fc6-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="53fc6-117">O `Take While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="53fc6-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53fc6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53fc6-118">Example</span></span>  
 <span data-ttu-id="53fc6-119">O seguinte exemplo de código usa o `Take While` cláusula para recuperar os resultados até que o primeiro cliente sem qualquer pedidos é encontrado.</span><span class="sxs-lookup"><span data-stu-id="53fc6-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="53fc6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53fc6-120">See Also</span></span>  
 [<span data-ttu-id="53fc6-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53fc6-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="53fc6-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="53fc6-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="53fc6-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="53fc6-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="53fc6-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="53fc6-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="53fc6-125">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="53fc6-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="53fc6-126">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="53fc6-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="53fc6-127">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="53fc6-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
