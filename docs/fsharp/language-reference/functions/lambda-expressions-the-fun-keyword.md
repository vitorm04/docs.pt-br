---
title: 'Expressões lambda: A palavra-chave Fun'
description: Saiba como usar a F# palavra-chave ' Fun ' para definir uma expressão lambda, que é uma função anônima.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630668"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="6ff9b-103">Expressões lambda: A palavra-chaveF#Fun ()</span><span class="sxs-lookup"><span data-stu-id="6ff9b-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="6ff9b-104">A `fun` palavra-chave é usada para definir uma expressão lambda, ou seja, uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ff9b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ff9b-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="6ff9b-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ff9b-106">Remarks</span></span>

<span data-ttu-id="6ff9b-107">A *lista de parâmetros* normalmente consiste em nomes e, opcionalmente, tipos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="6ff9b-108">Em geral, a *lista de parâmetros* pode ser composta de qualquer F# padrão.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="6ff9b-109">Para obter uma lista completa de padrões possíveis, consulte [correspondência de padrões](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="6ff9b-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="6ff9b-110">As listas de parâmetros válidos incluem os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="6ff9b-111">A *expressão* é o corpo da função, a última expressão que gera um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="6ff9b-112">Exemplos de expressões lambda válidas incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ff9b-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="6ff9b-113">Usando Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="6ff9b-113">Using Lambda Expressions</span></span>

<span data-ttu-id="6ff9b-114">As expressões lambda são especialmente úteis quando você deseja executar operações em uma lista ou em outra coleção e deseja evitar o trabalho extra de definir uma função.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="6ff9b-115">Muitas F# funções de biblioteca usam valores de função como argumentos e podem ser especialmente convenientes para usar uma expressão lambda nesses casos.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="6ff9b-116">O código a seguir aplica uma expressão lambda a elementos de uma lista.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="6ff9b-117">Nesse caso, a função anônima adiciona 1 a todos os elementos de uma lista.</span><span class="sxs-lookup"><span data-stu-id="6ff9b-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="6ff9b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ff9b-118">See also</span></span>

- [<span data-ttu-id="6ff9b-119">Funções</span><span class="sxs-lookup"><span data-stu-id="6ff9b-119">Functions</span></span>](index.md)
