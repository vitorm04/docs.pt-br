---
description: Cláusula let – Referência de C#
title: Cláusula let – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139587"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="ee2c7-103">Cláusula let (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ee2c7-103">let clause (C# Reference)</span></span>

<span data-ttu-id="ee2c7-104">Em uma expressão de consulta, às vezes é útil armazenar o resultado de uma subexpressão para usá-lo em cláusulas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-104">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="ee2c7-105">É possível fazer isso com a palavra-chave `let`, que cria uma nova variável de intervalo e a inicializa com o resultado da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-105">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="ee2c7-106">Depois de inicializado com um valor, a variável de intervalo não pode ser usada para armazenar outro valor.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-106">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="ee2c7-107">No entanto, se a variável de intervalo mantiver um tipo passível de consulta, ela poderá ser consultada.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-107">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="ee2c7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee2c7-108">Example</span></span>

<span data-ttu-id="ee2c7-109">No exemplo a seguir, `let` é usado de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="ee2c7-109">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="ee2c7-110">Para criar um tipo enumerável que pode ser pesquisado por si só.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-110">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="ee2c7-111">Para permitir que a consulta chame `ToLower` apenas uma vez na variável de intervalo `word`.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-111">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="ee2c7-112">Sem usar `let`, seria necessário chamar `ToLower` em cada predicado na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="ee2c7-112">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="ee2c7-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee2c7-113">See also</span></span>

- [<span data-ttu-id="ee2c7-114">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="ee2c7-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ee2c7-115">Palavras-chave de consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ee2c7-115">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="ee2c7-116">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="ee2c7-116">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="ee2c7-117">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="ee2c7-117">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="ee2c7-118">Tratar exceções em expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="ee2c7-118">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
