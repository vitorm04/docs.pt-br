---
title: Cláusula Take While
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869662"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="00b55-102">Cláusula Take While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00b55-102">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="00b55-103">Inclui elementos em uma coleção desde que uma condição especificada seja `true` e ignore os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="00b55-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00b55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00b55-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="00b55-105">Partes</span><span class="sxs-lookup"><span data-stu-id="00b55-105">Parts</span></span>  
  
|<span data-ttu-id="00b55-106">Termo</span><span class="sxs-lookup"><span data-stu-id="00b55-106">Term</span></span>|<span data-ttu-id="00b55-107">Definição</span><span class="sxs-lookup"><span data-stu-id="00b55-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="00b55-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="00b55-108">Required.</span></span> <span data-ttu-id="00b55-109">Uma expressão que representa uma condição para os elementos de teste.</span><span class="sxs-lookup"><span data-stu-id="00b55-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="00b55-110">A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliado como um `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="00b55-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00b55-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="00b55-111">Remarks</span></span>  

 <span data-ttu-id="00b55-112">A `Take While` cláusula inclui elementos do início de um resultado da consulta até que o `expression` retorno fornecido `false` .</span><span class="sxs-lookup"><span data-stu-id="00b55-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="00b55-113">Após o `expression` retorno `false` , a consulta irá ignorar todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="00b55-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="00b55-114">O `expression` é ignorado para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="00b55-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="00b55-115">A `Take While` cláusula é diferente da cláusula, pois `Where` a `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atenda a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="00b55-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="00b55-116">A `Take While` cláusula só inclui elementos até a primeira vez que a condição não for satisfeita.</span><span class="sxs-lookup"><span data-stu-id="00b55-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="00b55-117">A `Take While` cláusula é mais útil quando você está trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="00b55-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b55-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00b55-118">Example</span></span>  

 <span data-ttu-id="00b55-119">O exemplo de código a seguir usa a `Take While` cláusula para recuperar resultados até que o primeiro cliente sem nenhum pedido seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="00b55-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="00b55-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="00b55-120">See also</span></span>

- [<span data-ttu-id="00b55-121">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00b55-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="00b55-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="00b55-122">Queries</span></span>](index.md)
- [<span data-ttu-id="00b55-123">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="00b55-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="00b55-124">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="00b55-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="00b55-125">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="00b55-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="00b55-126">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="00b55-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="00b55-127">Cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="00b55-127">Where Clause</span></span>](where-clause.md)
