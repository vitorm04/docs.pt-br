---
title: Cláusula Skip While
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: af722f7aee021f244b411cdc61619b7de3c20607
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866229"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="93be4-102">Ignorar cláusula While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93be4-102">Skip While Clause (Visual Basic)</span></span>

<span data-ttu-id="93be4-103">Ignora os elementos em uma coleção, desde que uma condição especificada seja `true` e, em seguida, retorne os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="93be4-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93be4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93be4-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="93be4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="93be4-105">Parts</span></span>  
  
|<span data-ttu-id="93be4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="93be4-106">Term</span></span>|<span data-ttu-id="93be4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="93be4-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="93be4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="93be4-108">Required.</span></span> <span data-ttu-id="93be4-109">Uma expressão que representa uma condição para os elementos de teste.</span><span class="sxs-lookup"><span data-stu-id="93be4-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="93be4-110">A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliado como um `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="93be4-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93be4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="93be4-111">Remarks</span></span>  

 <span data-ttu-id="93be4-112">A `Skip While` cláusula ignora os elementos do início de um resultado da consulta até que o `expression` retorno fornecido `false` .</span><span class="sxs-lookup"><span data-stu-id="93be4-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="93be4-113">Após o `expression` retorno `false` , a consulta retorna todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="93be4-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="93be4-114">O `expression` é ignorado para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="93be4-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="93be4-115">A `Skip While` cláusula é diferente da cláusula, pois `Where` a `Where` cláusula pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="93be4-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="93be4-116">A `Skip While` cláusula exclui elementos somente até a primeira vez que a condição não for satisfeita.</span><span class="sxs-lookup"><span data-stu-id="93be4-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="93be4-117">A `Skip While` cláusula é mais útil quando você está trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="93be4-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="93be4-118">Você pode ignorar um número específico de resultados do início de um resultado de consulta usando a `Skip` cláusula.</span><span class="sxs-lookup"><span data-stu-id="93be4-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93be4-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="93be4-119">Example</span></span>  

 <span data-ttu-id="93be4-120">O exemplo de código a seguir usa a `Skip While` cláusula para ignorar os resultados até que o primeiro cliente do Estados Unidos seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="93be4-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="93be4-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="93be4-121">See also</span></span>

- [<span data-ttu-id="93be4-122">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93be4-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="93be4-123">Consultas</span><span class="sxs-lookup"><span data-stu-id="93be4-123">Queries</span></span>](index.md)
- [<span data-ttu-id="93be4-124">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="93be4-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="93be4-125">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="93be4-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="93be4-126">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="93be4-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="93be4-127">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="93be4-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="93be4-128">Cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="93be4-128">Where Clause</span></span>](where-clause.md)
