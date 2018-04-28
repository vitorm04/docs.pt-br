---
title: Funções embutidas (F#)
description: 'Saiba como usar o F # embutido funções que são integradas diretamente no código de chamada.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cb0addd1456af1ab97e249b9c5ece4d9f0818fa3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="inline-functions"></a><span data-ttu-id="bf3f4-103">Funções embutidas</span><span class="sxs-lookup"><span data-stu-id="bf3f4-103">Inline Functions</span></span>

<span data-ttu-id="bf3f4-104">*Funções embutidas* são funções que são integradas diretamente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="bf3f4-105">Usando funções embutidas</span><span class="sxs-lookup"><span data-stu-id="bf3f4-105">Using Inline Functions</span></span>
<span data-ttu-id="bf3f4-106">Quando você usar parâmetros de tipo estático, todas as funções que são parametrizadas por parâmetros de tipo devem ser embutida.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="bf3f4-107">Isso garante que o compilador pode resolver esses parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="bf3f4-108">Quando você usar parâmetros de tipo genérico comum, não há nenhuma restrição.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="bf3f4-109">Além de habilitar o uso de restrições de membro, funções embutidas podem ser úteis na otimização de código.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="bf3f4-110">No entanto, o uso excessivo de funções embutidas pode causar seu código seja menos resistentes a mudanças em otimizações do compilador e a implementação de funções de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="bf3f4-111">Por esse motivo, você deve evitar usar funções embutidas para otimização, a menos que você tentou todas as outras técnicas de otimização.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="bf3f4-112">Fazer um método ou função em linha pode muitas vezes melhorar desempenho, mas que não é sempre o caso.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="bf3f4-113">Portanto, você também deve usar medidas de desempenho para verificar o que fazer qualquer determinada função embutida na verdade tem um efeito positivo.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="bf3f4-114">O `inline` modificador pode ser aplicado às funções de nível superior, no nível de módulo ou no nível de método em uma classe.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="bf3f4-115">O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutido e um método estático em linha.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="bf3f4-116">Funções embutidas e Inferência de tipo</span><span class="sxs-lookup"><span data-stu-id="bf3f4-116">Inline Functions and Type Inference</span></span>
<span data-ttu-id="bf3f4-117">A presença de `inline` afeta a inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="bf3f4-118">Isso ocorre porque funções embutidas podem ter resolvidos estaticamente parâmetros de tipo, enquanto as funções embutidas não não é possível.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="bf3f4-119">O exemplo de código a seguir mostra um caso onde `inline` é útil porque você está usando uma função que tem um parâmetro de tipo resolvidos estaticamente, o `float` operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="bf3f4-120">Sem o `inline` força de inferência de tipo de modificador, a função para usar um tipo específico, nesse caso `int`.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="bf3f4-121">Mas com o `inline` modificador, a função também é inferido para ter um parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="bf3f4-122">Com o `inline` modificador, o tipo é inferido para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="bf3f4-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="bf3f4-123">Isso significa que a função aceita qualquer tipo que oferece suporte a uma conversão **float**.</span><span class="sxs-lookup"><span data-stu-id="bf3f4-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="bf3f4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf3f4-124">See Also</span></span>
[<span data-ttu-id="bf3f4-125">Funções</span><span class="sxs-lookup"><span data-stu-id="bf3f4-125">Functions</span></span>](index.md)

[<span data-ttu-id="bf3f4-126">Restrições</span><span class="sxs-lookup"><span data-stu-id="bf3f4-126">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="bf3f4-127">Parâmetros de Tipo Resolvidos Estaticamente</span><span class="sxs-lookup"><span data-stu-id="bf3f4-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
