---
title: 'Exceções: A expressão try...finally'
description: Saiba como o F# ' Try... Finally ' permite que você execute código de limpeza mesmo que um bloco de código gere uma exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083003"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="c9629-103">Exceções: A expressão try...finally</span><span class="sxs-lookup"><span data-stu-id="c9629-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="c9629-104">A `try...finally` expressão permite que você execute o código de limpeza mesmo que um bloco de código gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c9629-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9629-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9629-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="c9629-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9629-106">Remarks</span></span>

<span data-ttu-id="c9629-107">A `try...finally` expressão pode ser usada para executar o código em *expression2* na sintaxe anterior, independentemente de uma exceção ser gerada durante a execução de *expressão1*.</span><span class="sxs-lookup"><span data-stu-id="c9629-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="c9629-108">O tipo de *expression2* não contribui para o valor da expressão inteira; o tipo retornado quando uma exceção não ocorre é o último valor em *expression1*.</span><span class="sxs-lookup"><span data-stu-id="c9629-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="c9629-109">Quando ocorre uma exceção, nenhum valor é retornado e o fluxo de controle é transferido para o próximo manipulador de exceção correspondente na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="c9629-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="c9629-110">Se nenhum manipulador de exceção for encontrado, o programa será encerrado.</span><span class="sxs-lookup"><span data-stu-id="c9629-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="c9629-111">Antes que o código em um manipulador correspondente seja executado ou o programa seja encerrado, o código `finally` na ramificação será executado.</span><span class="sxs-lookup"><span data-stu-id="c9629-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="c9629-112">O código a seguir demonstra o uso da `try...finally` expressão.</span><span class="sxs-lookup"><span data-stu-id="c9629-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="c9629-113">A saída para o console é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c9629-113">The output to the console is as follows.</span></span>

```console
Closing stream
Exception handled.
```

<span data-ttu-id="c9629-114">Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa fosse tratada e o arquivo `test.txt` contém o texto `test1`, o que indica que os buffers foram liberados e gravados no disco, mesmo que a exceção seja transferida controle para o manipulador de exceção externa.</span><span class="sxs-lookup"><span data-stu-id="c9629-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="c9629-115">Observe que a `try...with` construção é uma construção separada `try...finally` da construção.</span><span class="sxs-lookup"><span data-stu-id="c9629-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="c9629-116">Portanto, se o seu código exigir um `with` bloco e um `finally` bloco, você precisará aninhar as duas construções, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9629-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="c9629-117">No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos, **tente...** as expressões finally podem ter uma implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c9629-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="c9629-118">Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c9629-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9629-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9629-119">See also</span></span>

- [<span data-ttu-id="c9629-120">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="c9629-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="c9629-121">Exceções: A `try...with` expressão</span><span class="sxs-lookup"><span data-stu-id="c9629-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
