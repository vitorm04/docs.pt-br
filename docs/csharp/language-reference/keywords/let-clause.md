---
title: Cláusula let – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173582"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="3a000-102">Cláusula let (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3a000-102">let clause (C# Reference)</span></span>

<span data-ttu-id="3a000-103">Em uma expressão de consulta, às vezes é útil armazenar o resultado de uma subexpressão para usá-lo em cláusulas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="3a000-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="3a000-104">É possível fazer isso com a palavra-chave `let`, que cria uma nova variável de intervalo e a inicializa com o resultado da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="3a000-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="3a000-105">Depois de inicializado com um valor, a variável de intervalo não pode ser usada para armazenar outro valor.</span><span class="sxs-lookup"><span data-stu-id="3a000-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="3a000-106">No entanto, se a variável de intervalo mantiver um tipo passível de consulta, ela poderá ser consultada.</span><span class="sxs-lookup"><span data-stu-id="3a000-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="3a000-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a000-107">Example</span></span>

<span data-ttu-id="3a000-108">No exemplo a seguir, `let` é usado de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="3a000-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="3a000-109">Para criar um tipo enumerável que pode ser pesquisado por si só.</span><span class="sxs-lookup"><span data-stu-id="3a000-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="3a000-110">Para permitir que a consulta chame `ToLower` apenas uma vez na variável de intervalo `word`.</span><span class="sxs-lookup"><span data-stu-id="3a000-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="3a000-111">Sem usar `let`, seria necessário chamar `ToLower` em cada predicado na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="3a000-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="3a000-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a000-112">See also</span></span>

- [<span data-ttu-id="3a000-113">C# Referência</span><span class="sxs-lookup"><span data-stu-id="3a000-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3a000-114">Palavras-chave de consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3a000-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="3a000-115">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="3a000-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="3a000-116">Consulta Integrada ao Idioma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3a000-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="3a000-117">Manipular exceções em expressões de consultas</span><span class="sxs-lookup"><span data-stu-id="3a000-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
