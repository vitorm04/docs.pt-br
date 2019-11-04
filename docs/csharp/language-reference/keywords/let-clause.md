---
title: Cláusula let – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422693"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="4013d-102">Cláusula let (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4013d-102">let clause (C# Reference)</span></span>

<span data-ttu-id="4013d-103">Em uma expressão de consulta, às vezes é útil armazenar o resultado de uma subexpressão para usá-lo em cláusulas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="4013d-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="4013d-104">É possível fazer isso com a palavra-chave `let`, que cria uma nova variável de intervalo e a inicializa com o resultado da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="4013d-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="4013d-105">Depois de inicializado com um valor, a variável de intervalo não pode ser usada para armazenar outro valor.</span><span class="sxs-lookup"><span data-stu-id="4013d-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="4013d-106">No entanto, se a variável de intervalo mantiver um tipo passível de consulta, ela poderá ser consultada.</span><span class="sxs-lookup"><span data-stu-id="4013d-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="4013d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4013d-107">Example</span></span>

<span data-ttu-id="4013d-108">No exemplo a seguir, `let` é usado de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="4013d-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="4013d-109">Para criar um tipo enumerável que pode ser pesquisado por si só.</span><span class="sxs-lookup"><span data-stu-id="4013d-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="4013d-110">Para permitir que a consulta chame `ToLower` apenas uma vez na variável de intervalo `word`.</span><span class="sxs-lookup"><span data-stu-id="4013d-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="4013d-111">Sem usar `let`, seria necessário chamar `ToLower` em cada predicado na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="4013d-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="4013d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4013d-112">See also</span></span>

- [<span data-ttu-id="4013d-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4013d-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="4013d-114">Palavras-chave de Consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4013d-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="4013d-115">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="4013d-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="4013d-116">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="4013d-116">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
- [<span data-ttu-id="4013d-117">Manipular exceções em expressões de consultas</span><span class="sxs-lookup"><span data-stu-id="4013d-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
