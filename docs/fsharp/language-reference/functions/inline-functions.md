---
title: Funções embutidas
description: Saiba como usar F# funções embutidas que são integradas diretamente no código de chamada.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630683"
---
# <a name="inline-functions"></a><span data-ttu-id="c2ea3-103">Funções embutidas</span><span class="sxs-lookup"><span data-stu-id="c2ea3-103">Inline Functions</span></span>

<span data-ttu-id="c2ea3-104">*Funções embutidas* são funções integradas diretamente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="c2ea3-105">Usando funções embutidas</span><span class="sxs-lookup"><span data-stu-id="c2ea3-105">Using Inline Functions</span></span>

<span data-ttu-id="c2ea3-106">Quando você usa parâmetros de tipo estático, todas as funções parametrizadas por parâmetros de tipo devem ser embutidas.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="c2ea3-107">Isso garante que o compilador possa resolver esses parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="c2ea3-108">Quando você usa parâmetros de tipo genérico comuns, não há essa restrição.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="c2ea3-109">Além de habilitar o uso de restrições de membro, as funções embutidas podem ser úteis para otimizar o código.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="c2ea3-110">No entanto, o uso excessivo de funções embutidas pode fazer com que seu código seja menos resistente a alterações em otimizações de compilador e a implementação de funções de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="c2ea3-111">Por esse motivo, evite usar funções embutidas para otimização, a menos que você tenha tentado todas as outras técnicas de otimização.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="c2ea3-112">Tornar uma função ou método embutido pode, às vezes, melhorar o desempenho, mas esse nem sempre é o caso.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="c2ea3-113">Portanto, você também deve usar medidas de desempenho para verificar se a criação de qualquer função embutida na verdade tem um efeito positivo.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="c2ea3-114">O `inline` modificador pode ser aplicado a funções no nível superior, no nível do módulo ou no nível do método em uma classe.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="c2ea3-115">O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutida e um método estático embutido.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="c2ea3-116">Funções embutidas e inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="c2ea3-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="c2ea3-117">A presença de `inline` afeta a inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="c2ea3-118">Isso ocorre porque as funções embutidas podem ter parâmetros de tipo estaticamente resolvidos, enquanto funções não embutidas não podem.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="c2ea3-119">O exemplo de código a seguir mostra um `inline` caso em que é útil porque você está usando uma função que tem um parâmetro de tipo resolvido `float` estaticamente, o operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="c2ea3-120">Sem o `inline` modificador, a inferência de tipos força a função a usar um tipo específico `int`, nesse caso.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="c2ea3-121">Mas com o `inline` modificador, a função também é inferida para ter um parâmetro de tipo estaticamente resolvido.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="c2ea3-122">Com o `inline` modificador, o tipo é inferido para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2ea3-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="c2ea3-123">Isso significa que a função aceita qualquer tipo que ofereça suporte a uma conversão para **float**.</span><span class="sxs-lookup"><span data-stu-id="c2ea3-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2ea3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2ea3-124">See also</span></span>

- [<span data-ttu-id="c2ea3-125">Funções</span><span class="sxs-lookup"><span data-stu-id="c2ea3-125">Functions</span></span>](index.md)
- [<span data-ttu-id="c2ea3-126">Restrições</span><span class="sxs-lookup"><span data-stu-id="c2ea3-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="c2ea3-127">Parâmetros de Tipo Resolvidos Estaticamente</span><span class="sxs-lookup"><span data-stu-id="c2ea3-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
