---
title: 'Exceções: a função raise (F#)'
description: Saiba como a função F# "raise" é usada para indicar que um erro ou uma condição excepcional ocorreu.
ms.date: 05/16/2016
ms.openlocfilehash: 537d274659d29404380bfdd56310ac267372bb98
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43778253"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="69b46-103">Exceções: a função raise</span><span class="sxs-lookup"><span data-stu-id="69b46-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="69b46-104">O `raise` função é usada para indicar que um erro ou uma condição excepcional ocorreu.</span><span class="sxs-lookup"><span data-stu-id="69b46-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="69b46-105">Informações sobre o erro são capturadas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="69b46-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="69b46-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69b46-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="69b46-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="69b46-107">Remarks</span></span>

<span data-ttu-id="69b46-108">O `raise` função gera um objeto de exceção e inicia uma processo de desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="69b46-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="69b46-109">O processo de desenrolamento de pilha é gerenciado pelo common language runtime (CLR), portanto, o comportamento desse processo é o mesmo que ele esteja em qualquer outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="69b46-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="69b46-110">O processo de desenrolamento de pilha é uma pesquisa por um manipulador de exceção que coincide com a exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="69b46-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="69b46-111">A pesquisa inicia no atual `try...with` expressão, se houver um.</span><span class="sxs-lookup"><span data-stu-id="69b46-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="69b46-112">Cada padrão no `with` bloco estiver marcado, em ordem.</span><span class="sxs-lookup"><span data-stu-id="69b46-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="69b46-113">Quando um manipulador de exceção correspondente for encontrado, a exceção será considerada tratada; Caso contrário, a pilha é desenrolada e `with` blocos de cadeia de chamadas são verificados até que um manipulador correspondente for encontrado.</span><span class="sxs-lookup"><span data-stu-id="69b46-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="69b46-114">Qualquer `finally` blocos que são encontrados na cadeia de chamadas também são executados em sequência, conforme a pilha esvazia.</span><span class="sxs-lookup"><span data-stu-id="69b46-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="69b46-115">O `raise` função é o equivalente de `throw` em c# ou C++.</span><span class="sxs-lookup"><span data-stu-id="69b46-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="69b46-116">Use `reraise` em um manipulador catch para propagar a mesma exceção na cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="69b46-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="69b46-117">Os exemplos de código a seguir ilustram o uso do `raise` função para gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="69b46-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="69b46-118">O `raise` função também pode ser usada para gerar exceções .NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="69b46-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="69b46-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69b46-119">See also</span></span>

- [<span data-ttu-id="69b46-120">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="69b46-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="69b46-121">Tipos de Exceção</span><span class="sxs-lookup"><span data-stu-id="69b46-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="69b46-122">Exceções: a expressão `try...with`</span><span class="sxs-lookup"><span data-stu-id="69b46-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="69b46-123">Exceções: a expressão `try...finally`</span><span class="sxs-lookup"><span data-stu-id="69b46-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="69b46-124">Exceções: a função `failwith`</span><span class="sxs-lookup"><span data-stu-id="69b46-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="69b46-125">Exceções: a função `invalidArg`</span><span class="sxs-lookup"><span data-stu-id="69b46-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
