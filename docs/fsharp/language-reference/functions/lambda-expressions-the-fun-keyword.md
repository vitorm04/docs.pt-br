---
title: "Expressões lambda: a palavra-chave fun (F#)"
description: "Saiba como usar a palavra-chave F # 'fun' para definir uma expressão lambda, que é uma função anônima."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="88aad-104">Expressões lambda: a palavra-chave fun (F#)</span><span class="sxs-lookup"><span data-stu-id="88aad-104">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="88aad-105">O `fun` palavra-chave é usada para definir uma expressão lambda, ou seja, uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="88aad-105">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="88aad-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88aad-106">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="88aad-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="88aad-107">Remarks</span></span>
<span data-ttu-id="88aad-108">O *a lista de parâmetros* normalmente é constituído de nomes e, opcionalmente, tipos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="88aad-108">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="88aad-109">Geralmente, o *a lista de parâmetros* pode ser composto de quaisquer padrões F #.</span><span class="sxs-lookup"><span data-stu-id="88aad-109">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="88aad-110">Para obter uma lista completa dos padrões possíveis, consulte [correspondência de padrões](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="88aad-110">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="88aad-111">Listas de parâmetros válidos incluem os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="88aad-111">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="88aad-112">O *expressão* é o corpo da função, a última expressão que gera um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="88aad-112">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="88aad-113">Exemplos de expressões lambda válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="88aad-113">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="88aad-114">Usando Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="88aad-114">Using Lambda Expressions</span></span>
<span data-ttu-id="88aad-115">Expressões lambda são especialmente úteis quando você deseja executar operações em uma lista ou outra coleção e para evitar o trabalho extra de definição de uma função.</span><span class="sxs-lookup"><span data-stu-id="88aad-115">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="88aad-116">Muitas funções de biblioteca F # levam valores como argumentos de função e é especialmente conveniente ao usar uma expressão lambda nesses casos.</span><span class="sxs-lookup"><span data-stu-id="88aad-116">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="88aad-117">O código a seguir se aplica a uma expressão lambda para elementos de uma lista.</span><span class="sxs-lookup"><span data-stu-id="88aad-117">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="88aad-118">Nesse caso, a função anônima adiciona 1 a cada elemento de uma lista.</span><span class="sxs-lookup"><span data-stu-id="88aad-118">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="88aad-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88aad-119">See Also</span></span>
[<span data-ttu-id="88aad-120">Funções</span><span class="sxs-lookup"><span data-stu-id="88aad-120">Functions</span></span>](index.md)
