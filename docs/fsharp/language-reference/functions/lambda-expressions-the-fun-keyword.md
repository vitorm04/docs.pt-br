---
title: 'Expressões lambda: a palavra-chave fun (F#)'
description: "Saiba como usar a palavra-chave F # 'fun' para definir uma expressão lambda, que é uma função anônima."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f2f15a1b482ce3971d0b3d5ffc4f6dcc9ccf1569
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="77167-103">Expressões lambda: a palavra-chave fun (F#)</span><span class="sxs-lookup"><span data-stu-id="77167-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="77167-104">O `fun` palavra-chave é usada para definir uma expressão lambda, ou seja, uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="77167-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="77167-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77167-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="77167-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="77167-106">Remarks</span></span>
<span data-ttu-id="77167-107">O *a lista de parâmetros* normalmente é constituído de nomes e, opcionalmente, tipos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="77167-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="77167-108">Geralmente, o *a lista de parâmetros* pode ser composto de quaisquer padrões F #.</span><span class="sxs-lookup"><span data-stu-id="77167-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="77167-109">Para obter uma lista completa dos padrões possíveis, consulte [correspondência de padrões](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="77167-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="77167-110">Listas de parâmetros válidos incluem os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="77167-110">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="77167-111">O *expressão* é o corpo da função, a última expressão que gera um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="77167-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="77167-112">Exemplos de expressões lambda válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="77167-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="77167-113">Usando Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="77167-113">Using Lambda Expressions</span></span>
<span data-ttu-id="77167-114">Expressões lambda são especialmente úteis quando você deseja executar operações em uma lista ou outra coleção e para evitar o trabalho extra de definição de uma função.</span><span class="sxs-lookup"><span data-stu-id="77167-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="77167-115">Muitas funções de biblioteca F # levam valores como argumentos de função e é especialmente conveniente ao usar uma expressão lambda nesses casos.</span><span class="sxs-lookup"><span data-stu-id="77167-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="77167-116">O código a seguir se aplica a uma expressão lambda para elementos de uma lista.</span><span class="sxs-lookup"><span data-stu-id="77167-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="77167-117">Nesse caso, a função anônima adiciona 1 a cada elemento de uma lista.</span><span class="sxs-lookup"><span data-stu-id="77167-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="77167-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77167-118">See Also</span></span>
[<span data-ttu-id="77167-119">Funções</span><span class="sxs-lookup"><span data-stu-id="77167-119">Functions</span></span>](index.md)
