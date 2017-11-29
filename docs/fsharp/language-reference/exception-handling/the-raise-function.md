---
title: "Exceções: a função raise (F#)"
description: "Saiba como a F # 'raise' função é usada para indicar que ocorreu um erro ou uma condição excepcional."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="9bd9c-104">Exceções: a função raise</span><span class="sxs-lookup"><span data-stu-id="9bd9c-104">Exceptions: the raise Function</span></span>

<span data-ttu-id="9bd9c-105">O `raise` função é usada para indicar que ocorreu um erro ou uma condição excepcional.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-105">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="9bd9c-106">Informações sobre o erro são capturadas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-106">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="9bd9c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd9c-107">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="9bd9c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd9c-108">Remarks</span></span>
<span data-ttu-id="9bd9c-109">O `raise` função gera um objeto de exceção e inicia uma processo de desenrolamento da pilha.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-109">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="9bd9c-110">O processo de desenrolamento de pilha é gerenciado pelo common language runtime (CLR), o comportamento desse processo é o mesmo, pois ele está em qualquer outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-110">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="9bd9c-111">O processo de desenrolamento de pilha é uma pesquisa para um manipulador de exceção que coincide com a exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-111">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="9bd9c-112">A pesquisa inicia no atual `try...with` expressão, se houver um.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-112">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="9bd9c-113">Cada padrão no `with` bloco estiver marcado, em ordem.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-113">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="9bd9c-114">Quando um manipulador de exceção de correspondência for encontrado, a exceção será considerada tratada; Caso contrário, a pilha é organizada e `with` blocos a cadeia de chamada são verificados, até que um manipulador correspondente foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-114">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="9bd9c-115">Qualquer `finally` blocos que são encontrados na cadeia de chamada também são executados em sequência conforme a pilha esvazia.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-115">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="9bd9c-116">O `raise` função é o equivalente de `throw` em c# ou C++.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-116">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="9bd9c-117">Use `reraise` em um manipulador catch para propagar a mesma exceção a cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-117">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="9bd9c-118">Os exemplos de código a seguir ilustram o uso do `raise` função para gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-118">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="9bd9c-119">O `raise` função também pode ser usada para gerar exceções .NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-119">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="9bd9c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd9c-120">See Also</span></span>
[<span data-ttu-id="9bd9c-121">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="9bd9c-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="9bd9c-122">Tipos de Exceção</span><span class="sxs-lookup"><span data-stu-id="9bd9c-122">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="9bd9c-123">Exceções: a expressão `try...with`</span><span class="sxs-lookup"><span data-stu-id="9bd9c-123">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="9bd9c-124">Exceções: a expressão `try...finally`</span><span class="sxs-lookup"><span data-stu-id="9bd9c-124">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="9bd9c-125">Exceções: a função `failwith`</span><span class="sxs-lookup"><span data-stu-id="9bd9c-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="9bd9c-126">Exceções: a função `invalidArg`</span><span class="sxs-lookup"><span data-stu-id="9bd9c-126">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
