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
ms.openlocfilehash: 080a106fc1deeb54165511ed03d7c7c5d2060f21
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818743"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="35815-102">Cláusula Take While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35815-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="35815-103">Inclui elementos em uma coleção, desde que uma condição especificada seja `true` e ignora os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="35815-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35815-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35815-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="35815-105">Partes</span><span class="sxs-lookup"><span data-stu-id="35815-105">Parts</span></span>  
  
|<span data-ttu-id="35815-106">Termo</span><span class="sxs-lookup"><span data-stu-id="35815-106">Term</span></span>|<span data-ttu-id="35815-107">Definição</span><span class="sxs-lookup"><span data-stu-id="35815-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="35815-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="35815-108">Required.</span></span> <span data-ttu-id="35815-109">Uma expressão que representa uma condição para testar elementos.</span><span class="sxs-lookup"><span data-stu-id="35815-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="35815-110">A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliada como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="35815-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35815-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="35815-111">Remarks</span></span>  
 <span data-ttu-id="35815-112">O `Take While` cláusula inclui elementos desde o início de um resultado de consulta até que o fornecido `expression` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="35815-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="35815-113">Após o `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="35815-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="35815-114">O `expression` é ignorado para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="35815-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="35815-115">O `Take While` cláusula difere de `Where` cláusula em que o `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atendam a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="35815-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="35815-116">O `Take While` cláusula inclui elementos apenas até a primeira vez em que a condição não for atendida.</span><span class="sxs-lookup"><span data-stu-id="35815-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="35815-117">O `Take While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="35815-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35815-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35815-118">Example</span></span>  
 <span data-ttu-id="35815-119">O seguinte exemplo de código usa o `Take While` cláusula para recuperar os resultados até que o primeiro cliente sem qualquer pedidos é encontrado.</span><span class="sxs-lookup"><span data-stu-id="35815-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="35815-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35815-120">See also</span></span>

- [<span data-ttu-id="35815-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35815-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="35815-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="35815-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="35815-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="35815-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="35815-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="35815-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="35815-125">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="35815-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="35815-126">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="35815-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="35815-127">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="35815-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
