---
title: 'Exceções: a função raise'
description: Saiba como a F# função ' raise ' é usada para indicar que ocorreu um erro ou uma condição excepcional.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630292"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="a6098-103">Exceções: a função raise</span><span class="sxs-lookup"><span data-stu-id="a6098-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="a6098-104">A `raise` função é usada para indicar que ocorreu um erro ou uma condição excepcional.</span><span class="sxs-lookup"><span data-stu-id="a6098-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="a6098-105">As informações sobre o erro são capturadas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="a6098-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6098-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6098-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="a6098-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6098-107">Remarks</span></span>

<span data-ttu-id="a6098-108">A `raise` função gera um objeto de exceção e inicia um processo de desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="a6098-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="a6098-109">O processo de desenrolamento de pilha é gerenciado pelo Common Language Runtime (CLR), portanto, o comportamento desse processo é o mesmo que em qualquer outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="a6098-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="a6098-110">O processo de desenrolamento de pilha é uma pesquisa por um manipulador de exceção que corresponda à exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="a6098-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="a6098-111">A pesquisa começa na expressão atual `try...with` , se houver uma.</span><span class="sxs-lookup"><span data-stu-id="a6098-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="a6098-112">Cada padrão no `with` bloco é verificado, em ordem.</span><span class="sxs-lookup"><span data-stu-id="a6098-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="a6098-113">Quando um manipulador de exceção correspondente é encontrado, a exceção é considerada tratada; caso contrário, a pilha será desbobinada e `with` bloqueará a cadeia de chamadas será verificada até que um manipulador correspondente seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="a6098-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="a6098-114">Todos `finally` os blocos encontrados na cadeia de chamadas também são executados em sequência à medida que a pilha se desenrola.</span><span class="sxs-lookup"><span data-stu-id="a6098-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="a6098-115">A `raise` função é o equivalente de `throw` em C# ou C++.</span><span class="sxs-lookup"><span data-stu-id="a6098-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="a6098-116">Use `reraise` em um manipulador catch para propagar a mesma exceção da cadeia de chamadas.</span><span class="sxs-lookup"><span data-stu-id="a6098-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="a6098-117">Os exemplos de código a seguir ilustram o `raise` uso da função para gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a6098-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="a6098-118">A `raise` função também pode ser usada para gerar exceções .net, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a6098-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="a6098-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6098-119">See also</span></span>

- [<span data-ttu-id="a6098-120">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="a6098-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="a6098-121">Tipos de Exceção</span><span class="sxs-lookup"><span data-stu-id="a6098-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="a6098-122">Exceções: A `try...with` expressão</span><span class="sxs-lookup"><span data-stu-id="a6098-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="a6098-123">Exceções: A `try...finally` expressão</span><span class="sxs-lookup"><span data-stu-id="a6098-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="a6098-124">Exceções: A `failwith` função</span><span class="sxs-lookup"><span data-stu-id="a6098-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="a6098-125">Exceções: A `invalidArg` função</span><span class="sxs-lookup"><span data-stu-id="a6098-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
