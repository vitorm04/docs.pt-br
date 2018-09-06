---
title: 'Exceções: a expressão try...finally (F#)'
description: "Saiba como o F # ' try... finally' expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção."
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803337"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="985ea-103">Exceções: a expressão try...finally</span><span class="sxs-lookup"><span data-stu-id="985ea-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="985ea-104">O `try...finally` expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="985ea-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="985ea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="985ea-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="985ea-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="985ea-106">Remarks</span></span>

<span data-ttu-id="985ea-107">O `try...finally` expressão pode ser usada para executar o código na *expression2* na sintaxe anterior, independentemente de se uma exceção é gerada durante a execução da *expression1*.</span><span class="sxs-lookup"><span data-stu-id="985ea-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="985ea-108">O tipo de *expression2* não contribui para o valor da expressão inteira; o tipo retornado quando ocorre uma exceção é o último valor no *expression1*.</span><span class="sxs-lookup"><span data-stu-id="985ea-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="985ea-109">Quando ocorre uma exceção, nenhum valor é retornado e o fluxo de controle transfere para o próximo manipulador de exceções correspondente a pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="985ea-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="985ea-110">Se nenhum manipulador de exceção é encontrada, o programa é encerrado.</span><span class="sxs-lookup"><span data-stu-id="985ea-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="985ea-111">Antes do código em um manipulador correspondente é executado ou o programa é encerrado, o código a `finally` ramificação é executado.</span><span class="sxs-lookup"><span data-stu-id="985ea-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="985ea-112">O código a seguir demonstra o uso do `try...finally` expressão.</span><span class="sxs-lookup"><span data-stu-id="985ea-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="985ea-113">A saída para o console é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="985ea-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="985ea-114">Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa foi tratada e o arquivo `test.txt` contém o texto `test1`, que indica que os buffers foram liberados e gravados no disco, mesmo que a exceção transferidos o controle para o manipulador de exceção externa.</span><span class="sxs-lookup"><span data-stu-id="985ea-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="985ea-115">Observe que o `try...with` constructo é uma construção separada do `try...finally` construir.</span><span class="sxs-lookup"><span data-stu-id="985ea-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="985ea-116">Portanto, se seu código exigir ambos um `with` bloco e um `finally` bloco, é necessário aninhar as duas construções, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="985ea-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="985ea-117">No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos **try... finally** expressões podem ter uma implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="985ea-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="985ea-118">Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="985ea-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="985ea-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="985ea-119">See also</span></span>

- [<span data-ttu-id="985ea-120">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="985ea-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="985ea-121">Exceções: a expressão `try...with`</span><span class="sxs-lookup"><span data-stu-id="985ea-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
