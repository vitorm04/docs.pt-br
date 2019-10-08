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
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004703"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="adaec-102">Ignorar cláusula While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adaec-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="adaec-103">Ignora os elementos em uma coleção, desde que uma condição especificada seja `true` e, em seguida, retorne os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="adaec-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adaec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adaec-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="adaec-105">Partes</span><span class="sxs-lookup"><span data-stu-id="adaec-105">Parts</span></span>  
  
|<span data-ttu-id="adaec-106">Termo</span><span class="sxs-lookup"><span data-stu-id="adaec-106">Term</span></span>|<span data-ttu-id="adaec-107">Definição</span><span class="sxs-lookup"><span data-stu-id="adaec-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="adaec-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="adaec-108">Required.</span></span> <span data-ttu-id="adaec-109">Uma expressão que representa uma condição para os elementos de teste.</span><span class="sxs-lookup"><span data-stu-id="adaec-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="adaec-110">A expressão deve retornar um valor `Boolean` ou um equivalente funcional, como um `Integer` a ser avaliado como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="adaec-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adaec-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="adaec-111">Remarks</span></span>  
 <span data-ttu-id="adaec-112">A cláusula `Skip While` ignora os elementos do início de um resultado da consulta até que o `expression` fornecido retorne `false`.</span><span class="sxs-lookup"><span data-stu-id="adaec-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="adaec-113">Depois que `expression` retorna `false`, a consulta retorna todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="adaec-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="adaec-114">O `expression` é ignorado para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="adaec-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="adaec-115">A cláusula `Skip While` difere da cláusula `Where`, na qual a cláusula `Where` pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="adaec-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="adaec-116">A cláusula `Skip While` exclui elementos somente até a primeira vez em que a condição não for satisfeita.</span><span class="sxs-lookup"><span data-stu-id="adaec-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="adaec-117">A cláusula `Skip While` é mais útil quando você está trabalhando com um resultado de consulta ordenada.</span><span class="sxs-lookup"><span data-stu-id="adaec-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="adaec-118">Você pode ignorar um número específico de resultados do início de um resultado de consulta usando a cláusula `Skip`.</span><span class="sxs-lookup"><span data-stu-id="adaec-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adaec-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adaec-119">Example</span></span>  
 <span data-ttu-id="adaec-120">O exemplo de código a seguir usa a cláusula `Skip While` para ignorar os resultados até que o primeiro cliente do Estados Unidos seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="adaec-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="adaec-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adaec-121">See also</span></span>

- [<span data-ttu-id="adaec-122">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="adaec-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="adaec-123">Consultas</span><span class="sxs-lookup"><span data-stu-id="adaec-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="adaec-124">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="adaec-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="adaec-125">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="adaec-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="adaec-126">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="adaec-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="adaec-127">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="adaec-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="adaec-128">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="adaec-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
