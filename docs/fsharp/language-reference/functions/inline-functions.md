---
title: Funções embutidas
description: Saiba como usar F# funções embutidas que são integradas diretamente ao código de chamada.
ms.date: 05/16/2016
ms.openlocfilehash: 12c175e3e46e12d978fe02d3e1fe83142e71a25d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966589"
---
# <a name="inline-functions"></a><span data-ttu-id="d9745-103">Funções embutidas</span><span class="sxs-lookup"><span data-stu-id="d9745-103">Inline Functions</span></span>

<span data-ttu-id="d9745-104">*Funções embutidas* são funções que são integradas diretamente ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="d9745-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="d9745-105">Usando funções embutidas</span><span class="sxs-lookup"><span data-stu-id="d9745-105">Using Inline Functions</span></span>

<span data-ttu-id="d9745-106">Quando você usa os parâmetros de tipo estático, todas as funções que são parametrizadas pelos parâmetros de tipo devem ser embutida.</span><span class="sxs-lookup"><span data-stu-id="d9745-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="d9745-107">Isso garante que o compilador pode resolver esses parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="d9745-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="d9745-108">Quando você usa os parâmetros de tipo genérico comum, não há nenhuma restrição.</span><span class="sxs-lookup"><span data-stu-id="d9745-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="d9745-109">Além de habilitar o uso de restrições de membro, funções embutidas podem ser útil para otimizar o código.</span><span class="sxs-lookup"><span data-stu-id="d9745-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="d9745-110">No entanto, uso excessivo de funções embutidas pode fazer com que seu código seja menos resistentes a alterações em otimizações do compilador e a implementação das funções de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d9745-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="d9745-111">Por esse motivo, você deve evitar o uso de funções embutidas para a otimização, a menos que você tenha tentado todas as outras técnicas de otimização.</span><span class="sxs-lookup"><span data-stu-id="d9745-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="d9745-112">Tornar um método ou função embutida, às vezes, pode melhorar desempenho, mas que não é sempre o caso.</span><span class="sxs-lookup"><span data-stu-id="d9745-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="d9745-113">Portanto, você também deve usar medidas de desempenho para verificar o que fazer qualquer determinada função embutida de fato, tem um efeito positivo.</span><span class="sxs-lookup"><span data-stu-id="d9745-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="d9745-114">O `inline` modificador pode ser aplicado a funções de nível superior, no nível de módulo ou no nível de método em uma classe.</span><span class="sxs-lookup"><span data-stu-id="d9745-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="d9745-115">O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutidos e um método estático em linha.</span><span class="sxs-lookup"><span data-stu-id="d9745-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="d9745-116">Funções embutidas e Inferência de tipo</span><span class="sxs-lookup"><span data-stu-id="d9745-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="d9745-117">A presença de `inline` afeta inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="d9745-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="d9745-118">Isso é porque as funções embutidas podem resolveram estaticamente os parâmetros de tipo, enquanto funções não embutidas não podem.</span><span class="sxs-lookup"><span data-stu-id="d9745-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="d9745-119">O exemplo de código a seguir mostra um caso em que `inline` é útil porque você está usando uma função que tem um parâmetro de tipo estaticamente resolvidos, o `float` operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="d9745-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="d9745-120">Sem o `inline` modificador, força a inferência de tipo para levar a um tipo específico, nesse caso, a função `int`.</span><span class="sxs-lookup"><span data-stu-id="d9745-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="d9745-121">Mas com o `inline` modificador, a função também é inferida para ter um parâmetro de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="d9745-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="d9745-122">Com o `inline` modificador, o tipo é inferido para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9745-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="d9745-123">Isso significa que a função aceita qualquer tipo que dá suporte a uma conversão **float**.</span><span class="sxs-lookup"><span data-stu-id="d9745-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9745-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9745-124">See also</span></span>

- [<span data-ttu-id="d9745-125">Funções</span><span class="sxs-lookup"><span data-stu-id="d9745-125">Functions</span></span>](index.md)
- [<span data-ttu-id="d9745-126">Restrições</span><span class="sxs-lookup"><span data-stu-id="d9745-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="d9745-127">Parâmetros de Tipo Resolvidos Estaticamente</span><span class="sxs-lookup"><span data-stu-id="d9745-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)