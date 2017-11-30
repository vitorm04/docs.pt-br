---
title: "Exceções: a expressão try...finally (F#)"
description: "Saiba como o F # ' try... finally' que permite executar código de limpeza, mesmo se um bloco de código gera uma exceção."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="2f6c1-104">Exceções: a expressão try...finally</span><span class="sxs-lookup"><span data-stu-id="2f6c1-104">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="2f6c1-105">O `try...finally` expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-105">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="2f6c1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f6c1-106">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="2f6c1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f6c1-107">Remarks</span></span>
<span data-ttu-id="2f6c1-108">O `try...finally` expressão pode ser usada para executar o código em *expression2* na sintaxe anterior, independentemente se uma exceção é gerada durante a execução de *expression1*.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-108">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="2f6c1-109">O tipo de *expression2* não contribuem para o valor da expressão de inteiro; o tipo retornado quando não ocorrer uma exceção é o último valor *expression1*.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-109">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="2f6c1-110">Quando ocorre uma exceção, nenhum valor será retornado e o fluxo de controle transfere para o manipulador de exceção correspondente próximo a pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-110">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="2f6c1-111">Se nenhum manipulador de exceção é encontrada, o programa será encerrado.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-111">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="2f6c1-112">Antes do código em um manipulador de correspondência é executado ou o programa é encerrado, o código de `finally` ramificação é executada.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-112">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="2f6c1-113">O código a seguir demonstra o uso de `try...finally` expressão.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-113">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="2f6c1-114">A saída para o console é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-114">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="2f6c1-115">Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa foi tratada e o arquivo `test.txt` contém o texto `test1`, que indica que os buffers foram liberados e gravados no disco, embora a exceção transferidos controle ao manipulador de exceção externa.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-115">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="2f6c1-116">Observe que o `try...with` construção é uma construção separada do `try...finally` construir.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-116">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="2f6c1-117">Portanto, se seu código requer um `with` bloco e um `finally` bloco, você precisa aninhar as duas construções, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-117">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="2f6c1-118">No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos, **try... finally** expressões podem ter uma implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-118">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="2f6c1-119">Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2f6c1-119">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="2f6c1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f6c1-120">See Also</span></span>
[<span data-ttu-id="2f6c1-121">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="2f6c1-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="2f6c1-122">Exceções: a expressão `try...with`</span><span class="sxs-lookup"><span data-stu-id="2f6c1-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
