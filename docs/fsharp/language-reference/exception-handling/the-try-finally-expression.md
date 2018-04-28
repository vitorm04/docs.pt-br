---
title: 'Exceções: a expressão try...finally (F#)'
description: "Saiba como o F # ' try... finally' que permite executar código de limpeza, mesmo se um bloco de código gera uma exceção."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 588e4edb4d25c6d25ef103ba724613db997f68d7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="6e748-103">Exceções: a expressão try...finally</span><span class="sxs-lookup"><span data-stu-id="6e748-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="6e748-104">O `try...finally` expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6e748-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="6e748-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e748-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="6e748-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e748-106">Remarks</span></span>
<span data-ttu-id="6e748-107">O `try...finally` expressão pode ser usada para executar o código em *expression2* na sintaxe anterior, independentemente se uma exceção é gerada durante a execução de *expression1*.</span><span class="sxs-lookup"><span data-stu-id="6e748-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="6e748-108">O tipo de *expression2* não contribuem para o valor da expressão de inteiro; o tipo retornado quando não ocorrer uma exceção é o último valor *expression1*.</span><span class="sxs-lookup"><span data-stu-id="6e748-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="6e748-109">Quando ocorre uma exceção, nenhum valor será retornado e o fluxo de controle transfere para o manipulador de exceção correspondente próximo a pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="6e748-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="6e748-110">Se nenhum manipulador de exceção é encontrada, o programa será encerrado.</span><span class="sxs-lookup"><span data-stu-id="6e748-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="6e748-111">Antes do código em um manipulador de correspondência é executado ou o programa é encerrado, o código de `finally` ramificação é executada.</span><span class="sxs-lookup"><span data-stu-id="6e748-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="6e748-112">O código a seguir demonstra o uso de `try...finally` expressão.</span><span class="sxs-lookup"><span data-stu-id="6e748-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="6e748-113">A saída para o console é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="6e748-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="6e748-114">Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa foi tratada e o arquivo `test.txt` contém o texto `test1`, que indica que os buffers foram liberados e gravados no disco, embora a exceção transferidos controle ao manipulador de exceção externa.</span><span class="sxs-lookup"><span data-stu-id="6e748-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="6e748-115">Observe que o `try...with` construção é uma construção separada do `try...finally` construir.</span><span class="sxs-lookup"><span data-stu-id="6e748-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="6e748-116">Portanto, se seu código requer um `with` bloco e um `finally` bloco, você precisa aninhar as duas construções, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e748-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="6e748-117">No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos, **try... finally** expressões podem ter uma implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6e748-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="6e748-118">Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6e748-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="6e748-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e748-119">See Also</span></span>
[<span data-ttu-id="6e748-120">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="6e748-120">Exception Handling</span></span>](index.md)

[<span data-ttu-id="6e748-121">Exceções: a expressão `try...with`</span><span class="sxs-lookup"><span data-stu-id="6e748-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
